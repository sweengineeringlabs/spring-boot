# Grine bootstrap build

This repository remains a Gradle-first Spring Boot build. The root `grine.toml`
provides a native Grine build for foundational pure-Java modules that do not
depend on Gradle plugin execution or generated Gradle metadata.

## Prerequisites

- JDK 21 or newer (Grine's current compiler floor)
- The Grine CLI uber-JAR built at `../grine4j/cli/target/cli-*-all.jar`

## Build

From the repository root:

```powershell
java -jar ..\grine4j\cli\target\cli-0.1.0-SNAPSHOT-all.jar build
```

```bash
java -jar ../grine4j/cli/target/cli-0.1.0-SNAPSHOT-all.jar build
```

Compiled output is written beneath `target/grine`.

## Current scope

- `spring-boot-autoconfigure-processor`

The complete Spring Boot distribution still requires Gradle. It uses custom
Gradle plugins, Kotlin and Groovy compilation, generated sources, test fixtures,
dependency platforms, and specialized packaging tasks that Grine does not yet
model. Add further pure-Java modules incrementally as those capabilities land.

In particular, workspace-member feature source sets are not currently loaded by
Grine, so modules that combine `src/main/java` with additional source trees such
as `src/json-shade/java` are intentionally excluded.
