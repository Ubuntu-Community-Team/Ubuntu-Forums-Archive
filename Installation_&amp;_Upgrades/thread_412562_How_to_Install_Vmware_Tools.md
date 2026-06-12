---
title: "How to Install Vmware Tools?"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by jchstevens on 2007-04-18
Hi everyone,

Really impressed with what I've seen of Feisty Fawn so far. (:D )
I've tinkered with various versions of linux at home (over many years!), but this looks like a version that I will really be able to recommend to family and friends.
(**Really** impressed with the way it was able to cope with my old sound card, and my Canon MP760 printer)
The only way I can run Ubuntu at work is as a guest on VMWare under XP (:( )
I've installed Ubuntu OK, but how do I install the VMWare Tools?
When I select the VMWare menu options to install VMWare Tools it creates a "CD" on my ubuntu desktop containing an  rpm package and a tgz package.
Do I have to build the Tools from source, or is there an approved Ubuntu package?

Thanks,

Julian

---

### Post by Voland on 2007-04-18
As it said [here]("http://www.vmware.com/community/thread.jspa?messageID=609180"), there is no   pre-compiled VM Tools package for Debian. You can build your own package from sources or try to convert rpm package using Alien.

---

### Post by jchstevens on 2007-04-18
OK, thanks.
I'll try building from source.

Julian

---

### Post by jchstevens on 2007-04-18
Just tried building VMWare Tools and I've got stuck halfway through the perl install script:

[FONT="Courier New"]What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-15-generic/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-15-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.
[/FONT]

Have I given the right header file directory? (uname -r => 2..20-15)
If so, what could be the problem?

Thanks,

Julian

---

### Post by Voland on 2007-04-18
Try *sudo apt-get install kernel-headers*

---

### Post by jchstevens on 2007-04-18
> **Voland said:**
> Try *sudo apt-get install kernel-headers*
I've tried this, but I get the following:
[FONT="System"]root@Feisty-Fawn:~# apt-get install kernel-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kernel-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-headers has no installation candidate[/FONT]

Maybe I need to wait for the official Feisty Fawn to come out?

---

### Post by Voland on 2007-04-18
Sorry, my misprint: instead  "kernel-headers" you need to install "linux-headers"

---

### Post by jchstevens on 2007-04-19
> **Voland said:**
> Sorry, my misprint: instead  "kernel-headers" you need to install "linux-headers"

Tried kernel-headers but it needed a more specific name:
[FONT="System"]Package linux-headers is a virtual package provided by:
  linux-headers-2.6.20-15-server-bigiron 2.6.20-15.27
  linux-headers-2.6.20-15-server 2.6.20-15.27
  linux-headers-2.6.20-15-lowlatency 2.6.20-15.27
  linux-headers-2.6.20-15-generic 2.6.20-15.27
  linux-headers-2.6.20-15-386 2.6.20-15.27
  linux-headers-2.6.20-15 2.6.20-15.27
You should explicitly select one to install.
[/FONT]

Tried installing linux-headers-2.6.20-15-generic, but this is already installed:
[FONT="System"]root@Feisty-Fawn:~# apt-get install linux-headers-2.6.20-15-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

Thanks again for the advice, but the vmware-install.pl script is still complaining!

---

### Post by Anicka on 2007-04-19
> **jchstevens said:**
> Thanks again for the advice, but the vmware-install.pl script is still complaining!

Isn't it vmware-config-tools.pl that you should run? Your Ubuntu is the guest i XP, right?

```
sudo alien --scripts /cdrom/VMwareTools*.rpm
sudo dpkg -i vmwaretools*.deb
sudo vmware-config-tools.pl
```

---

### Post by jchstevens on 2007-04-19
> **Anicka said:**
> Isn't it vmware-config-tools.pl that you should run? Your Ubuntu is the guest i XP, right?

```
sudo alien --scripts /cdrom/VMwareTools*.rpm
sudo dpkg -i vmwaretools*.deb
sudo vmware-config-tools.pl
```

Actually it is vmware-config-tools.pl that is failing. (vmware-config.pl calls this script at the end.)
I don't have alien installed and I'm not sure how to get it.
My machine is behind a firewall so I need to specify a proxy server somehow.
If I use the GUI "Add/Remove Applications", this knows about the proxy, but doesn't list alien as being installable.  If I try:
```
apt-get install alien
```
 from a shell, then it can't get through the firewall.
Any ideas?

Thanks,

Julian

---

### Post by Voland on 2007-04-19
Try to use Synaptic to install alien

---

### Post by jchstevens on 2007-04-19
> **Voland said:**
> Try to use Synaptic to install alien
OK. Got alien using Synaptic and converted rpm to deb.
Installed deb using Dpkg, but didn't find vmware-config-tools.pl.
Checked in Synaptic which only lists vmware-tools-kernel-modules - and these aren't installed.
Used Synaptic to install - still no perl script, just libraries!

---

### Post by jchstevens on 2007-04-19
Oh, wait.... just found a whole load more vmware packages in Synaptic.
Not sure why Dpkg didn't install but I'm going to use Synaptic to complete the job.

---

### Post by jchstevens on 2007-04-19
Right.  vmware-config-tools.pl is still prompting for the C header files and I'm stuck here again?:
[HTML]What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-15-generic/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic). Even if the module were to
compile successfully, it would not load into the running kernel.[/HTML]

