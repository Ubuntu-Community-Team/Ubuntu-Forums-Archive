---
title: "Vmware workstation 6.5 not working in jaunty"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by w3rt on 2009-01-15
After upgrading to jaunty i tried to install vmware workstation the .bundle file off their website, it installs fine as far as i know, when i try loading it with the gui, nothing happens, so i then tried running it from the command line, i get the following errors

Logging to /tmp/vmware-w3rt/setup-9600.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
Segmentation fault (core dumped)


I have the latest linux headers and cc installed etc, so i have no idea what the problem is, it runs fine under intrepid, so i really am confused, has anyone else experienced this problem?

---

### Post by judgen on 2009-02-04
> **w3rt said:**
> After upgrading to jaunty i tried to install vmware workstation the .bundle file off their website, it installs fine as far as i know, when i try loading it with the gui, nothing happens, so i then tried running it from the command line, i get the following errors

Logging to /tmp/vmware-w3rt/setup-9600.log
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
modinfo: could not find module vmmon
modinfo: could not find module vmnet
modinfo: could not find module vmblock
modinfo: could not find module vmci
modinfo: could not find module vsock
Segmentation fault (core dumped)


I have the latest linux headers and cc installed etc, so i have no idea what the problem is, it runs fine under intrepid, so i really am confused, has anyone else experienced this problem?

I have the exact same problem on Jaunty 64-bit

---

### Post by judgen on 2009-02-04
I have the sollution for you.
First you got to remove the broken module:
sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old

then simply rebuild the module.
sudo vmware-modconfig --console --install-all

It should all work. If you have any problems let me know.

PS: Also you need the current headers for your kernel ofcourse and for obvious reasons the build-essential package to be able to build the modules.

Peace!

---

### Post by icest0rm on 2009-02-05
> **judgen said:**
> I have the sollution for you.
First you got to remove the broken module:
sudo mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old

then simply rebuild the module.
sudo vmware-modconfig --console --install-all

It should all work. If you have any problems let me know.

PS: Also you need the current headers for your kernel ofcourse and for obvious reasons the build-essential package to be able to build the modules.

Peace!

that's working.
thanks

---

### Post by inportb on 2009-02-05
Hm... I've heard that VMware is releasing an opensource VM viewer? How's that coming along? ;p

---

### Post by denisesballs on 2009-02-12
Is there a way to INSTALL Vmware 6.5 on Jaunty Alpha? I have a fresh install that will not go, here is the Vmware installer log:

```
Configuring Bridged network vmnet0
Configuring hostonly network vmnet1, probing for unused subnet ...
Configuring NAT network vmnet8, probing for unused subnet ...
Configured default networks - Bridged, Hostonly, NAT
* Restarting Common Unix Printing System: cupsd
...done.
Unable to install kernel modules
[vmware-workstation 6.5.1] Installation failed, rolling back installation.
VMware DiskMount Utility version 6.5.1, build-126130

Usage: /usr/bin/vmware-mount diskPath [partition num] mountPoint
/usr/bin/vmware-mount [option] [opt args]

There are two modes for mounting disks.  If no option is
specified, we mount individual partitions from virtual disks
independently.  The filesystem on the partition will be
accessible at the mount point specified.

The -f option mounts a flat representation of a disk on a
user-specified mount point.  The user must explicitly unmount
the disk when finished.  A disk may not be in both modes at once.

diskID is an identifier of the form username@hostname:/path/to/vm
for remote disks and just the path for local disks.  Options that
mount a remote disk also require -h -u -F and optionally -v options.
The -v option is required when connecting to a Virtual Center.

Options: -p <diskID>      list all partitions on a disk
-l <diskID>      list all mounted partitions on a disk
-L               list all mounted disks
-d <mountPoint>  cleanly unmount this partition
(closes disk if it is the last partition)
-f <diskPath> <mountPoint> mount a flat representation of the disk
at "mountPoint/flat."
-k <diskID>      unmount all partitions and close disk
-K <diskID>      force unmount all partitions and close disk
-x               unmount all partitions and close all disks
-X               force unmount all partitions and close all disks
Options for remote disks:
-v                inventory path of the vm
-h                hostname of remote server
-u                username for remote server
-F                file containing password
-P                optional TCP port number (default: 902)
,
No mounted disks.
All virtual disks were unmounted successfully
Top level exception handler
Traceback (most recent call last):
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/transaction.py", line 267, in RunTransaction
    txn.Run()
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/transaction.py", line 55, in Run
    self.get()()
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/common.py", line 93, in Show
    i.Execute(txn.temp, onProgress)
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/install.py", line 291, in Execute
    for filePath in source.Install(self._installer.component, dest, self.PreCopy):
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/files.py", line 187, in Install
    component.CopyFile(entry, fileDest)
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/component.py", line 276, in CopyFile
    doit(self, source, dest)
  File "/tmp/vmis.vcMFGD/install/vmware-installer/vmis/core/component.py", line 261, in doit
    for data in fileobj:
  File "/tmp/vmis.vcMFGD/install/vmware-installer/python/lib/gzip.py", line 444, in next
    line = self.readline()
  File "/tmp/vmis.vcMFGD/install/vmware-installer/python/lib/gzip.py", line 399, in readline
    c = self.read(readsize)
  File "/tmp/vmis.vcMFGD/install/vmware-installer/python/lib/gzip.py", line 227, in read
    self._read(readsize)
  File "/tmp/vmis.vcMFGD/install/vmware-installer/python/lib/gzip.py", line 292, in _read
    self._read_eof()
  File "/tmp/vmis.vcMFGD/install/vmware-installer/python/lib/gzip.py", line 311, in _read_eof
    raise IOError, "CRC check failed"
IOError: CRC check failed
Stopping VMware services:
Virtual machine communication interface                                done
Virtual machine monitor                                                done
Blocking file system                                                   done
Usage:
gconftool-2 [OPTION...] - Tool to manipulate a GConf configuration

Help Options:
-?, --help                                     Show help options
--help-all                                     Show all help options
--help-client                                  Show client options
--help-key-type                                Show key type options
--help-load                                    Show load/save options
--help-server                                  Show server options
--help-install                                 Show installation options
--help-test                                    Show test options
--help-schema                                  Show schema options

Application Options:
-v, --version                                  Print version
```

---

