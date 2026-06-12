---
title: "Unable to restore GRUB via boot-repair-disk"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by android.amonra on 2014-11-12
My laptop was running a working dual-boot Windows 7 / Ubuntu 14.04 combination (using GRUB).
After a forced installation (IT policy) of Microsoft bitlocker the laptop didn't boot anymore and only presented the GRUB rescue prompt...


I booted with a Windows 7 CD and repaired the MBR ("bootrec /fixboot" and "bootrec /fixmbr) so Windows 7 would boot back again.
Now that the laptop was booting Windows 7 again I wanted to repair GRUB so I could access my Ubuntu installation again. Here is where the issues started.

I created a boot-repair USB disk, but unfortunately it doesn't seem to be able to repair my GRUB menu.
When I press the "recommended repair" no GRUB menu is installed, and the laptop just boots into Windows 7.
When I check the advanced options both GRUB location and GRUB options are greyed out.

I pasted the Boot-repair extra info : [http://paste.ubuntu.com/8969210/](http://paste.ubuntu.com/8969210/)

I "think" that my old Linux partition was sda2, however boot-repair displays it as being an ntfs partition instead of a Linux partition?
Might this be the issue why boot-repair can't repair it? Did bitlocker make these changes?

Any input/help is welcome....

UPDATE : 

I was able to restore the Linux partition using Testdisk :

[COLOR=#000000]Testdisk Instructions[/COLOR]
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by grahammechanical on 2014-11-12
First of all Boot Repair cannot repair if we do not give it permission to repair.

> [COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would restore the [COLOR=#666666][([/COLOR]generic mbr[COLOR=#666666])][/COLOR] MBR in sda, and make it boot on sda2.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

[COLOR=#666666]===================[/COLOR] Settings chosen by the user
Boot-Info
This setting will not act on the MBR.


No change has been performed on your computer.

Second, there is this comment
> 1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.


Ubuntu does not exist on that hard disk anymore. Windows is using sda1 and sda2. The Linux swap partition is sda5 which is in sda3 (Extended partition). But no location for Ubuntu. Was this a Wubi install of Ubuntu inside of Windows?

Sorry

---

### Post by android.amonra on 2014-11-12
The installation was a normal Ubuntu installation, definitely not a wubi install (I don't have the rights to install anything under Windows without the required admin rights &#128521;).

I guess the Ubuntu location should have been in sda3 because it's the biggest in size.

Weird...

---

### Post by yancek on 2014-11-12
>  guess the Ubuntu location should have been in sda3 because it's the biggest in size.

No it would not because that is an Extended partition which is a container for logical partitions.  An Extended partition cannot hold data, a logical partition can.  All you have now in the Extended is the swap partition which is just a small part of the Extended partition.  There is a lot of space on which you could install Ubuntu but there is no sign of Ubuntu or any Linux partition in the output as indicated in the previous post.

---

### Post by oldfred on 2014-11-12
Windows does not correctly see Linux partitions. And some Windows repairs/updates rewrite partition table. It for whatever reason leaves extended partition and swap but just does not include the Linux partition.

You should be able to use testdisk to restore the missing partition.

But I thought bitlocker was one of the tools that wrote its own MBR and you could not overwrite it? Or was that some other software?

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by android.amonra on 2014-11-15
Thanks!

Testdisk was able to restore my linux partition.

---