:confused:

---

### Post by tommy_k on 2007-04-19
I managed to install vmware client tools, but it is not for faint of heart. It is ugly and doesn't use package management. If you follow these instructions, you can break your brand new Ubuntu. You get to keep all pieces :).

Also, if you are getting mismatch between running kernel and headers, check your kernel version using command "uname -r".

1. Install vmware-tools-kernel-modules from repository.

2. Unpack VMwareTools-X.Y.Z-NNNN.tar.gz from vmware's virtual cd into your home directory and cd inside.

```

tar xfz '/media/cdrom0/VMwareTools-5.5.3-34685.tar.gz'
cd vmware-tools-distrib

```

3. Run client tools installation

```

~$ sudo ./vmware-install.pl

```

4. Answer all questions, when it asks to run vmware-config-tools.pl, allow it.

5. It will try to build its drivers, but the build process will fail. It doesn't matter, you installed them in step 1 anyway.

6. Copy mouse driver into your X installation. Config tool doesn't, because Ubuntu uses X 7.2 and client tools contain driver for X 7.0:

```

sudo cp /usr/lib/vmware-tools/configurator/XOrg/7.0/vmmouse_drv.so /usr/lib/xorg/modules/input/

```

7. Configure your mouse in xorg.conf. Configurator did change display driver to vmware driver, but not the mouse driver.

```

sudo pico /etc/X11/xorg.conf

```

Find line:

```

Driver "mouse"

```

and change it to:

```

Driver "vmmouse"

```

8. If you want to change your screen resolution, now is the time. For example, if you like to use quickswitch mode at 1280x1024 resolution, add this modeline:

```

ModeLine "1280x996" 100 1280 1300 1400 1500 996 1000 1100 1200

```

and change to this mode in corresponding Modes lines.

9. Restart your X to verify everything is ok. Now your mouse should be able to move outside vmware window.

10. Now is time to get your network working. Edit the file /etc/modules.conf

```

sudo pico /etc/modules.conf

```

and change the eth0 alias to 'vmxnet'. At command line, run these commands:

```

sudo modprobe vmxnet
sudo ifconfig eth0 up

```

Now, you should be able to use network connection.

11. At next login, Restricted Driver Manager will ask you about new drivers.

---

### Post by jchstevens on 2007-04-20
> **tommy_k said:**
> I managed to install vmware client tools, but it is not for faint of heart. It is ugly and doesn't use package management. If you follow these instructions, you can break your brand new Ubuntu. You get to keep all pieces :).

Also, if you are getting mismatch between running kernel and headers, check your kernel version using command "uname -r".

1. Install vmware-tools-kernel-modules from repository.

2. Unpack VMwareTools-X.Y.Z-NNNN.tar.gz from vmware's virtual cd into your home directory and cd inside.

```

tar xfz '/media/cdrom0/VMwareTools-5.5.3-34685.tar.gz'
cd vmware-tools-distrib

```

3. Run client tools installation

