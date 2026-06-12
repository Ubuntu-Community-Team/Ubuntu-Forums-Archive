---
title: "Windows install killed access to Wubi Ubuntu"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by n1unqn on 2011-03-28
[SOLVED! SEE MY LAST POST]

Windows Vista had virus that killed network access.

I installed Ubuntu 10.04.1 on my D: hard disc partition with **Wubi** and copied my windows files across (they appear under HOST).

I did some work using Ubuntu for a few months.

Later I got around to reinstalling Windows Vista on C: drive.

Now I can no longer access Wubi Ubutu or my files saved to the desktop there.

Im scared of doing a reinstall incase it kills my Windows or Ubuntu files on D:

Please can someone explain to a simpleton how to fix the boot menu to get **Wubi Ubuntu** back running on from the NTFS second partition drive D:

Thanks in advance.

---

### Post by Megaptera on 2011-03-28
If your files are on 'D' then if you set the BIOS to boot from a live CD (Ubuntu perhaps) you should be able to access your 'D' drive and copy or cut&paste those docs, photos etc etc to external storage (portable hard drive, perhaps).
You can then set about reinstalling Windows and perhaps have a dual boot with Ubuntu - dual boot considered better long-term option than Wubi for the reason you've discovered.

Hope this helps?

---

### Post by n1unqn on 2011-03-28
Windows Vista is reinstalled, I can access all the files on D: (/HOSTS) except the files I left on the Ubuntu desktop. 

I assume these files are embeded in the 17Gb file Wubi creates on NTFS as the virtual Ubutu partition.

The problem is if I reinstall Wubi im scared it will replace the 17gb file and wipe those documents.

It was a dual boot just with Ubuntu running from NTFS, which I like as it makes working on files in both OS easy.

I need the knowledge on how to re-Grub Wubi I suspect.

Thanks for your help though.

---

### Post by Megaptera on 2011-03-28
If it was Wubi it wasn't a "dual-boot", Wubi installed Ubuntu _within_ Windows.
If you reinstalled Windows _I think_ that'll have wiped your original Wubi install and docs, photos etc within it.

Let's see if anyone else can help.

---

### Post by coffeecat on 2011-03-28
> **Megaptera said:**
> 
If you reinstalled Windows _I think_ that'll have wiped your original Wubi install and docs, photos etc within it.

I think the possible saving grace here is that the wubi virtual HD is on the Windows D: drive and Windows was re-installed to the C: partition. In which case the OP's documents and so on should still be in the virtual drive and potentially accessible.

> **n1unqn said:**
> I assume these files are embeded in the 17Gb file Wubi creates on NTFS as the virtual Ubutu partition.

I believe that is so. I think what happens with wubi is that a Linux filesystem is created within the 17GB file. If so, then it is a fairly easy thing to mount from an Ubuntu live CD. I'll look into this and post back as soon as I can.

---

### Post by n1unqn on 2011-03-28
On the D: drive is a folder called /UBUNTU and it has the 17gb file in it.

I'm in the process of making a backup copy of this folder

then I'm just gona try and reinstall Wubi

if it wipes the original files I suspect I can just copy back the 17gb file from the backup copy im making.

Let you know if it works soon :D

---

### Post by coffeecat on 2011-03-28
Did you see my earlier post, just before yours?

> **n1unqn said:**
> On the D: drive is a folder called /UBUNTU and it has the 17gb file in it.

I'm in the process of making a backup copy of this folder

then I'm just gona try and reinstall Wubi

if it wipes the original files I suspect I can just copy back the 17gb file from the backup copy im making.

It's a good idea to copy the /Ubuntu folder and contents. At least then you will be able to access your files from within the virtual partition from the backup if necessary. Where are you backing up to? An external USB drive would be a good idea.

I suggest not deleting the /Ubuntu folder on the D: drive. The wubi installer *may* detect that and offer to use it as well as the 17GB virtual partition file.

Here is the Ubuntu Wiki page on Wubi for your bookmarks:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

And here for mounting the virtual partition from the Ubuntu live CD:

[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?](https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?)

If you want to adapt that to mount the virtual partition from your backup copy of the 17GB file, then I can help you with that.

---

### Post by n1unqn on 2011-03-28
IT WORKS!

If you re-install windows after Wubi Ubuntu (on D: drive) and it kills the Grub menu all you have to do is this...

1) rename D:\Ubuntu to D:\Ubuntu_Old
2) install Wubi
3) delete D:\Ubuntu
4) rename D:\Ubuntu_Old to D:\Ubuntu

:lolflag:

Tip for anyone using Windows keep all you work files on drive D: and install a copy of Wubi Ubuntu there too so you can keep working when that day comes when Windows dies to virus.

---

### Post by Megaptera on 2011-03-28
Pleased to read you solved it!

---

### Post by n1unqn on 2011-03-28
By the way Megapetra,

> If it was Wubi it wasn't a "dual-boot", Wubi installed Ubuntu _within_ Windows.

Wubi installs from Windows and uses an NTFS partition but it is a dual boot, it's doesn't run inside Windows like a virtual machine.

---

### Post by Megaptera on 2011-03-28
Not a dual boot "It is not a virtual machine, but creates a stand-alone installation within a loopmounted device, also known as a disk image, like Topologilinux does. It is not a Linux distribution of its own, but rather an installer for Ubuntu.[1]
While Wubi does not install Ubuntu directly to its own partition this can also be accomplished by using LVPM, the Loopmounted Virtual Partition Manager, to transfer the Wubi-generated Ubuntu installation to a dedicated real partition, including a bootable USB keydrive.[1] The advantage of this setup is that users can test the operating system and install the drivers before they install it to a dedicated partition (and avoid booting and functioning risks).
**Wubi adds an entry to the Windows boot menu which allows the user to run Linux. Ubuntu is installed within a file in the Windows file system **(c:\ubuntu\disks\root.disk), **as opposed to being installed within its own partition**. This file is seen by Linux as a real hard disk.[1] Wubi also creates a swap file in the Windows file system (c:\ubuntu\disks\swap.disk), in addition to the memory of the host machine. This file is seen by Ubuntu as additional RAM.[1"
Wikipedia (above)

Sourceforge "Instead of creating new partitions, Wubi uses a method whereby the Linux files system is stored as a single Windows file." "Except for the file system, the Linux system is a real Linux installation, not an emulation."

Launchpad "Wubi is a Windows front-end for lupin ([http://launchpad.net/lupin](http://launchpad.net/lupin)) and ubiquity ([http://launchpad.net/ubiquity](http://launchpad.net/ubiquity)). Wubi and lupin provide a user friendly installer which allows to install/uninstall Ubuntu as any other program, without modifying partitions, without replacing the bootloader and without having to burn a CD. Ubuntu installation is _almost identical_ to a standard dual-boot installation both in terms of behaviour and performance." Note almost.

---

