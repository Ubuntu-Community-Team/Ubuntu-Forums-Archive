---
title: "[SOLVED] Installing onto unsupported RAID array"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by Stant0n on 2007-09-24
> I've posted my solution in [post #8](http://ubuntuforums.org/showpost.php?p=3641049&postcount=8) 
What I've done is built a server with a massive storage array that I want to install Ubuntu on.  
I'm using an AMD 64 Athlon 3000+ system with a Highpoint RocketRAID 1740 and 4 Seagate 1TB drives in a RAID 5 array.

The problem is that Highpoint doesn't provide precompiled drivers for Ubuntu.  They have drivers for Redhat and Suse and provide source code to compile your own driver (So there should be hope right?).  What I've done is booted this system with the Desktop installation CD,  and loaded the Live desktop.  I've downloaded the source for the driver and compiled it (after some modifications).   This gives me a file,  rr174x.ko that I use insmod to load.   When loaded,  Ubuntu's installer see's the array as a 800gb array (way too small), but if I use parted,  I see the whole 3 Terabytes.  

So I partition with parted and begin the install.   however Grub fails every time saying that the file system is type 0xee and then quits.  

I've been hammering on this for several days and can't figure it out.   I was thinking that if I could "slipstream" the compiled driver into the install disk,  perhaps the install would work.  I also have no idea how to make a driver update CD so that I could load the driver during install. 

I've followed the installation instructions in the FakeRaid guide which gets the entire installation onto the disks but then fails at the Grub installation.    So close!  If I could get Grub to install I think I could have this system running.

---

### Post by Stant0n on 2007-09-27
OK,  so much work and testing later.  I've made some progress but am at another wall.

What I've done...  Downloaded the 7.04 server iso and loaded it up on the server.
I've used my laptop to compile multiple versions of the module for my RAID array. 

Module built against the following version headers:
2.6.20-15-generic
2.6.20-15-server
2.6.20-15-i386

I then copied these modules to a USB drive and plugged it into the server during installation.
When the installer loads the partitioner,  I back out of the install and select the option from the main menu to execute a shell.  

Running `uname -r` at this shell prints
2.6.20-15-generic

So I load the generic module and get an error -Invalid module format
So I load the i386 module and everything becomes recognized.
I setup the partitions on the array to my liking and continue the installtion

Fatal Error with grub-install on (hd0)

Ok, no big deal, I use Lilo and it installs no problems.

Now for the real deal...
When the server boots,  lilo launches.  (OMG FINALLY)
Bad news,  lilo can't see the root partition.
I get a bourne shell with initramfs prompt.
I try to load the 2.6.20-15-i386 module   error: - Invalid Module Format

`uname -r`
2.6.20-15-server

I can load the 2.6.20-15-server module and I can see my array again.

Now how to I continue the boot up?  How do I correct this problem?



And to make matters worse,  I also get repeating errors dumping to the screen:

ata1: soft reseting port
ATA: abnormal status 0x7f on port 0x0001dc07
ATA: abnormal status 0x7f on port 0x0001dc07
ata1.00: configure for UDMA/33
ata1: EH complete
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 actions 0x2 frozen
ata1.00 cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 254 in
              res 40/00:03:00:00:20/00:00:00:00:00/a0 Emask 0x4 (time out)
(repeats)


Some advice please!

---

### Post by jboomer on 2007-09-27
do you have the pre compiled drivers for the 1740 card.  if you could those to me i have similar situation.  working on a resolution

---

### Post by Stant0n on 2007-09-28
links deleted

---

### Post by Stant0n on 2007-10-01
Can anyone offer any advice here?  Am I stuck using Redhat or Windows on this system?

Really all I need is a guide to install Ubuntu on a storage system that requires a third party driver/module.

How can this be so difficult?  

To recap where I'm at:

