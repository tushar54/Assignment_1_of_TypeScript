
## Differences Between Interfaces and Types in TypeScript ?

## In TypeScript, both interfaces and types are used to define custom shapes for data, but they have subtle differences that influence when and how you should use them.

## Interfaces are primarily designed for defining object structures, making them a natural fit for object-oriented programming. They support declaration merging, meaning you can define an interface in multiple places, and TypeScript will automatically combine them. This is useful for extending third-party types or gradually adding properties. Interfaces also work seamlessly with extends for inheritance, making them ideal for class implementations.

## Types, on the other hand, are more flexible. They can represent not just objects but also primitives, unions ("active" | "inactive"), tuples, and even complex mapped types. However, types cannot be merged or extended after creation—though you can use intersections (&) to combine them. They’re the go-to choice for advanced type manipulations, like conditional types or utility types (Partial<T>, Pick<T, K>).

 ## When to Use Which?

Use interfaces for defining public APIs, class shapes, or when you need merging/extending.

Use types for ad-hoc type aliases, unions, or complex type logic.

For example, if you’re defining a User object that might evolve, an interface is cleaner. But if you need a type like Status = "pending" | "completed", a type is the right tool. Both are interchangeable for simple objects, but their differences become powerful in larger projects.



## What is the use of the keyof keyword in TypeScript?Provide an example :

keyof keyword usually used for when we need to extracts the keys of an object type as a union of string literals.
Key Use Cases of keyof:
-Type-safe property access (prevents invalid keys at compile time).
-Mapped Types 
-Dynamic object manipulation
 
 ## Example:

 interface User {
  id: number;
  name: string;
  email: string;
}

type UserKeys = keyof User; // "id" | "name" | "email"

function getProperty<T, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user: User = { id: 1, name: "Alice", email: "alice@example.com" };
console.log(getProperty(user, "name")); // Output: "Alice"
