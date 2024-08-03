# Simple JSON Database Driver in Go

This repository contains a simple JSON-based database driver implementation in Go. The driver supports basic CRUD (Create, Read, Update, Delete) operations using JSON files to store data. 

## Overview

The driver provides functionalities to:

- **Write**: Save records in JSON format.
- **Read**: Retrieve records from JSON files.
- **ReadAll**: Retrieve all records from a specific collection.
- **Delete**: Remove records or collections.

It also includes basic logging using the `lumber` package.

## Code Structure

### `Driver`

The `Driver` struct manages the JSON database and provides methods for interacting with it. It includes:

- **Fields**:
  - `mutex`: A global mutex for synchronizing access to the driver.
  - `mutexes`: A map of mutexes for each collection.
  - `dir`: Directory where the database is stored.
  - `log`: Logger for logging messages.

- **Methods**:
  - `New(dir string, options *Options) (*Driver, error)`: Initializes a new database driver.
  - `Write(collection, resource string, v interface{}) error`: Writes a record to a collection.
  - `Read(collection, resource string, v interface{}) error`: Reads a record from a collection.
  - `ReadAll(collection string) ([]string, error)`: Reads all records from a collection.
  - `Delete(collection, resource string) error`: Deletes a record or collection.

### `Options`

The `Options` struct is used to pass configuration options to the `Driver`, including a custom logger.

### Example Usage

The `main` function demonstrates how to use the `Driver` to perform basic operations:

- Initialize the database driver.
- Write sample user data to a collection.
- Read and print all records from the collection.
- Delete a specific record or handle errors.