---
title: "Cloning xubuntu ..."
date: 2021-04-21
forum: Installation &amp; Upgrades
---

### Post by dbee on 2021-04-21
I want to clone xubuntu from an old desktop with 32 GB hd. Onto a ThinkPad with 250GB.

I also have a microsd card that i'd prefer to transfer.

can't seem to install tuxboot though...
> 
dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ sudo apt install tux*.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 tuxboot:i386 : Depends: libc6:i386 (>= 2.3.6-6~) but it is not installed
                Depends: libgcc1:i386 (>= 1:4.1.1) but it is not installed
                Depends: libqt4-network:i386 (>= 4:4.5.3) but it is not installed
                Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not installed
                Depends: libqtgui4:i386 (>= 4:4.5.3) but it is not installed
                Depends: libstdc++6:i386 (>= 4.1.1) but it is not installed
                Depends: syslinux:i386 but it is not installed
                Depends: p7zip-full:i386 but it is not installed
                Depends: mtools:i386 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


So I run a fix broken install.

> 
dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  tuxboot:i386
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 1,141 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 222504 files and directories currently installed.)
Removing tuxboot:i386 (0.8debian1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for mime-support (3.60ubuntu1) ...


Tried installing the .deb for i386...

> 
dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ sudo dpkg -i tux*.deb
Selecting previously unselected package tuxboot:i386.
(Reading database ... 222497 files and directories currently installed.)
Preparing to unpack tuxboot_0.8debian1_i386.deb ...
Unpacking tuxboot:i386 (0.8debian1) ...
dpkg: dependency problems prevent configuration of tuxboot:i386:
 tuxboot:i386 depends on libc6 (>= 2.3.6-6~).
 tuxboot:i386 depends on libgcc1 (>= 1:4.1.1).
 tuxboot:i386 depends on libqt4-network (>= 4:4.5.3).
 tuxboot:i386 depends on libqtcore4 (>= 4:4.7.0~beta1).
 tuxboot:i386 depends on libqtgui4 (>= 4:4.5.3).
 tuxboot:i386 depends on libstdc++6 (>= 4.1.1).
 tuxboot:i386 depends on syslinux.
 tuxboot:i386 depends on p7zip-full.
 tuxboot:i386 depends on mtools.

dpkg: error processing package tuxboot:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Errors were encountered while processing:
 tuxboot:i386


My system ..

> 
dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 4.15.0-141-generic #145-Ubuntu SMP Wed Mar 24 18:08:07 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux


I've done a full upgrade, tried to install from *apt cache*, *PPA*, and *dpkg -i* but I'm getting unmet dependencies.

Does anyone know a simple way of cloning a harddrive?

---

### Post by TheFu on 2021-04-21
> **dbee said:**
> Does anyone know a simple way of cloning a harddrive?

Yes.
```
sudo cp {source-device} {target-device}
```

Just be correct in picking the source and target devices. Get those backwards and it will be a very bad day/week/month/year.

If you want to clone just 1 partition, pick the partition device FOR BOTH the source and target.  That means you must pre-create the partition on the target first.

If you want to close the entire disk, including boot sector, partition table, everything .... pick the whole drive device for FOR BOTH the source and target.  The target must be at least the same size as the source, but shouldn't be over 2GB in size unless GPT is used.

If you don't know what a partition device or what a whole disk device is, go and learn about those. If you search these forums for ddrescue, dd, and cp, I bet someone has attempted to explain it a few times.

If the source is failing, **cp** will fail too. You'll probably want to use those file backups and start with a fresh install. Lacking that, check into **ddrescue** and hope the failing parts of the disk aren't important.

---

### Post by oldfred on 2021-04-21
Is old install 32 bit?
Is Thinkpad 64 bit?
 Just about everything in last 15 years is 64 bit, even if it had 32 bit Windows.

May be time to convert to 64 bit install, but then it is a total new install.
You can export list of installed apps, /home and maybe some other folders, but all those should be in your normal backup, anyway.

---

### Post by tea for one on 2021-04-21
> **dbee said:**
> can't seem to install tuxboot though

Are you trying to install [COLOR="#0000FF"]tuxboot[/COLOR] to make a bootable Clonezilla drive?

If so, please try [https://unetbootin.github.io/](https://unetbootin.github.io/)

---

### Post by dbee on 2021-05-05
> **tea for one said:**
> Are you trying to install [COLOR="#0000FF"]tuxboot[/COLOR] to make a bootable Clonezilla drive?

If so, please try [https://unetbootin.github.io/](https://unetbootin.github.io/)

I don't want to create a bootable live USB.

I want to clone my ubuntu OS.

---

### Post by TheFu on 2021-05-05
> **dbee said:**
> I don't want to create a bootable live USB.

I want to clone my ubuntu OS.

See post#2.

---

### Post by guiverc on 2021-05-05
Be aware the packages show you're using a EOL release of Xubuntu..

*Flavors* of Ubuntu only come with three years of supported life (*five years applies to Ubuntu Desktop, Ubuntu Server but not flavors*), so you're asking about a release that only days ago reached it's EOL.

If you check out  [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)

you'll note other *flavors* put out EOL notices (ie. Lubuntu/Ubuntu-MATE/Kubuntu/Ubuntu-Budgie)

Xubuntu didn't, but if you refer [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) you'll see that **29 April 2021** was the *end of life* for Xubuntu 18.04 LTS.

---

### Post by tea for one on 2021-05-05
> **dbee said:**
> I don't want to create a bootable live USB.

I want to clone my ubuntu OS.

My reply no. 4 mentioned [COLOR="#0000FF"]bootable Clonezilla drive[/COLOR] not [COLOR="#FF0000"]bootable live USB[/COLOR].

I suspect that you are not familiar with Clonezilla (the clue is in the name of the software).

[https://clonezilla.org/](https://clonezilla.org/)

---

### Post by dbee on 2021-05-06
Thanks. I'm not familiar with clonezilla. You are correct.

So I've created a bootable clonezilla live usb. Then I cloned my hp stream hd to my external hd.

Now I want to copy that image to my much larger thinkpad running windows and I want to make the image bootable.

I figured I could do that using clonezilla. So I tried and failed. Windows is still on the machine and I can't find a copy of the hp-stream ubuntu image anywhere on the thinkpad machine.

damn. i hate windows.

---

### Post by dbee on 2021-05-06
> **tea for one said:**
> My reply no. 4 mentioned [COLOR="#0000FF"]bootable Clonezilla drive[/COLOR] not [COLOR="#FF0000"]bootable live USB[/COLOR].

I suspect that you are not familiar with Clonezilla (the clue is in the name of the software).

[https://clonezilla.org/](https://clonezilla.org/)

so how do I go about copying my ubuntu image from my hp-stream to my larger Thinkpad machine running windows. I don't want a dual-boot.

Thanks tea for one. (pls see above post for more details)

---

### Post by TheFu on 2021-05-06
> **dbee said:**
> so how do I go about copying my ubuntu image from my hp-stream to my larger Thinkpad machine running windows. I don't want a dual-boot.

Thanks tea for one. (pls see above post for more details)

Post the output from the running system for 
```
df -Th
```
Then we can provide the 'cp' command. I would show how to figure this stuff out, but my systems use advanced LVM storage so the 'cp' isn't the way to accomplish this.  It is all about picking the correct device files to copy, then likely need to modify the fstab and grub if each partition has to be copied and not the entire HDD.

If you have to go through an intermediate file first, you can use **fsarchiver** to copy each partition.  fsarchiver supports restoring to smaller partitions than the original source, provided the data will still fit.  None of the other "imaging" tools can do that to my knowledge.

While doing all this stuff, an alternative booting OS will be necessary. We cannot safely copy a running OS or target a running OS.

BTW, always, always, mention dual boot and the other OS involved, if you want to retain that. I don't think it is easily possible and I wouldn't know where to start to make it happen for Windows.

A fresh install takes 15 minutes, even on slow machines.  Then you could have copied everything from /home over and created a list of installed packages and fed those into the new system via a trivial batch process and been done with this in about 30 minutes total time. Just something to consider rather than a bit-for-bit copy.  In general, disk imaging is a poor method for backup/restore processes, though for mirroring bit-for-bit exactly the same sized HDDs, it is 1 easy command.

Because I use LVM, moving an entire PV (roughly an entire partition) from 1 physical device to another is 1 command - **pvmove**. This can be run while the system is still being used.  Just something to consider when the installer offers LVM as an option on the storage page. It does add complexity for some day-to-day stuff, but it also provides fantastic flexibility when downtime has to be minimized for a system.  Extending a file system across multiple disks is possible with LVM (for some risks), but if you have excellent backups, go for it.

Just providing more information, for future considerations.

---

### Post by tea for one on 2021-05-06
Clonezilla will do want you want to do i.e. transfer your HP Stream OS to your Thinkpad.
However, with Clonezilla you have to be aware of the nomenclature of the drives in each PC.

Your HP Stream is probably [COLOR="#0000FF"]/dev/mmcblk0[/COLOR] and your Thinkpad is possibly [COLOR="#0000FF"]sda[/COLOR].

Clonezilla will not automatically allow an image with mmcblk0 to be restored to sda without converting the image.
If you can supply the exact details of each drive, then I can give you the terminal command to run in a Clonezilla session.
It is not intuitive but it can be done.

However, a slightly easier approach (without converting the nomenclature of the image) could be:-

HP Stream via USB Stick to Thinkpad

Start Clonezilla on your HP Stream
Plug in a USB stick with a larger capacity than your HP Stream and a smaller capacity than your Thinkpad (say 64GB)
Choose device to device using disks in the Clonezilla menu (Source = HP Stream & Target = USB stick)
Clone the complete mmcblk0 disk to the USB device

Plug both the USB disk and the Clonezilla drive into your Thinkpad
Start Clonezilla and use device to device using disks (Source = USB stick & Target = Thinkpad)

---

### Post by dbee on 2021-05-06
Restoring from a clonezilla image...

[https://youtu.be/eVOihefKE7w](https://youtu.be/eVOihefKE7w)

---

### Post by TheFu on 2021-05-06
When device names change, cloning means both grub and the fstab and perhaps some other disk mounting settings will need to be updated manually. Only the OP knows his skill level for these things.

Changing from mmcblk0 --> sda will definitely require manual intervention.  

If the understanding is off a little, the cloned drive will not boot and for many end-users, a fresh install will be needed to the new storage anyways.  Boot-repair (a tool to correct these sorts of things) doesn't touch fstab entries and has difficulty with most UEFI boot situations.

This thread has been open for 2 weeks. A 15 minute install and selective data transfers from the old system would have taken perhaps a few hours.

Cloning storage isn't foolproof, unfortunately.

---

### Post by dbee on 2021-05-09
> **guiverc said:**
> Be aware the packages show you're using a EOL release of Xubuntu..

*Flavors* of Ubuntu only come with three years of supported life (*five years applies to Ubuntu Desktop, Ubuntu Server but not flavors*), so you're asking about a release that only days ago reached it's EOL.

If you check out  [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582)

you'll note other *flavors* put out EOL notices (ie. Lubuntu/Ubuntu-MATE/Kubuntu/Ubuntu-Budgie)

Xubuntu didn't, but if you refer [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) you'll see that **29 April 2021** was the *end of life* for Xubuntu 18.04 LTS.

Thanks. I'll upgrade.

---

