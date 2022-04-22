---
title: Easy Publisher
---

Ever wondered how to create a simple publisher?

 

Quick Start
-----------

Firstly we need to import the required frameworks

```swift
// Used for the ObservableObject
import Combine

// The easiest for publishers
import SwiftUI
```

 

### Published object

We're going to create a `ObservableObject`, which contains a `@Published` variable.

```swift
class MyObject: ObservableObject {
    @Published var y: String
    init() {
        y = "Loading..."
        DispatchQueue.main.asyncAfter(deadline: .now() + 5) { 
            self.upd()
        }
    }
    func upd() {
        y = "Published World"
        self.objectWillChange
    }
}
```

### Generate static files

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ bash
$ hexo generate
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

More info: [Generating](https://hexo.io/docs/generating.html)

 

### Full code

```swift
import Combine
import SwiftUI

class MyObject: ObservableObject {
    @Published var y: String
    init() {
        y = "Loading..."
        DispatchQueue.main.asyncAfter(deadline: .now() + 5) { 
            self.upd()
        }
    }
    func upd() {
        y = "Published World"
        self.objectWillChange
    }
}

struct MyView: View {
    @ObservedObject var v = MyObject()
    var body: some View {
        Text(v.y)
    }
}
```

 
