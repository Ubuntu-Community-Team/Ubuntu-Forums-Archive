---
title: "VMware install trouble"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by KDB9000 on 2007-09-26
I didn't find the answer I was looking for. If there is a post about this sorry. I have done the apt-get update, upgrade, build-essential, and the linux-headers. I go and start the install of VMware tools and it makes it to were it needs to compile the drivers. Well it crashed there, on the ethernet drivers to be exact. Once it crashes I have to restart to get the network back. Main OS is Windows with workstation V. 5.5.4 build-44386 with Ubuntu 7.04 as the guest. Anyone have any ideas what else I might need or what else I need to do?

---

### Post by KDB9000 on 2007-09-26
Text from the terminal.

>  ./vmware-install.pl 
A previous installation of VMware software has been detected.

The previous installation was made by the tar installer (version 3).

Keeping the tar3 installer database format.

Uninstalling the tar installation of VMware Tools.

Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

   Guest filesystem driver:-ne                                         done


File /etc/X11/xorg.conf is backed up to /etc/X11/xorg.conf.old.2.

The removal of VMware Tools 5.5.4 build-44386 for Linux completed successfully.
Thank you for having tried this software.

Installing the content of the package.

In which directory do you want to install the binary files? 
[/usr/bin] 

What is the directory that contains the init directories (rc0.d/ to rc6.d/)? 
[/etc] 

What is the directory that contains the init scripts? 
[/etc/init.d] 

In which directory do you want to install the daemon files? 
[/usr/sbin] 

In which directory do you want to install the library files? 
[/usr/lib/vmware-tools] 

The path "/usr/lib/vmware-tools" does not exist currently. This program is 
going to create it, including needed parent directories. Is this what you want?
[yes] 

In which directory do you want to install the documentation files? 
[/usr/share/doc/vmware-tools] 

The path "/usr/share/doc/vmware-tools" does not exist currently. This program 
is going to create it, including needed parent directories. Is this what you 
want? [yes] 

The installation of VMware Tools 5.5.4 build-44386 for Linux completed 
successfully. You can decide to remove this software from your system at any 
time by invoking the following command: "/usr/bin/vmware-uninstall-tools.pl".

Before running VMware Tools for the first time, you need to configure it by 
invoking the following command: "/usr/bin/vmware-config-tools.pl". Do you want 
this program to invoke the command for you now? [yes] 


Stopping VMware Tools services in the virtual machine:
   Guest operating system daemon:-ne                                   done

   Guest filesystem driver:-ne                                         done

Trying to find a suitable vmhgfs module for your running kernel.

None of the pre-built vmhgfs modules for VMware Tools is suitable for your 
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-16-generic/build/include] 

Extracting the sources of the vmhgfs module.

Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmhgfs-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/driver.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/hgfsUtil.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/main.o
  CC [M]  /tmp/vmware-config0/vmhgfs-only/staticEscape.o
  LD [M]  /tmp/vmware-config0/vmhgfs-only/vmhgfs.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config0/vmhgfs-only/vmhgfs.mod.o
  LD [M]  /tmp/vmware-config0/vmhgfs-only/vmhgfs.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
cp -f vmhgfs.ko ./../vmhgfs.o
make: Leaving directory `/tmp/vmware-config0/vmhgfs-only'
The module loads perfectly in the running kernel.

pcnet32                34052  0 
Unloading pcnet32 module

Extracting the sources of the vmxnet module.

Building the vmxnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmxnet-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmxnet-only/vmxnet.o
/tmp/vmware-config0/vmxnet-only/vmxnet.c: In function ‘vmxnet_netpoll’:
/tmp/vmware-config0/vmxnet-only/vmxnet.c:1058: error: too many arguments to function ‘vmxnet_interrupt’
make[2]: *** [/tmp/vmware-config0/vmxnet-only/vmxnet.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmxnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmxnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmxnet-only'
Unable to build the vmxnet module.

The fast network device driver (vmxnet module) is used only for our fast 
networking interface. The rest of the software provided by VMware Tools is 
designed to work independently of this feature.
If you wish to have the fast network driver enabled, you can install the driver
by running vmware-config-tools.pl again after making sure that gcc, binutils, 
make and the kernel sources for your running kernel are installed on your 
machine. These packages are available on your distribution's installation CD.
[ Press Enter key to continue ]

---

### Post by ddrichardson on 2007-09-26
It has been noted in some [vmware forums]("http://communities.vmware.com/message/517149") that this happens with certain vmeare configurations, but nothing seems to be moving on it.

Does the system run without the enhanced net drivers.

---

### Post by KDB9000 on 2007-09-26
It can, but I want to be able to go from windows to ubuntu and back to windows without having to click or press ctrl and alt. Plus the link isn't the same error. It looks like a Xorg problem in the link where mine crashes as it is compiling. I still need to check to see if binutils is installed, if not it might be the problem but I am not sure right now. Looks like a problem with vmxnet.c, is there anyways I can have it compile without doing the network?

---

### Post by ddrichardson on 2007-09-27
Not that I know of, but I have the utilities installed and still need to CTRL/ALT. There probably is if it uses a makefile you could just comment out the vmxnet section.

---

### Post by KDB9000 on 2007-09-27
Fix the problem. Here is the web site that helped me.

[http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_(7.04](http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_(7.04))

It has a part where you add an if statement, it didn't work for me so I commented out 
```
vmxnet_interrupt(dev->irq, dev, NULL);
```
 using /* at the beginning and */ at the end, then added 
```
vmxnet_interrupt(dev->irq, dev);
```
just below it. So the final code looks like this:

 ```
/*   vmxnet_interrupt(dev->irq, dev, NULL); */
     vmxnet_interrupt(dev->irq, dev);
```

What files and how to edit them are in the website.

---

### Post by ddrichardson on 2007-09-27
Good to hear, can you mark it solved to help anyone else searching for the same problem, theres a link in my signature.

---

### Post by sfens on 2007-10-04
I just tried the fix mentioned above, and it worked for me! 

FYI: the URL for the fix is:

[http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_%287.04%29](http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_%287.04%29)

---

### Post by PS8 on 2008-03-01
Sorry, but it seems those links provided in the thread are not working. Could anyone provide fresh working link please?

---

### Post by rryan on 2008-04-27
This link worked for me:

[http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_%287.04%29]("http://www.xastir.org/wiki/index.php/HowTo:Update_Xubuntu_Virtual_Machine_to_Feisty_%287.04%29")

If it doesn't work, go to [http://www.xastir.org/wiki/index.php/Special:Allpages]("http://www.xastir.org/wiki/index.php/Special:Allpages") and click the link from there.

RJ

---

