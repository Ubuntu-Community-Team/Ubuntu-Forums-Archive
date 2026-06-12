---
title: "Quick fix for virtualbox 1.6.4 PUEL version and kernel 2.6.27"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dinxter on 2008-08-27
Quick fix for virtualbox 1.6.4 PUEL version and kernel 2.6.27, no guarantees provided :*)

(1) backup /usr/share/virtualbox/src/SUPDRV.h and /usr/share/virtualbox/src/linux/SUPDrv-linux.c 

(2) Edit /usr/share/virtualbox/src/SUPDRV.h (LINE 104) and remove the line containing "include <asm/semaphore.h>"

#   else /* older kernels */
#       include <asm/semaphore.h>
#   endif /* older kernels */
#   include <asm/semaphore.h>   // REMOVE THIS LINE
#   include <linux/timer.h>

(3) Edit /usr/share/virtualbox/src/linux/SUPDrv-linux.c (LINE 1331) and change

        smp_call_function(VBoxDrvLinuxGipResumePerCpu, pDevExt, 0 /*retry*/,  1 /* wait */);

to
        smp_call_function(VBoxDrvLinuxGipResumePerCpu, pDevExt,  1 /* wait */);

as retry option has been dropped in 2.6.27

(4) Run /etc/init.d/vboxdrv setup

[EDIT] Just to add, this fixes the compilation errors below from  /var/log/vbox-install.log

In file included from /tmp/vbox.2/linux/SUPDrv-linux.c:35:
/tmp/vbox.2/SUPDRV.h:104:30: error: asm/semaphore.h: No such file or directory
/tmp/vbox.2/linux/SUPDrv-linux.c: In function &#8216;supdrvOSGipResume&#8217;:
/tmp/vbox.2/linux/SUPDrv-linux.c:1331: error: too many arguments to function &#8216;smp_call_function&#8217;
make[2]: *** [/tmp/vbox.2/linux/SUPDrv-linux.o] Error 1

---

### Post by plun on 2008-08-27
Thanks !

Works just fine.

---

### Post by podulator on 2008-08-27
magic, thanks :)

---

### Post by chacham23 on 2008-08-28
thanks m8

---

### Post by vikrant82 on 2008-08-29
Works fine.

---

### Post by olskar on 2008-08-29
I don't understand what I am supposed to do to fix th compilation errors I get?

> /tmp/vbox.1/linux/SUPDrv-linux.c: I funktion "supdrvOSGipResume":
/tmp/vbox.1/linux/SUPDrv-linux.c:1331: fel: för få argument till funktionen "smp_call_function"
make[2]: *** [/tmp/vbox.1/linux/SUPDrv-linux.o] Fel 1
make[1]: *** [_module_/tmp/vbox.1] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.24-19-generic"
make: *** [vboxdrv] Fel 2


---

