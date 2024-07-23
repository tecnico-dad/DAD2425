# DAD2425
Project course for DAD 2024-25

This repository holds the base code required to implement the project. Students are free to improve on the following code.

# Requirements

The project requires the following packages:

- Java 22
- Maven 3.8.4
- Protoc 3.12

# Compiling

To compile the project, students must run the command
`mvn clean install` in the root directory

## **WARNING - Compilation Environment**

The project requires different `pom.xml` for the *contract* module depending on the CPU architecture/OS distribution. 
The project currently has two pre-pepared poms:
- One for **ARM/M4 Mac-OS** based systems, named `arm-pom.xml`;
- One for **Intel/Linux** based systems, named `intel-pom.xml`;

Before the first compilation, copy your required contract pom and rename it to `pom.xml`.

# Deployment

Current implementation assumes that all modules run on the same physical machine and requires 5 active servers. 

The project is composed of three main components:
- Servers
- Clients
- ConsoleClient


## Servers

The servers run the base implementation. They are executed running the following command in the *server* directory:

`mvn exec:java -Dexec.args="{port} {id}"`

Where you must fill in the following arguments:
- **{id}**: Sequential id of the server. Current implementation requires servers to be ID'ed starting from *0* to *N-1* servers.
- **{port}**: Base port of all servers. **All servers should use the same port**. The Server binded port will be  **{port} + {id}**. 

## Client

A client that executes transactions. It is executed by running the following command in the *client* directory:

`mvn exec:java`

The client module opens a terminal from where students may issue commands. The following commands are available:
- `help` - Shows the full command list;
- `read` - ...;
- `tx {read_key_1} {read_key_2} {write_key}` - Takes as input 3 keys and executes a transaction with 2 reads and 1 write respectively;
- `loop` - ...
- `lenght {loop-lenght}` - ...
- `time {sleep-range}` - ...
- `exit` - Gracefully finishes the client

## ConsoleClient

The console client servers as a front-end to issue configuration settings to servers. It is executed by running the following command in the *consoleclient* directory:

`mvn exec:java`

The console client opens a terminal from where students may issue configuration changes to servers. The following commands are available:
- ... ;

## Protobuffs and Utils

To support these modules, the project has two additional directories:
- *contract*, holding the required `.proto` files;
- *util*, holding the general classes to collect RPC responses
