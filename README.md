# proto-gen-go

This tool is a thin wrapper around protoc, the protocol compiler. It
makes it easy to reliably generate and update Go definitions for
messages and services defined in .proto files. It uses a docker
container with explicitly versioned dependencies to ensure maximum
reproducibility and minimum side effects.

In your Go project's proto directory, add a `gen.go` file with the following contents:

```go
package proto
//go:generate sh -c "go run github.com/github/proto-gen-go@latest [protoc flags] [proto files]"
```

Now, when you run `go generate` in your proto directory, the script
will re-run the protocol compiler on all .proto files, and generate go
files into the obvious relative locations. Commit them along with your
source code.