```

~$ sudo ./vmware-install.pl

```
... snip ...
Thanks for all this advice - much appreciated.  However, I can't get past the bit in vmware-config-tools.pl where it tries to build vmhgfs!
My kernel version is definitely **2.6.20-15-generic**, but when I tell it the headers are in:
```
/usr/src/linux-headers-2.6.20-15-generic/include
```
It comes back with:
```
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic). Even if the module were to
compile successfully, it would not load into the running kernel.

```
This is driving me nuts! :(

---

### Post by jonom on 2007-04-20
> **jchstevens said:**
> 
This is driving me nuts! :(

Do you need vmware specifically?

Virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) runs great and is an easy install. And there is also KVM which I haven't tried yet - there are a couple of others as well.

---

### Post by tommy_k on 2007-04-20
> **jchstevens said:**
> Thanks for all this advice - much appreciated.  However, I can't get past the bit in vmware-config-tools.pl where it tries to build vmhgfs!
My kernel version is definitely **2.6.20-15-generic**, but when I tell it the headers are in:
```
/usr/src/linux-headers-2.6.20-15-generic/include
```
It comes back with:
```
The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match
your running kernel (version 2.6.20-15-generic). Even if the module were to
compile successfully, it would not load into the running kernel.

```
This is driving me nuts! :(

Did you enter the headers directory by hand, or the configurator detected it automatically? Mine detects different directory:
```

/lib/modules/2.6.20-15-generic/build/include

```

Anyway, it should be link to your /usr/src directory. Make sure you have file linux/version.h there. Also, check your version of vmware tools, this is from vmware-config.pl:

> 
Kernels before 2.6.18 declare UTS_RELEASE in version.h. Newer kernels
use utsrelease.h. We include both just in case somebody moves UTS_RELEASE
back while leaving utsrelease.h file in place.


If you have older vmware application, you may have old client tools version that can't handle newer kernels. Get client tools from latest workstation or server (vmware installation directory contains several iso files, linux.iso is what you are looking for).

---

### Post by jchstevens on 2007-04-20
> **tommy_k said:**
> Did you enter the headers directory by hand, or the configurator detected it automatically? Mine detects different directory:
```

/lib/modules/2.6.20-15-generic/build/include

```

Anyway, it should be link to your /usr/src directory. Make sure you have file linux/version.h there. Also, check your version of vmware tools, this is from vmware-config.pl:



If you have older vmware application, you may have old client tools version that can't handle newer kernels. Get client tools from latest workstation or server (vmware installation directory contains several iso files, linux.iso is what you are looking for).
Thanks for this.  I think it's begining to make sense!
My kernel release is in utsrelease.h (not in version.h) and my vmware-config.pl script doesn't check in there.  I guess my vmware version (5.0.0) is too old for this release of ubuntu.
Do you think I can get an updated vmware-config.pl, or do I really need to upgrade my vmware?

---

### Post by jchstevens on 2007-04-20
> **jonom said:**
> Do you need vmware specifically?

Virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/) runs great and is an easy install. And there is also KVM which I haven't tried yet - there are a couple of others as well.

VMWare is kind of mandated at work, but this looks very interesting for home use. Thanks.

---

### Post by tommy_k on 2007-04-20
> **jchstevens said:**
> Thanks for this.  I think it's begining to make sense!
My kernel release is in utsrelease.h (not in version.h) and my vmware-config.pl script doesn't check in there.  I guess my vmware version (5.0.0) is too old for this release of ubuntu.
Do you think I can get an updated vmware-config.pl, or do I really need to upgrade my vmware?

No, you don't need to upgrade vmware. All you need is newer version of client tools. Download latest vmware server (or workstation trial, but server 1.0.2 is newer) and get the tools from there. It will work with your older vmware workstation.

---

### Post by jchstevens on 2007-04-20
> **tommy_k said:**
> No, you don't need to upgrade vmware. All you need is newer version of client tools. Download latest vmware server (or workstation trial, but server 1.0.2 is newer) and get the tools from there. It will work with your older vmware workstation.
OK, now I'm getting somewhere! Followed your advice and have managed to install vmware-tools. 
 Thanks for your help, I don't think I would have got here on my own!
Didn't go quite smoothly, though - vmhgfs still bombed out (see below) - but I can now use 1280x1024 resolution.  I believe vmhgfs is used to share files between host and guest O/S so this would be useful.
What do you think about the following error:
```
Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmhgfs-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/driver.o
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsChangeFileAttributes’:
/tmp/vmware-config2/vmhgfs-only/driver.c:763: error: ‘struct inode’ has no member named ‘i_blksize’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsInitializeInode’:
/tmp/vmware-config2/vmhgfs-only/driver.c:835: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsIget’:
/tmp/vmware-config2/vmhgfs-only/driver.c:884: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsCreate’:

. . .   snip   . . .

/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsClearInode’:
/tmp/vmware-config2/vmhgfs-only/driver.c:4105: error: ‘struct inode’ has no member named ‘u’
make[2]: *** [/tmp/vmware-config2/vmhgfs-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmhgfs-only'
Unable to build the vmhgfs module.
```

---

### Post by xavierh on 2007-04-20
Thanks Tommy_k.....I was able to follow your instructions and now my mouse works on my VM

Thanks again

---

### Post by tommy_k on 2007-04-20
> **jchstevens said:**
> OK, now I'm getting somewhere! Followed your advice and have managed to install vmware-tools. 
 Thanks for your help, I don't think I would have got here on my own!
Didn't go quite smoothly, though - vmhgfs still bombed out (see below) - but I can now use 1280x1024 resolution.  I believe vmhgfs is used to share files between host and guest O/S so this would be useful.
What do you think about the following error:
```
Building the vmhgfs module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config2/vmhgfs-only'
make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpName.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/cpNameLinux.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/dev.o
  CC [M]  /tmp/vmware-config2/vmhgfs-only/driver.o
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsChangeFileAttributes’:
/tmp/vmware-config2/vmhgfs-only/driver.c:763: error: ‘struct inode’ has no member named ‘i_blksize’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsInitializeInode’:
/tmp/vmware-config2/vmhgfs-only/driver.c:835: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsIget’:
/tmp/vmware-config2/vmhgfs-only/driver.c:884: error: ‘struct inode’ has no member named ‘u’
/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsCreate’:

. . .   snip   . . .

/tmp/vmware-config2/vmhgfs-only/driver.c: In function ‘HgfsClearInode’:
/tmp/vmware-config2/vmhgfs-only/driver.c:4105: error: ‘struct inode’ has no member named ‘u’
make[2]: *** [/tmp/vmware-config2/vmhgfs-only/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config2/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/vmware-config2/vmhgfs-only'
Unable to build the vmhgfs module.
```

No problem, glad to help.

About vmhgfs - it did the same thing for me, too. I don't use this functionality, so it was just ignored. If you check the vmware-tools-kernel-modules package, it doesn't contain this module either. Chalk it up to those famous kernel API breakages :).

