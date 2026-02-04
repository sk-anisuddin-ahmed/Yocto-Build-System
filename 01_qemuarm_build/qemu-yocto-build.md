# Yocto QEMU ARM (qemuarm) Build Process (kirkstone)

## Clone poky and checkout `kirkstone`

```bash
git clone git://git.yoctoproject.org/poky
cd poky
git checkout kirkstone
```

## Initialize the build environment

```bash
source oe-init-build-env
```

This creates `build/conf/local.conf` and `build/conf/bblayers.conf` if they don’t exist.

## Configure the target machine

Edit the config and set the machine to `qemuarm`:

```bash
nano build/conf/local.conf
```

Add or update:

```conf
MACHINE ?= "qemuarm"
```

## Build the image

```bash
bitbake core-image-minimal
```

## Run the image in QEMU (nographic)

```bash
runqemu qemuarm nographic
qemuarm login:
```
Login as `root`.

## Verify

```bash
uname -a
uname -m
free -h
df -h
```