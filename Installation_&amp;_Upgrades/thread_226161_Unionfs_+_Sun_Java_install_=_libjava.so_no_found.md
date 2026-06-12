---
title: "Unionfs + Sun Java install = libjava.so no found"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by Celica on 2006-07-30
My setup: Ubuntu 6.06 on USB pen drive with Persistent (casper-rw in a file on a FAT32 patition). Everything works fine, until I try to install Sun Java, which gives me the error: 
```
Error: could not find libjava.so 
Error: could not find Java 2 Runtime Environment.
```
It seems that the system use "the link at /proc/self/exe to determine its installation path, and then uses that path to load libjava.so. After a unionfs mount and chroot, the proc links still point back to the original root." Is there a fix to the probelm? or anyone succefully getting LiveCD with Sun Java?

---

### Post by Celica on 2006-07-31
anyone? This also apply to blackdown java too. What is the proper way to submit bugs?

---

### Post by Siilex on 2007-03-01
Here is a solution, a fast hack:

[http://www.ubuntuforums.org/showpost.php?p=1947183&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1947183&postcount=12)

If somebody still don't gets the point, I explain it further:

- Alice runs his Ubuntu pen drive in "persistent" mode. 
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

- Bob wants to remasterize his Ubuntu live CD, codename Casper.

Both two will face trouble installing sun-java5-bin, and so sun-java5-plugin.

$ sudo apt-get install sun-java5-bin
...
Setting up sun-java5-bin (1.5.0-06-1)...
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment
dpkg: error processing sun-java5-bin (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
sun-java5-bin
...

At this point Bob can not install nor unistall the package, 
leaving the system in a bad position.

Hopefully the files have been copied yet, so Bob can do:
$ strace java
...
 readlink("/proc/self/exe", "/home/bob/remaster-casper/fsrw/usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/bin/java", 4095) = 69
...

After some time, Bob does:
$ mkdir -p /home/bob/remaster-casper/
$ ln -s / /home/bob/remaster-casper/fsrw

Now Bob can do again:
$ sudo apt-get install sun-java5-bin

Remember to remove the link at the end.

---

### Post by mastapat11 on 2007-03-29
i tried **'strace java'** and it gave me this long listing that i couldn't pipe or redirect into a file. 
so i scrolled thru it manually but could not find the line with "readline..."

i'm trying this on Dapper Live CD not from a USB stick if that makes a difference.  Any ideas on this?  Apprecitate any help.

---

