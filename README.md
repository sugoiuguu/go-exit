# Who is this for?

For our naive gophers who call `log.Fatal(err)` or `os.Exit(1)` after
doing some shit like `defer f.Close()`.

# Usage

Buckle up boys and galz...

```go
package main

import (
    "os"
    "fmt"
    "exit"
)

type ExitStatus int

func (s ExitStatus) ExitCode() int {
    fmt.Fprintln(os.Stderr, "OMG IT ALL WENT DOWN THE SHITTER")
    return int(s)
}

func main() {
    defer exit.Handler()
    defer fmt.Println("it worked I guess")
    exit.WithStatus(ExitStatus(2))
}
```
