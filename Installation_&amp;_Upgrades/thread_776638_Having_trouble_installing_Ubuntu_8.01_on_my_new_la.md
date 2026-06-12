---
title: "Having trouble installing Ubuntu 8.01 on my new laptop"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by JDean on 2008-04-30
Hey all, thanks for the help.  I'm a pretty competent Windows user, but just got a new laptop and wanted to set up a dual-boot w/ Vista and Ubuntu 8.01 but am running into difficulty.

Laptop type is a Toshiba A305-s6825, with a 250GB HDD, an Intel Core2 Duo 1.83GHz processor, and 3GB of RAM.  I wiped the initial HDD and repartitioned it with 200 to Vista and 50 for Ubuntu, then reloaded the Vista Home Premium.

I've downloaded, burned, checked, and re-checked the ISO files for 8.04 desktopi386 and amd64 (chip can run 64-bit but the installation isn't, but I figured it should be the 64 bit?) and the alternate install options for both.  None have worked and all return the same error message:

udevd-event[1360]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    0.000000] usb 3-2: device not accepting address 3, error -110
[    0.000000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[    0.000000] usb 3-2: device not accepting address 4, error -110
[    0.000000] usb 3-2: new high speed USB dvice using ehci+hcd and address 5
[    0.000000] usb 3-2: device not accepting address 5, error -110"

This happens when I try to install, run without installing, or verify CD on any of the aforementioned installation discs.  I've tried booting in with special parameters "acpi=off" and "irqpoll" because I found that suggestion for getting around a similar problem, but that still kicks back the same error message.  And...now I'm stuck.  Any help or direction would be GREATLY appreciated, thanks :)

---

### Post by garyedwardjohnston on 2008-04-30
> **JDean said:**
> Hey all, thanks for the help.  I'm a pretty competent Windows user, but just got a new laptop and wanted to set up a dual-boot w/ Vista and Ubuntu 8.01 but am running into difficulty.

[COLOR="Red"]WHY NOT USE WUBI OR VIRTUALBOX?[/COLOR]

Laptop type is a Toshiba A305-s6825, with a 250GB HDD, an Intel Core2 Duo 1.83GHz processor, and 3GB of RAM.  I wiped the initial HDD and repartitioned it with 200 to Vista and 50 for Ubuntu, then reloaded the Vista Home Premium.

I've downloaded, burned, checked, and re-checked the ISO files for 8.04 desktopi386 and amd64 (chip can run 64-bit but the installation isn't, but I figured it should be the 64 bit?) and the alternate install options for both.  None have worked and all return the same error message:
[COLOR="Red"]
FORGET ALTERNATE INSTALL AND USE 32BIT[/COLOR]

udevd-event[1360]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [    0.000000] usb 3-2: device not accepting address 3, error -110
[    0.000000] usb 3-2: new high speed USB device using ehci_hcd and address 4
[    0.000000] usb 3-2: device not accepting address 4, error -110
[    0.000000] usb 3-2: new high speed USB dvice using ehci+hcd and address 5
[    0.000000] usb 3-2: device not accepting address 5, error -110"
[COLOR="Red"]
DISABLE HI-SPEED USB 2.0 IN BIOS
[/COLOR]
This happens when I try to install, run without installing, or verify CD on any of the aforementioned installation discs.  I've tried booting in with special parameters "acpi=off" and "irqpoll" because I found that suggestion for getting around a similar problem, but that still kicks back the same error message.  And...now I'm stuck.  Any help or direction would be GREATLY appreciated, thanks :)

good luck

---

### Post by JDean on 2008-05-01
So I went ahead and used the WUBI installer instead, which ran through and seemed to be installed fine.  Lets me choose Ubuntu or Vista on boot, but now different errors are popping with the same abnormal exit:

32.241808 SGE XFS with ACLs, security attributes, real time, large block / inode numbers, no debug enabled
32.242249 SGI XFS Quota Management subsystem
32.247074 JFS: nTxBlock = 8192, nTxLock = 65536

Now I can't seem to get past these...

---

### Post by DHGE on 2008-05-01
Get 8.04 ;)

You *could* have found a (n old) bug in the installer: XFS on /boot is not supported (without some heavy lifting). Still there??

OR (would not do this if you are new to Linux): You could check the file-system from a live-CD
[PHP]man xfs_check[/PHP]
and *try* to correct errors.

OR (bitter but easy):
Reinstall with the default ext3 filesystem for Ubuntu

---

### Post by RogerDaryl on 2008-05-01
> **JDean said:**
> So I went ahead and used the WUBI installer instead, which ran through and seemed to be installed fine.  Lets me choose Ubuntu or Vista on boot, but now different errors are popping with the same abnormal exit:

32.241808 SGE XFS with ACLs, security attributes, real time, large block / inode numbers, no debug enabled
32.242249 SGI XFS Quota Management subsystem
32.247074 JFS: nTxBlock = 8192, nTxLock = 65536

Now I can't seem to get past these...

I'm getting the same error on an HP laptop. sometimes it does show one more line of code after that. The next line is dealing with firewire.

---

### Post by JDean on 2008-05-01
Heh, typo on my end, I am using 8.04, not 8.01...

anyway, I burned another disc and double-checked it on a desktop PC (passed the verify disc option just fine and booted as a Live-CD there) but once again, running that disk on the laptop just kicks back those USB errors.  I've tried some different advanced boot options (like mentioned earlier) but still..no dice.

Soo...I'm still messing with it but having little luck.  Any other suggestions?

---

### Post by egor08 on 2008-05-19
I am having exactly the same problem. Please let me know if you will find a way to fix it.
Thanks.

---

### Post by Jimbob78 on 2008-05-20
I'm getting almost exactly the same issue. I have a live CD that works on my apple machine, and on my work laptop, but fails to run on the machine I actually want to install on.


Toshiba Satellite
64bit AMD Athlon x2
2gb


I get the following:


udevd-event[1533]: run_program: 'sbin/modprobe' abnormal exit
[219.659653] SGI XFS with ACLs, security attriubutes, realtime, large block.inode numbers, no debug enabled
[219.660121] SGI XFS Quota Management subsystem
[219.660121] JFS: nTxBlock = 8192, nTxLock = 65536

I've tried both the 64bit and 32bit Live CDs... same result with both, and as I mentioned before, they work fine on other machines...

J

---

### Post by Jimbob78 on 2008-05-20
I can confirm that this happens with 7.10 as well. I've tried the fix for "RTL8102E Lan Chip is enabled" (ie disabling the LAN). but still no joy...

Anyone else having these issues with a Toshiba?

J

---

### Post by Jimbob78 on 2008-05-23
Ok, disabling my built in LAN via the BIOS does actually work, and I can now successfully boot the live CD. Bad news is my wireless card is not showing up.

I've seen some threads mentioning a way of downlaoding and installing the windows driver for the card... but this will be tricky with the LAN diabled...

Can anyone offer any advice?

Cheers

J

---