### Post by chronographer on 2008-08-30
Thanks aswell, its worked perfectly, I followed instructions here, just to create a nice circular reference! [http://forums.virtualbox.org/viewtopic.php?t=8997](http://forums.virtualbox.org/viewtopic.php?t=8997)

---

### Post by scottro on 2008-08-30
Just wanted to add my thanks as well.  This works, by the way, on Fedora Rawhide which is running 2.6.27-lots of other numbers.  (As Rawhide tends to update daily, it's almost a waste to put the particular version, but in this case 2.6.27-0.207.rc4.git7.fc10.x86_64).

---

### Post by plun on 2008-08-30
> **olskar said:**
> I don't understand what I am supposed to do to fix th compilation errors I get?

You don´t compile this one, just installs Suns version  (Ubuntu deb file)
and then using "dinxter´s" walk around.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

(Suns version includes a minimal portition of proprietary stuff for USB)

---

### Post by olskar on 2008-08-30
> **plun said:**
> You don´t compile this one, just installs Suns version  (Ubuntu deb file)
and then using "dinxter´s" walk around.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

(Suns version includes a minimal portition of proprietary stuff for USB)


But I have to recompile the kernel module with "/etc/init.d/vboxdrv setup", that is where it fails with the errormessage I wrote above

---

### Post by dinxter on 2008-08-30
i notice from your output /usr/src/linux-headers-2.6.24-19-generic, are you sure your on the 2.6.27 kernel? as you dont seem to be using the headers for that kernel.

as for which files to edit, they are shown in steps 2 and 3 in the first post. these files are from the .deb file for the PUEL version of virtualbox downloaded from sun and not the OSE version from the repositories which may or may not be diferent

The OSE files from the repository are in the file /usr/src/virtualbox-ose.tar.bz2 from the virtualbox-ose-source package in the repositories. you might manage to fix the compilation by editing the corresponding SUPR named files in that although i cannot say for sure

---

### Post by VoidedCheck on 2008-08-30
Thank you.  Worked like a charm.

---

### Post by TDFlanders on 2008-08-30
Hi there dinxter,

You rock baby. I don't know how you found out about this. I believe you probably compared the source code of the two kernels and ran a difference check on it? Don't try to explain really, I am an absolute UNIX illiterate without an IT background. Anyway, I just wanted to thank you for helping me out on this one. 

I must say though I did not manage to get sharing sorted out just yet. I followed these instructions: [https://help.ubuntu.com/community/VirtualBox?highlight=(VirtualBox)|(usb](https://help.ubuntu.com/community/VirtualBox?highlight=(VirtualBox)|(usb)). The vboxmanage program is not available, and it prompts me to use an older version of virtualbox-ose and virtualbox-ose-modules, but then I have to downgrade to 1.6.2. So I tried to install linux-backports-modules-2.6.27-1-generic, but unfortunately that one isn't loaded into apt just yet (see bug 262509). I upgraded further to 1.6.27-2 and was prompted to restart, but I failed to establish a first boot (see bug 263036). So I don't know yet how to solve this one.

Thanks anyway,

Thomas

*****

Notes:

Bug 263036

thomas@thomas-desktop:~$ lsb_release -rd ; uname -a ; apt-cache policy dpkg dkms xorg-driver-fglrx fglrx-kernel-source xinit xserver-xorg apt synaptic ; sudo dpkg-reconfigure linux-image-2.6.27-2-generic
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Linux thomas-desktop 2.6.27-1-generic #1 SMP Sat Aug 23 23:20:09 UTC 2008 i686 GNU/Linux
dpkg:
  Installed: 1.14.20ubuntu5
  Candidate: 1.14.20ubuntu5
  Version table:
 *** 1.14.20ubuntu5 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
dkms:
  Installed: 2.0.20.4-0ubuntu1
  Candidate: 2.0.20.4-0ubuntu1
  Version table:
 *** 2.0.20.4-0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
xorg-driver-fglrx:
  Installed: 2:8.522-0ubuntu3
  Candidate: 2:8.522-0ubuntu3
  Version table:
 *** 2:8.522-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
        100 /var/lib/dpkg/status
     1:7.1.0-8-3+2.6.24.14-21.47 0
        500 cdrom://[APTonCD for ubuntu hardy - i386 (2008-08-17 02:58) DVD1]  Packages
fglrx-kernel-source:
  Installed: 2:8.522-0ubuntu3
  Candidate: 2:8.522-0ubuntu3
  Version table:
 *** 2:8.522-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages
        100 /var/lib/dpkg/status
xinit:
  Installed: 1.0.9-2
  Candidate: 1.0.9-2
  Version table:
 *** 1.0.9-2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
xserver-xorg:
  Installed: 1:7.4~1ubuntu1
  Candidate: 1:7.4~1ubuntu1
  Version table:
 *** 1:7.4~1ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
apt:
  Installed: 0.7.14ubuntu6
  Candidate: 0.7.14ubuntu6
  Version table:
 *** 0.7.14ubuntu6 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
synaptic:
  Installed: 0.62.1ubuntu8
  Candidate: 0.62.1ubuntu8
  Version table:
 *** 0.62.1ubuntu8 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-2-generic
cp: cannot stat `/lib/udev/hotplug.functions': No such file or directory
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-2.3 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-2.3 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-2-generic
Found kernel: /boot/last-good-boot/vmlinuz
Found kernel: /boot/vmlinuz-2.6.27-1-generic
Found kernel: /boot/vmlinuz-2.6.26-5-generic
Found kernel: /boot/vmlinuz-2.6.26-4-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-20-virtual
Found kernel: /boot/vmlinuz-2.6.24-20-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-2-generic           
 *  fglrx (8.522)...                                                            fglrx (8.522): Installing module.
.......(bad exit status: 7)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxdrv (1.6.4)...                                                          vboxdrv (1.6.4): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
thomas@thomas-desktop:~$ 

Hi there, I have been upgrading and stuff and at a certain point I was prompted to install 2.6.27-2. Being a bit of a fruitcake and a happy testing donkey with virtually no ICT skills, I rarely refuse on any an upgrade. Anyway: 2.6.27-1 was behaving rather stable and was rebootable. Now I have the 2.6.27-2 installed, it is not really unstable, but it refuses to boot somehow. I really don't know why. I could not get virtualbox 1.6.4 sharing capability, after following this set of instructions: [http://ubuntuforums.org/showthread.php?p=5693268#post5693268](http://ubuntuforums.org/showthread.php?p=5693268#post5693268). Therefore I started toying with upgrading, build-dep, also through backports.org and apt-get -t etch-backports and manually selecting some synaptic packages, including restricted-modules. So now I have the 2.6.27-2 kernel but it won't install properly. If I try sudo dpkg-reconfigure linux-headers-2.6.27-2-generic linux-image-2.6.27-2- generic, I get the following output. Afte a while I get the restart prompt in the upper right panel, but the new kernel won't boot. The 2.6.27-1 does not boot anymore either. I have to use the alfa 3 live CD image and select all options under F6 and the 'with driver update CD' option under F4 to boot the recovery version of 2.6.27-1 and run xfix and dpkg repair broken packages. The first time I had this problem, there was one package selected to be removed: gnome-cups-manager. File system check did not reveal any problems. dpkg repair broken packages I doubt that I will have any more luck as root, I tried that, even dpkg-reconfigure -a, but I can't find the problem. Are there any log files I could consult? I mind you that I am not a UNIX literate. I have cups-spooler configured as foo, could that be it? Anyway, the cycle repeats: I boot up with 2.6.27-1, reconfigure, get restart prompt, and the system fails to reboot.

normal boot of 2.6.27-2 hangs at first line: starting up
recovery mode hangs at: running virtualization kernel, bottom of first screen.

*****

Bug 262509

Binary package hint: synaptic

Linux backports won't install through synaptic.

thomas@thomas-desktop:~$ lsb_release -rd; uname -a
Description: Ubuntu intrepid (development branch)
Release: 8.10
Linux thomas-desktop 2.6.27-1-generic #1 SMP Sat Aug 23 23:20:09 UTC 2008 i686 GNU/Linux
thomas@thomas-desktop:~$

*****

reboot does not work

---

### Post by FishRCynic on 2008-09-01
thanks 
this worked for me

ibex i686
all updated as of today

---

### Post by scottro on 2008-09-02
They came out with 1.6.6.  I don't know if it will fix the issues or not, won't be able to try till tonight.

---

### Post by dinxter on 2008-09-02
fixes for new kernels have been added. also, thankfully,  virtualbox repositories are back at,

deb [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) hardy non-free

with the key, 

wget -k  [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O-|sudo apt-key add -

---

### Post by plun on 2008-09-05
Version 2.0 is also out.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Changelog:

> VirtualBox 2.0.0 (released 2008-09-04)
[B]
This version is a major update.[/B] The following major new features were added:

    * 64 bits guest support (64 bits host only)
    * New native Leopard user interface on Mac OS X hosts
    * The GUI was converted from Qt3 to Qt4 with many visual improvements
    * New-version notifier
    * Guest property information interface
    * Host Interface Networking on Mac OS X hosts
    * New Host Interface Networking on Solaris hosts
    * Support for Nested Paging on modern AMD CPUs (major performance gain)
    * Framework for collecting performance and resource usage data (metrics)
    * Added SATA asynchronous IO (NCQ: Native Command Queuing) when accessing raw disks/partitions (major performance gain)
    * Clipboard integration for OS/2 Guests
    * Created separate SDK component featuring a new Python programming interface on Linux and Solaris hosts
    * Support for VHD disk images 

In addition, the following items were fixed and/or added:

    * VMM: VT-x fixes
    * AHCI/SATA: improved performance
    * GUI: keyboard fixes
    * Linux installer: properly uninstall the package even if unregistering the DKMS module fails
    * Linux additions: the guest screen resolution is properly restored
    * Network: added support for jumbo frames (> 1536 bytes)
    * Shared Folders: fixed guest crash with Windows Media Player 11
    * Mac OS X: Ctrl+Left mouse click doesn&#8217;t simulate a right mouse click in the guest anymore. Use Hostkey+Left for a right mouse click emulation. (bug #1766) 

---

### Post by TDFlanders on 2008-09-05
VirtualBox 2.0 has come out as well as alfa 5 supposedly but the links are dead. No bad news I hope? Anyway VBox 2.0 doesn't work properly yet and I am still working on it. The problem is that after installing 2.0 (first attempt), NetWorkManager 0.7.0 would not recognize my wireless card anymore. I did $ sudo dpkg-reconfigure -a, which gave: see attachments.

A NVIDIA wireless card warning was issued, maybe because I tried to upgrade in the terminal with:

thomas@thomas-laptop:~$ sudo apt-get -y update ; sudo apt-get -y upgrade ; sudo apt-get -y dist-upgrade ; sudo apt-get install -fy ; sudo dpkg --configure -a ; sudo apt-get -t etch-backports -y update ; sudo apt-get -t etch-backports -y upgrade ; sudo apt-get -t etch-backports -y dist-upgrade ; sudo apt-get -t etch-backports install -fy ; sudo dpkg --configure -a 

After which I was prompted to reboot. Still no connection plus kernel stayed the same, that means no alfa 5 I guess.

thomas@thomas-laptop:~$ lsb_release -rd ; uname -a ; apt-cache policy linux-headers-generic linux-image-generic linux linux-source-2.6.27 linux-restricted-modules virtualbox network-manager
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Linux thomas-laptop 2.6.27-2-generic #1 SMP Thu Aug 28 17:20:02 UTC 2008 i686 GNU/Linux
linux-headers-generic:
  Installed: 2.6.27.2.2
  Candidate: 2.6.27.2.2
  Version table:
 *** 2.6.27.2.2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
linux-image-generic:
  Installed: 2.6.27.2.2
  Candidate: 2.6.27.2.2
  Version table:
 *** 2.6.27.2.2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
linux:
  Installed: 2.6.27.2.2
  Candidate: 2.6.27.2.2
  Version table:
 *** 2.6.27.2.2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
        100 /var/lib/dpkg/status
linux-source-2.6.27:
  Installed: 2.6.27-2.3
  Candidate: 2.6.27-2.3
  Version table:
 *** 2.6.27-2.3 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
linux-restricted-modules:
  Installed: 2.6.27.2.2
  Candidate: 2.6.27.2.2
  Version table:
 *** 2.6.27.2.2 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages
        100 /var/lib/dpkg/status
virtualbox:
  Installed: (none)
  Candidate: 1.6.6-35336_Ubuntu_hardy
  Version table:
     1.6.6-35336_Ubuntu_hardy 0
        500 [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Packages
        100 /var/lib/dpkg/status
network-manager:
  Installed: 0.7~~svn20080818t061112+eni0-0ubuntu1
  Candidate: 0.7~~svn20080818t061112+eni0-0ubuntu1
  Version table:
 *** 0.7~~svn20080818t061112+eni0-0ubuntu1 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
thomas@thomas-laptop:~$ 

Any Ideas?

[ATTACH]84140[/ATTACH]

[ATTACH]84141[/ATTACH]

[ATTACH]84150[/ATTACH]

[ATTACH]84151[/ATTACH]

[ATTACH]84152[/ATTACH]

[ATTACH]84153[/ATTACH]

[ATTACH]84154[/ATTACH]

---

### Post by TDFlanders on 2008-09-05
Oops,

so screenshot 1, 2 and 8:

[ATTACH]84155[/ATTACH]

[ATTACH]84156[/ATTACH]

[ATTACH]84157[/ATTACH]

---

### Post by gjoellee on 2008-09-05
For me virtual box 2.0 works great to:)

---

### Post by run1206 on 2008-10-09
sorry for editing the whole text, but i was able to get Virtualbox 2.0.2 (PUEL version) to not only work on Intrepid Ibex, but with searching around, i was able to read and write to USB devices from within my "virtual" XP Home.  

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)
(i know TDFlanders posted this link up before, but that link didn't work for me :( )

you have to make a group and give them read and write permissions to /proc/bus/usb

also, you have to make changes to mount /proc/bus/usb as well, which is shown in the link as well. 

finally, with VirtualBox running, make sure you "filter" your USB device in the Settings -> USB tab. After booting windows, i'm able to read and write to my Flash Drive.

hope this helps those using VirtualBox :)

---

