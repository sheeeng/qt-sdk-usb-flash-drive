# Qt SDK from USB Flash Drive

This repository stores Qt SDK from USB flash drive released in 2010.

## Combine Files

Go to `Qt` subdirectory.

Use `combine.sh` script to combine all installation files. Else, use one of the below command.

```
cat qt-sdk-linux-x86-opensource-2010.03.bin-part-* > qt-sdk-linux-x86-opensource-2010.03.bin
cat qt-sdk-linux-x86_64-opensource-2010.03.bin-part-* > qt-sdk-linux-x86_64-opensource-2010.03.bin
cat qt-sdk-mac-opensource-2010.03.dmg-part-* > qt-sdk-mac-opensource-2010.03.dmg
cat qt-sdk-win-opensource-2010.03.exe-part-* > qt-sdk-win-opensource-2010.03.exe
```

## Verify Checksums of Combined Files

Go to `Qt` subdirectory.

```
docker run \
--interactive \
--tty \
--workdir /tmp/workspace \
--volume ${PWD}:/tmp/workspace:ro \
--rm \
fedora:latest \
/bin/bash -c 'sha256sum --check SHA256'
```

## Miscellaneous

### Generate Checksums

Go to `Qt` subdirectory.

```
docker run \
--interactive \
--tty \
--workdir /tmp/workspace \
--volume ${PWD}:/tmp/workspace:rw \
--rm \
fedora:latest \
/bin/bash -c 'sha256sum * | tee SHA256'
```

### Split Files

```
split -b 100m qt-sdk-linux-x86-opensource-2010.03.bin qt-sdk-linux-x86-opensource-2010.03.bin-part-
split -b 100m qt-sdk-linux-x86_64-opensource-2010.03.bin qt-sdk-linux-x86_64-opensource-2010.03.bin-part-
split -b 100m qt-sdk-mac-opensource-2010.03.dmg qt-sdk-mac-opensource-2010.03.dmg-part-
split -b 100m qt-sdk-win-opensource-2010.03.exe qt-sdk-win-opensource-2010.03.exe-part-
```
