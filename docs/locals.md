---
layout: default
title: All About Locals
nav_order: 2
---

1. TOC
{:toc}

---

## Manipulating Locals

### Remove duplicates

1. Use the `list uniq` macro list functionality

    ```
    local vars state county county
    loc nodups : list uniq vars
    ```

    ```
    display `nodups'
    . state county
    ```

### Add/Remove Elements

Removing elements of a local is easy.

1. Create a local (`minus`) with the elements you want to remove

    ```
    local vars a b c
    local minus a
    ```

    ```
    display `vars'
    . a b c
    ```

2. Use the macro list functionality: `list` with a minus

    ```
    local vars : list vars - minus
    ```

    ```
    display `vars'
    . b c
    ```

### Union and intersection

Another useful tool is taking the common and different elements between two locals

```
local x state county
local y county tract
```

1. For unions use `|` (like in x "or" y)
    ```
    local union : list x | y
    ```

    ```
    display `union'
    .  state county tract
    ```
2. For intersections use `&` (like in x "and" y)
    ```
    local intersection : list x & y
    ```

    ```
    display `intersection'
    .  county
    ```

### Sorting

Sometimes we want to sort elements of a local

1. Use `sort` macro list functionality

    ```
    local unordered b c a
    local ordered : list sort unordered
    ```

    ```
    display `ordered'
    . a b c
    ```