---

### Post by tjabri on 2007-04-22
Thanks for the information regarding the mouse issue. It was driving me up the wall.

However, on a different note, has anyone had luck with the networking?

This is what happens on my vmware Feisty. I have the vmxnet installed and loaded, it shows up on the restricted drivers notifier and you can see it as a loaded module, however, when I click on the NetworkManager applet, it shows the driver in use is pcnet32. I tried removing from the modules.conf, and doing a sudo rmmod pcnet32 and if it's not loading, I have no networking. Does the vmxnet module affect network performance at all? If so, has anyone gotten it to work without needing pcnet32?

Thanks!

---

### Post by wrycatcher on 2007-04-24
(after rereading the previous post, seems I misunderstood the question...but maybe this is helpful to someone anyway)

The following is an excerpt from here:    [http://www.vmware.com/community/thread.jspa?threadID=62836&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=62836&tstart=0)

- unpack vmtools into tmp. 
- mkidr /tmp/vmxnet 
- cd /tmp/vmxnet 
- tar xf /tmp/vmware-tools-distrib/lib/modules/source/vmxnet.tar 
- fix vmxnet.c 
- tar cf vmxnet.tar vmxnet-only 
- cp vmxnet.tar /tmp/vmware-tools/distrib/lib/modules/source/vmxnet.tar 
rerun the installation.

hint:  When it says "fix vmxnet.c" that means go to line 1058 (in my version, anyway) and remove the last argument altogether, and save.  In my version, this line was causing a compiliation error.  In case your version shows it on a different line, here's the code (pre-update):  ```
vmxnet_interrupt(int irq, void *dev_id, NULL)
```

This worked for me perfectly when Feisty was in beta and still works now.  You should be able to accept all the default options, and then at the end of the install it will kcik off the vmware-tools-config.pl which spells out a few commands you need to issue regarding networking.  **Make sure to do those otherwise your network devices won't work.**

---

### Post by stephenk on 2007-04-26
I tried this but "fix vmxnet.c" doesn't work - the fix command isn't found.  How do I install this?

---

### Post by tommy_k on 2007-05-02
> **stephenk said:**
> I tried this but "fix vmxnet.c" doesn't work - the fix command isn't found.  How do I install this?

Why bother with compilation? Install package **vmware-tools-kernel-modules** from repository. It contains compiled vmxnet and as a bonus, it will be updated together with kernel, saving you any troubles in future.

---

### Post by Anicka on 2007-05-02
> **tommy_k said:**
> 10. Now is time to get your network working. Edit the file /etc/modules.conf

```

sudo pico /etc/modules.conf

```

and change the eth0 alias to 'vmxnet'. At command line, run these commands:

```

sudo modprobe vmxnet
sudo ifconfig eth0 up

```

Now, you should be able to use network connection.

When I type ```

sudo ifconfig eth0 up
```I get > eth0: ERROR while getting interface flags: No such device Could it be caused by that I use NAT and not bridge-network? The vmxnet driver appears in the restricted modules, but the network insists on using pcnet32 (eth1). Any suggestions?

---

### Post by tommy_k on 2007-05-06
> **Anicka said:**
> When I type ```

sudo ifconfig eth0 up
```I get  Could it be caused by that I use NAT and not bridge-network? The vmxnet driver appears in the restricted modules, but the network insists on using pcnet32 (eth1). Any suggestions?

You are not supposed to have eth1. Shut this interface down and then remove pcnet32 from kernel ('sudo rmmod pcnet32'). pcnet32 and vmxnet are mutually exclusive, they drive the same 'virtual hardware'. Also when something doesn't work, check your system log, especially after modprobe. Any failure will show up there.

---

