---
title: "Subversion wont install and a plethora of other problems"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by gusjdt on 2007-11-05
Hello, I am new to the forums here and I am also new to Linux. I have tried installing Ubuntu 7.10 on a virtual machine to work on some development projects, but I have encountered many problems along the way. I hope I can get some help from the forums here.

I followed this guide to install Ubuntu 7.10.

[http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware](http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware)

I tried installing the VMware tools but then something happened that I could not connect to my wireless network, so I reinstalled Ubuntu without installing VMware tools.

I am trying to setup the OpenMoko Emulator and I came with some other problems. I am following the instructions here:

[http://wiki.openmoko.org/wiki/OpenMoko_under_QEMU](http://wiki.openmoko.org/wiki/OpenMoko_under_QEMU)

I tried doing the svn command, but it tells me I do 
not have subversion installed so I typed

```
 sudo apt-get install subversion 
```

And I got this error:

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package subversion is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package subversion has no installation candidate

```

So I used the SVN command found in the instructions of the above link using Cygwin on Windows XP, and then I moved the folder qemu-neo1973 (what I got from the SVN) to my desktop on the virtual machine.

So I cd to the desktop and the folder, then I typed

```
 ./configure --target-list=arm-softmmu 
```

and I got this...

```
 WARNING: "gcc" looks like gcc 4.x
Looking for gcc 3.x
gcc 3.x not found!
QEMU is known to have problems when compiled with gcc 4.x
It is recommended that you use gcc 3.x to build QEMU
To use this compiler anyway, configure with --disable-gcc-check

``` 

Tried installing a 3.X version, but it would not let me since I already have a 4.X version. Minutes later I found out that I dont have SDL or Cocoa. When I typed 

```
 sudo apt-get install Cocoa 
``` and ```
 sudo apt-get install SDL 
```


(I dont think that is that right command) I got 

```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Cocoa

``` and ```
 Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package SDL

```

The list goes on... This is really frustrating as I tried searching almost everywhere on google to see if anybody else had similar problems but no luck. I don't expect to solve all of these problems, but even a slight point to a tutorial on correctly installing Ubuntu 7.10 on a virtual machine would be greatly appreciated. Thanks in advance.

---

