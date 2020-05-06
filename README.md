# Morphir

Morphir is a multi-language system built on a data format that captures an application's domain model and business logic in a technology agnostic manner. Having all the business knowledge available as data allows you to process it programatically in various ways:

- **Translate it** to move between languages and platforms effortlessly as technology evolves
- **Visualize it** to turn black-box logic into insightful explanations for your business users
- **Share it** across different departments or organizations for consistent interpretation
- **Store it** to retrieve and explain earlier versions of the logic in seconds
- and much more ...

While the core idea behind Morphir is very simple it's still challenging to describe it because it doesn't fit into any well-known categories. To help you understand what it is and how you can use it to solve real-world problems we came up with a list of questions and short answers:

- [How do I define my domain model and business logic?](#how-do-I-define-my-domain-model-and-business-logic)
- [How does Morphir turn logic into data?](#how-does-morphir-turn-logic-into-data)
- [What does the data format look like?](#what-does-the-data-format-look-like)


## How do I define my domain model and business logic?

Morphir is a multi-language system so it gives you flexibility in what language or tool you use to define your domain model and business logic (we refer to them as frontends). As a community we are continuously building new language frontends and if the one you are looking for is not available we provide tools for you to build it yourself.

Our main frontend is currently the [Elm](https://elm-lang.org/) programming language. We support the whole language (except for some very platform specific features like ports) so defining your domain model and business logic boils down to writing Elm code. To learn more about the fronted see [morphir-elm](https://github.com/Morgan-Stanley/morphir-elm).

Other frontends:

- [Bosque Programming Language](https://github.com/Morgan-Stanley/morphir-bosque)

## How does Morphir turn logic into data?

The process of turning logic into data is well known because every programming language compiler and interpreter does it. They parse the source code to generate an [abstract syntax tree](https://en.wikipedia.org/wiki/Abstract_syntax_tree) which is then transformed into an [intermediate representation](https://en.wikipedia.org/wiki/Intermediate_representation) of some sort.

Morphir simply turns that intermediate representation into a developer-friendly data format that makes it easy to build automation on top of it.

## What does the data format look like?

It's easiest to start with an example. Say you have some simple business logic like this:

```javascript
quantity * unitPrice
```

In Morphir's data format this would translate into something like this:

```javascript
["Apply"
, ["Apply"
  , ["Reference", [["Morphir", "SDK"], ["Number"], "multiply"]]
  , ["Variable", ["quantity"]]]
, ["Variable", ["unit", "price"]]
]
```