Install runs fine until the partitioner loads.  At which point I drop to a shell,  load the necessary module to recognize the RAID array, then continue installation.   Grub installation fails, but using LILO works fine.
The system restarts, LILO launches, booting begins.

As storage devices are being detected, the kernel errors with:

Done.
Check root= bootarg cat /proc/cmdline
or missing modules, devices cat /proc/modules ls /dev
ALERT! /dev/sdb3 does not exist. Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-ubuntu3) built in shell (asb)
Enter Help for a list of built-in commands
/bin/sh can't access tty:  job control turned off

{initramfs} cat /proc/cmdline
auto BOOT_IMAGE=Linux ro root=/dev/sdb3
{initramfs}cat /proc/modules
... lots of modules,  rr174x.ko is not listed
{initramfs}cat /dev/sd*
/dev/sda   
/dev/sda1
... this is my USB thumb drive used to load the driver during installation

---

### Post by Stant0n on 2007-10-03
bump

---

### Post by Stant0n on 2007-10-04
Shameless bump

---

### Post by Stant0n on 2007-10-26
It's been 3 weeks.  I've finally made some real progress. 
For anyone else that has a RocketRaid Highpoint array and wants to install linux,  here's how I got it to boot.

I'm still troubleshooting things, but have successfully booted Kubuntu i386 version and Ubuntu AMD64 version.  I'm pretty sure this will work regardless of what version of Ubuntu you're trying out. 

*What will this rundown help me do?*
Install your flavor of Ubuntu (possibly other distros) onto a Highpoint RocketRAID 1740, without a floppy disk.  This rundown will probably work for any controller that you have source code drivers for. 

*What do I need?*
A Live CD that will boot up to the desktop with network support (able to access the internet). 
Both my successful installs used a 7.10 Ubuntu Live CD

**The Procedure**
Pop in your Live CD and boot to the desktop.  Launch the web browser and download the source code of your drivers from the manufacturer's website to the /tmp directory.
[RocketRaid 1740 Drivers]("http://www.highpoint-tech.com/BIOS_Driver/rr1740/Linux/rr174x-linux-src-v1.03-082307-0910.tar.gz")
[RocketRaid 1720 Drivers]("http://www.highpoint-tech.com/BIOS_Driver/rr172x/Linux/rr172x-linux-src-v1.0-082307-0825.tar.gz")

Open up a terminal and extract the source code from the downloaded tarball.  In the cd command below, I'm moving to the extracted directory that contains the makefile.  Be sure you modify the command to move to the directory of the makefile in your extracted tarball.

```
cd /tmp
tar xvf rr174x-linux-src-v1.03-082307-0910.tar.gz 
cd rr174x-linux-src-v1.03/product/rr174x/linux/
```



Next is to compile and and install the source code.  To do this, you need to install the compiler first.  

```
sudo apt-get update
sudo apt-get install build-essential
```

Now you can run make with the arguments needed for your install.  I'm using an AMD64 system so I added the ARCH argument to specify this.  You can see all the available arguments in the README file included with the source code.

```
sudo make ARCH=x86_64

```

When the compiling is finished, you need to insert the new module for setup to work. Substitute rr174x.ko with the driver name you compiled earlier if different.

```
sudo insmod -p rr174x.ko
sudo depmod -ae
ls /dev/sd*
```


Now the drives are recognized, you can run the installation via the Install icon on the desktop.  

