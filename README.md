# Super Evil Golang Linter
A super evil linter for Golang.

## Requirements

- Linux or MacOS
- [Golang][golang]

## Installation

Install using one of the following locations:

- https://git.superevilmegaco.com/golang/superevil-golint
- https://github.com/stroeerdigitalpublishing/superevil-golint
- https://github.com/superevilmegaco/superevil-golint

```bash
# Using the superevilmegaco.com Git mirror
go get git.superevilmegaco.com/golang/superevil-golint

# Using the repository from stroeerdigitalpublishing on Github
go get github.com/stroeerdigitalpublishing/superevil-golint

# Using the repository from superevilmegaco on Github
go get github.com/superevilmegaco/superevil-golint
```

### Custom mirrors

You can always mirror one of the locations found above and use your own
location then.

Just fork this repository and you're good to go.

## Usage

Switch to the root of your project directory and run the following command

```bash
go lint
```

## Passing checks

To pass the *linting* rules, your code has to pass the following checks:

- [gofmt][gofmt]
- [golint][golint]
- have at least 90% code coverage

### Passing `gofmt` check

You have to pass the `gofmt` default rules, so we all have a consistent
code-style. This helps to minimize the possiblity of merge conflicts and helps
to ease in code-reviews.

You should really consider running `gofmt` each time you save your files.
There are excellent plugins that helps to ease the pain,
like the wonderful [vim-go][vim-go-github] plugin for *Vim* and *NeoVim*.

### Passing `golint` check

You don't have to do anything specific to pass the `golint` testing stage,
because I can't enforce them; even the official repo states:

> The suggestions made by golint are exactly that: suggestions.
> Golint is not perfect, and has both false positives and false negatives.
> Do not treat its output as a gold standard.
> We will not be adding pragmas or other knobs to suppress specific warnings,
> so do not expect or require code to be completely "lint-free".
> In short, this tool is not, and will never be,
> trustworthy enough for its suggestions to be enforced automatically,
> for example as part of a build process.
>
> Golint makes suggestions for many of the mechanically checkable
> items listed in Effective Go and the CodeReviewComments wiki page.

Following to the best extend is in the hands of the developers,
but if we happen to work on a project and you're simply ignoring all this,
I will come to your desk and start yelling at you. I swear!

This should also help to minimize the possiblity of merge conflicts and also
help to ease-in code-reviews.

## Example Unit-Tests

### Example Goblin Unit-Test

```go
package superevilpack

import (
    "testing"
    . "github.com/franela/goblin"
)

func Test(t *testing.T) {
    g := Goblin(t)
    g.Describe("Numbers", func() {
        // Passing Test
        g.It("Should add two numbers ", func() {
            g.Assert(1+1).Equal(2)
        })
        // Failing Test
        g.It("Should match equal numbers", func() {
            g.Assert(2).Equal(4)
        })
        // Pending Test
        g.It("Should substract two numbers")
        // Excluded Test
        g.XIt("Should add two numbers ", func() {
            g.Assert(3+1).Equal(4)
        })
    })
}
```

## Dependencies

These dependencies are automatically resolved when you install the
*Super Evil Golang Linter*.

- [gofmt][gofmt]
- [gomega][gomega]
- [goblin][goblin]
- [golint][golint]



[gofmt]: https://golang.org/cmd/gofmt/
[gomega]: https://github.com/onsi/gomega
[goblin]: https://github.com/franela/goblin
[golint]: https://godoc.org/golang.org/x/lint/golint
[golang]: https://golang.org/
[vim-go-github]: https://github.com/fatih/vim-go

