This is a simple TOTP _(Time-based One-time Password)_ CLI tool.
TOTP is the most common mechanism for 2FA _(Two-Factor-Authentication)_.
You can manage and organize your accounts with namespaces
and protect your data with a password.

### Install

```
$ go get https://github.com/Yitsushi/go-commander
```

### Sample output _(from [totp-cli](https://github.com/Yistsuhi/totp-cli))_

```
$ totp-cli help

add-token [namespace] [account]   Add new token
list [namespace]                  List all available namespaces or accounts under a namespace
delete <namespace>[.account]      Delete an account or a whole namespace
change-password                   Change password
update                            Check and update totp-cli itself
version                           Print current version of this application
generate <namespace>.<account>    Generate a specific OTP
```

### Usage

Every single command has to implement `CommandInterface`.
Check [this project](https://github.com/Yitsushi/totp-cli) for examples.

```
package main

// Import the package
import "github.com/Yitsuhsi/go-commander"

// Yout Command
type YourCommand struct {
}

func (c *YourCommand) Execute() {
  // Command Action
}

func (c *YourCommand) ArgumentDescription() string {
  return ""
}

func (c *YourCommand) Description() string {
  return ""
}

func (c *YourCommand) Help() string {
  return ""
}

func (c *YourCommand) Examples() []string {
  return []string{}
}

// Main Section
func main() {
	registry := commander.NewCommandRegistry()

	registry.Register("your-command", &YourCommand{})

	registry.Execute()
}
```

Now you have a CLI tool with two commands: `help` and `your-command`.