The tricky part here is that Grub wont install on a GPT partition table and I don't think msdos partition tables support partitions larger than 2.199 TB.  I had to play with the partitions a bit to get a successful installation, so if you run into trouble, it's likely a problem with how you partitioned your drives (I'm guessing).  I've got a 3TB drive that I've partitioned like this

/dev/sda1   256 MB  /boot  ext3        primary
/dev/sda2   801 GB  /          reiserfs   primary
/dev/sda3       2 GB             swap       primary
/dev/sda4 2198 GB /home  xfs          primary

Set the rest of your settings and finish the install.  However, once installation completes, 
**DON'T REBOOT.**

Once installation is complete, we need to mount the installation and compile the driver into the boot image.  Lets copy the source we need to the new installation. (be sure to use the correct device name for your system in the commands below.  (e.g.  if you only have a root partition skip the /target/boot command. If you only have /dev/sda1 use that for the /target command)

```
sudo mount /dev/sda2 /target
sudo mount /dev/sda1 /target/boot
cd /tmp
cp -r rr174x-linux-src-v1.03 /target/tmp/
sudo chroot /target
```

Now you need to mount the running proc and sysfs to the local installation.

```
umount proc
umount sysfs
mount
mount -t proc proc /proc
mount -t sysfs sysfs /sys
```


Now, Highpoint specifically calls mkinitrd as part of the installation process.  Unfortunately, Ubuntu doesn't use mkinitrd, but instead uses mkinitramfs.  The work around that I used was to simply link mkinitrd to mkinitramfs and everything installs fine.  (as far as I know) 

```

ln /usr/sbin/mkinitramfs /usr/sbin/mkinitrd
```


Now install with the arguements you need.

```
cd /tmp/rr174x-linux-src-v1.03/product/rr174x/linux/
make clean
make ARCH=x86_64
make install
exit
```

Now reboot the system, and remove the Live CD from the drive.  Your new linux installation should boot up!

---

### Post by Stant0n on 2007-10-30
Updated my solution to show how I was able to get access to all 3 terabytes of the storage array. 

It's not an elegant solution, but I couldn't find any way to force the installer to use a GPT partition table over an MSDOS partition table.  Please post a link to any solutions to this limitation.

---

### Post by scoob_2000 on 2007-11-02
Many thanks Stant0n,

I have successfully got a similar system going following your instructions.

I followed the same procedure with an AMD 3500 and Highpoint Rocket RAID 1720 card.

---

### Post by n_lion on 2007-11-27
Stant0n,  I also used this for a RocketRaid 1720.  I am able to mount my 2-500GB drives immediately after I mkfs (either ext2 or ext3) one of the partitions.  But after I reboot, the partitions will not mount until I mkfs again.

Suggestions?

---

### Post by therufus on 2007-12-27
I followed your steps, but when it got to the 'sudo insmod -p rr174x.ko' all I get back is "insmod: error inserting 'rr174x.ko': -1 No such device".

Help!

---

### Post by therufus on 2007-12-27
Solved. The driver that works (for me anyway) is located [here](http://www.highpoint-tech.com/BIOS_Driver/rr172x/Linux/rr172x-linux-src-v1.0-082307-0825.tar.gz).

---

### Post by hedefalk on 2007-12-27
If you haven't been compiling any kernel before, you'll probably need to:
```
sudo apt-get install linux-headers-generic
```
or similar to get the kernal headers needed before trying to build the drivers. You could also specify a manually configured kernel source tree with ```
make KERNELDIR=…
```

---

### Post by Stant0n on 2008-01-11
> **n_lion said:**
> Stant0n,  I also used this for a RocketRaid 1720.  I am able to mount my 2-500GB drives immediately after I mkfs (either ext2 or ext3) one of the partitions.  But after I reboot, the partitions will not mount until I mkfs again.

Suggestions?

Sorry for the late reply...   I had a lot of trouble figuring out successfully booting partitions on this system.  The main problem was that I simply could not get the GPT to cooperate and ended up with a similar sounding problem to what you have.   Check that you're labeling your partition tables in MSDOS format.


> **therufus said:**
> Solved. The driver that works (for me anyway) is located here.

I've gotten a few PM's about the 1720, so I've added your link to my rundown.

> **hedefalk said:**
> If you haven't been compiling any kernel before, you'll probably need to:


When using the 7.10 Live CD, the linux headers source files are already installed.  Also see the README file for a listing of all make options.

---

### Post by Skulle on 2008-01-23
> **Stant0n said:**
> 
```
sudo make ARCH=x86_64

```
When the compiling is finished, you need to insert the new module for setup to work. Substitute rr174x.ko with the driver name you compiled earlier if different.


I can not get the RocketRaid 1740 sourcecode truth the compilation/make without warnings...
...also receiving errors when trying to load the driver into kernel. :(

PC1: My "new" server, an old Compaq AP230(1GHz PIII, 512MB) with RocketRaid 1740 (2xSamsung 500GB)... right now run the Live-version of Ubuntu due to driver issue with the  RocketRaid 1740.

PC2: Ubuntu 7.10 PC on a Dell C810 Laptop. This is the machine where I have tried to compile the driver. Then via old fashion diskette transfer the driver (rr174x.ko) to  my server.

**On my Laptop:**
```

root# **make clean**
root# **make**
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /1740/product/rr174x/linux/.build/os_linux.o
  CC [M]  /1740/product/rr174x/linux/.build/osm_linux.o
/1740/product/rr174x/linux/.build/osm_linux.c: I funktion "hpt_detect":
/1740/product/rr174x/linux/.build/osm_linux.c:286: varning: "pci_find_device" bör undvikas (deklarerad vid include/linux/pci.h:477)
/1740/product/rr174x/linux/.build/osm_linux.c:371: varning: "deprecated_irq_flag" bör undvikas (deklarerad vid include/linux/interrupt.h:66)
  CC [M]  /1740/product/rr174x/linux/.build/div64.o
  CC [M]  /1740/product/rr174x/linux/.build/hptinfo.o
  CC [M] /1740/product/rr174x/linux/.build/config.o
  LD [M]  /1740/product/rr174x/linux/.build/rr174x.o
  Building modules, stage 2.
  MODPOST 1 modules
[COLOR="Red"]WARNING: could not find /1740/product/rr174x/linux/.build/.him_rr1740.o.cmd for /1740/product/rr174x/linux/.build/him_rr1740.o[/COLOR]
  CC      /1740/product/rr174x/linux/.build/rr174x.mod.o
  LD [M]  /1740/product/rr174x/linux/.build/rr174x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
root#

```
The resulting rr174x.ko file is 741260byte large (724kB) - Is that a reasonable size :confused:
Can a compile my driver on a other machine like this?:confused:

**On my server**
When I try to load the module into kernel on the target machine i get the following.
```

ubuntu@ubuntu:/media/disk$ **sudo insmod rr174x.ko -p**
[COLOR="Red"]insmod: error inserting 'rr174x.ko': -1 Unknown symbol in module[/COLOR]
ubuntu@ubuntu:/media/disk$

```

Does anyone have a working 'rr174x.ko' file for 7.10, PII/i386 that he could post/send?

Thanks
Skull  ](*,)

---

### Post by sreese on 2008-01-24
hey guys im trying install the drivers for my highpoint rocketraid 1720 card and I followed the instructions and it works great up until the point where i try to compile the drivers. I have ubuntu server 6.06 installed, currently running off of 7.10 desktop cd. 

This is the error I receive.
```

ubuntu@ubuntu:/tmp/rr172x-linux-src-v1.0/product/rr1720/linux$ sudo make ARCH=i386
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/os_linux.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.o
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c: In function &#8216;hpt_detect&#8217;:
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c:286: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c:371: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/div64.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/hptinfo.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/config.o
make[2]: *** No rule to make target `/tmp/rr172x-linux-src-v1.0/lib/linux/free-i386-regparm3/him_rr1720.o', needed by `/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/him_rr1720.o'.  Stop.
make[1]: *** [_module_/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [rr172x.ko] Error 2
ubuntu@ubuntu:/tmp/rr172x-linux-src-v1.0/product/rr1720/linux$ sudo insmod -p rr172x.ko
insmod: can't read 'rr172x.ko': No such file or directory
ubuntu@ubuntu:/tmp/rr172x-linux-src-v1.0/product/rr1720/linux$ 
ubuntu@ubuntu:/tmp/rr172x-linux-src-v1.0/product/rr1720/linux$ sudo make ARCH=i386
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/os_linux.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.o
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c: In function &#8216;hpt_detect&#8217;:
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c:286: warning: &#8216;pci_find_device&#8217; is deprecated (declared at include/linux/pci.h:477)
/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/osm_linux.c:371: warning: &#8216;deprecated_irq_flag&#8217; is deprecated (declared at include/linux/interrupt.h:66)
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/div64.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/hptinfo.o
  CC [M]  /tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/config.o
make[2]: *** No rule to make target `/tmp/rr172x-linux-src-v1.0/lib/linux/free-i386-regparm3/him_rr1720.o', needed by `/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build/him_rr1720.o'.  Stop.
make[1]: *** [_module_/tmp/rr172x-linux-src-v1.0/product/rr1720/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [rr172x.ko] Error 2
```

Any Ideas on what the "Error 2" means and what I can do to solve this problem? Please let me know and thanks for the help.

---

### Post by lsilver on 2008-01-26
I'm trying to install a Highpoint Rocketraid 2300 raid controller onto an AMD64 machine running Ubuntu 6.06.

Following instructions above I have installed the kernel-headers and the various build-essential etc.  However, when I try to build the driver I get the following error output which is very similar to that reported above.  Any ideas how to correct these errors?

Thanks, Leo.

sudo make ARCH=x86_64
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-51-amd64-generic'
  CC [M]  /home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.o
/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.c: In function ‘refresh_sd_flags’:
/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.c:261: warning: implicit declaration of function ‘mutex_lock’
/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.c:261: error: ‘struct inode’ has no member named ‘i_mutex’
/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.c:267: warning: implicit declaration of function ‘mutex_unlock’
/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.c:267: error: ‘struct inode’ has no member named ‘i_mutex’
make[2]: *** [/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build/os_linux.o] Error 1
make[1]: *** [_module_/home/lsilver/Desktop/rr231x_0x-linux-src-v2.1/product/rr2310pm/linux/.build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-51-amd64-generic'
make: *** [rr2310_00.ko] Error 2

---

### Post by Stant0n on 2008-02-20
> **Skulle said:**
> 

PC1: My "new" server, an old Compaq AP230(1GHz PIII, 512MB) with RocketRaid 1740 (2xSamsung 500GB)... right now run the Live-version of Ubuntu due to driver issue with the  RocketRaid 1740.

PC2: Ubuntu 7.10 PC on a Dell C810 Laptop. This is the machine where I have tried to compile the driver. Then via old fashion diskette transfer the driver (rr174x.ko) to  my server.


Does your server not have an internet connection?  I think you'd be best off using this guide straight from the server.   In any case,  I'm thinking the problem is probably the headers you're compiling against.   If you run a uname -r on the server,  does its kernel version match the uname -r of the laptop?  If not, you can download the headers for your server to the laptop, then use the make option to specify the new headers source to compile against.  



> **Skulle said:**
> 
The resulting rr174x.ko file is 741260byte large (724kB) - Is that a reasonable size :confused:
Can a compile my driver on a other machine like this?:confused:


724KB is approximately the same size of the drivers I have compiled.

---

### Post by Stant0n on 2008-02-20
> **sreese said:**
> Any Ideas on what the "Error 2" means and what I can do to solve this problem? Please let me know and thanks for the help.

During my initial trial and error of setting up these drivers,  I tried multiple versions of Ubuntu.  If memory serves me correct, I also received the Error 2 with mutex_lock errors.  These errors were only present using specific version of Ubuntu and didn't show up with 7.10.  I was able to work around these errors however, but it required editing the source code.

Using the post here as a reference:
[Reference Post]("http://www.linuxquestions.org/questions/linux-software-2/controller-compilation-problem-sata-1740-highpoint-550575/")

I commented out the lines referring to the mutex for the version of Ubuntu I was using and the compile would complete successfully and the module could be loaded.   I honestly have no idea of the implications of the change to the source, but it did seem to work.   One thing to note though is that I believe krischeu was using an older source version as the line numbers he modifies were different from the line numbers I modified.  Unforutunately that was a good long while ago and I've no recollection of exactly what I modified,  I just know I only commented or uncommented a half dozen lines of code or so.

---

### Post by Yfrwlf on 2008-03-06
Don't know if this has been recommended to you before, but have you tried using the alternate install CD and then telling it you wish to load additional drivers when it asks, and loading the compiled driver at that point?  If it works, it should install it when it installs your system.

---

### Post by Stant0n on 2008-03-06
When I first did this install, i tried both Kubuntu and Ubuntu Alternate CD's.  The problem is how do you load the compiled drivers during setup?  If you use a USB drive,  your install will assign sda to the USB drive and fudge your install.  You'd need to use a floppy drive... which I don't have (It is 2008 right?).  

Also, if I recall correctly, the alternate CD does the same thing the server install does, which is it uses the generic kernel during setup and installs the i386 kernel when finished.  So you load the driver compiled against generic headers during install and the reboot fails because it then needs the driver compiled against the i386 kernel.

---

### Post by Yfrwlf on 2008-03-07
Ugh...and this is one of the reasons why source-only compliance = fail.  An OS needs to have both source and binary compliance.  I'm not compiling every program I install, and there's no way in hell someone else can compile everything I'd ever want or need for the repository.

---

### Post by jake.burkholder on 2008-05-03
I followed the same steps with the driver version 2.1 and ubuntu 8.04, kernel 2.6.24-16-generic, and finally got it to work.  Before loading the rr174x.ko you need to unload the sata_mv module included with the kernel (sudo rmmod sata_mv).  I also deleted it from /lib/modules/2.6.24-16-generic/kernel/drivers/ata/sata_mv.ko before running make install, don't know if this is necessary.

The sata_mv module now recognizes the controller and tries to attach to it.  This conflicts with the proprietary driver, it will load but after a few seconds/minutes the driver will start to print reset messages and down one of the disks which sets off the raid alarm (as below).

[  489.691444] sd 12:0:0:0: [sda] Write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[  489.692253]  sda:rr174x:hpt_reset(12/0/0)
[  504.885597] rr174x:start channel [0,0]
[  505.012614] rr174x:channel [0,0] started successfully
[  506.384487] rr174x:start channel [0,0]
[  506.511512] rr174x:channel [0,0] started successfully
[  527.317703] rr174x:hpt_reset(12/0/0)
[  527.317722] rr174x:start channel [0,1]
[  527.444739] rr174x:channel [0,1] started successfully
[  528.816613] rr174x:start channel [0,1]
[  528.943638] rr174x:channel [0,1] started successfully
[  530.315509] rr174x:start channel [0,1]
[  530.442535] rr174x:channel [0,1] started successfully
[  531.814412] rr174x:start channel [0,1]
[  531.941433] rr174x:channel [0,1] started successfully
[  533.931648] rr174x:start channel [0,1]
[  534.058651] rr174x:channel [0,1] started successfully
[  535.430547] rr174x:[0 1 0] too many resets - make drive offline.
[  553.147734] rr174x:hpt_reset(12/0/0)
[  553.147762] rr174x:start channel [0,0]
[  553.376401] rr174x:channel [0,0] started successfully
etc
etc

---

### Post by hedefalk on 2008-06-15
[QUOTE=jake.burkholder;4871874]I followed the same steps with the driver version 2.1 and ubuntu 8.04, kernel 2.6.24-16-generic, and finally got it to work.  Before loading the rr174x.ko you need to unload the 

Thanks! This saved my day. The beeping was really killing me. ;)

---

