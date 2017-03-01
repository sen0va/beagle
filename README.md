# Beagle
> Beacons tracking system

**Note: Work in progress**

## Description
Beagle is a beacon tracking system which targets to run on small devices.
It allows to track user-specific beacons and send notifications to dedicated RESTful services when they appear and disappear.

In current implementation Beagle is supposed to run on small single-board computers like Raspberry Pi.
Therefore default database is SQLite. Additional options may appear in future.

## Prerequisites

### Linux

 * Kernel version 3.6 or above
 * ```bluez```
 * ```bluez-utils```
 * ```libbluetooth-dev```
 * ```libcap2-bin```



## Installation

```sh
git clone https://github.com/blent/beagle
cd beagle
make build
```

### Cross-compile and deploy to a target device

Build and run Beagle on a ARMv5 target device.
```sh
GOARCH=arm GOARM=5 GOOS=linux go build -v -o ./bin/beagle ./src/main.go
```

## Start

Since Beagle programs administer network devices, they must either be run as root, or be granted appropriate capabilities:

```sh
sudo beagle
```

### Options

```sh
  -http
    	enables http server (default true)
  -http-api-route string
    	http server api route (default "/api")
  -http-port int
    	htpp server port number (default 8080)
  -http-static-dir string
    	http server static files directory
  -http-static-route string
    	http server static files route
  -name string
    	application name (default "beagle")
  -storage-connection string
    	storage connection string (default "/var/lib/beagle/database.db")
  -tracking-heartbeat int
    	peripheral heartbeat interval in seconds (default 30)
  -tracking-ttl int
    	peripheral ttl duration in seconds (default 30)
```



