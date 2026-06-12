---
title: "Windows installation &quot;killed&quot; my dual boot"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Terryracoon on 2010-09-17
I used to have ubuntu AND windows XP installed in dual boot (2 different partitions, obviously) with grub.... Recently, however, windows got a virus and died! I obviously reformatted the machine, and.... IT KILLED GRUB! I reinstalled windows, all fine, but now it just goes straight into windows! Ubuntu is still there, in a partition windows can't find... Is there anyway to recover it? I don't wanna lose ubuntu! I REALLY don't
(P.S. the version is Ubuntu 9.10)

---

### Post by wilee-nilee on 2010-09-18
You have 9.10 but run this command to confirm your grub version should be 1.97 or so. You will need a live cd for all of this.
```
sudo grub-install -v
```

If it is grub2 follow this link or post
```
sudo fdisk -l
```
and I will give you the commands.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

So if it is grub2 you need a karmic or beyond cd to reload grub to the mbr with the commands.

---

### Post by phillipdhall on 2010-09-18
Is there a chance Ubuntu installed grub to the partition and he could use EasyBCD from his Windows installation to tell the Windows bootloader to call his Ubuntu installation? Or does grub always default to the MBR?
 
I ask this more from my own desire to undertand the way grub likes to work...
 
Phil

---

### Post by wilee-nilee on 2010-09-18
> **phillipdhall said:**
> Is there a chance Ubuntu installed grub to the partition and he could use EasyBCD from his Windows installation to tell the Windows bootloader to call his Ubuntu installation? Or does grub always default to the MBR?
 
I ask this more from my own desire to undertand the way grub likes to work...
 
Phil

XP was installed last; its boot loader is in the MBR. They just need to reload grub back to the mbr. At least if I am correct in reading the post.

---

### Post by Terryracoon on 2010-09-18
Yup XP was reinstalled, thus it was installed last!
Grub is 1.97....
Now how do i get it back up and running?

---

### Post by Dragynn on 2010-09-18
Ouch. Always install Winders first bubba. Stay off interwebs with Winders and ya won't get virused.

Edit the windows MBR manually and you should be able to get to the linux party, but i would seriously consider re-doing the whole thing and loading windows first.

---

### Post by coffeecat on 2010-09-18
> **Dragynn said:**
> but i would seriously consider re-doing the whole thing and loading windows first.

This is completely and utterly unnecessary and is misleading advice.

@Terryracoon, post the output of:

```
sudo fdisk -l
```that wilee-nilee asked you for. Then someone can tell you the (easy) steps to reinstall grub2 to the mbr and get you dual-booting again.

---

### Post by wilee-nilee on 2010-09-18
> **coffeecat said:**
> This is completely and utterly unnecessary and is misleading advice.

@Terryracoon, post the output of:

```
sudo fdisk -l
```that wilee-nilee asked you for. Then someone can tell you the (easy) steps to reinstall grub2 to the mbr and get you dual-booting again.

Yah yah post the output from this command.

---

### Post by Terryracoon on 2010-09-18
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd33bd33b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4980    40001818+   7  HPFS/NTFS
/dev/sda2            4981        9729    38146342+   5  Extended
/dev/sda5            4981        5229     2000061   82  Linux swap / Solaris
/dev/sda6            5230        9729    36146218+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40f84c0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 1999 MB, 1999568384 bytes
32 heads, 63 sectors/track, 1937 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x4ab404ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1937     1952464+   6  FAT16

```
Here....

---

### Post by wilee-nilee on 2010-09-18
So from the booted cd of karmic or beyond run these commands.
```
sudo mount /dev/sda6 /mnt
```
Then
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
Reboot and the grub loader should show, go to Ubuntu and run.
```
sudo update-grub
```

So these commands are from this link and the link defaults to that part of the page.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Terryracoon on 2010-09-18
[s]YES! It's back! Thank you man! Saved me a reinstallation[/s]
Now it won't boot windows! o.o
It goes into grub, and boots ubuntu, just fine!
But if i select windows it says
"invalid device (insert numbers here)"
and sends me back to the menu

---

### Post by wilee-nilee on 2010-09-18
> **Terryracoon said:**
> [s]YES! It's back! Thank you man! Saved me a reinstallation[/s]
Now it won't boot windows! o.o
It goes into grub, and boots ubuntu, just fine!
But if i select windows it says
"invalid device (insert numbers here)"
and sends me back to the menu

Thats not good is it, I wonder if there is a problem in XP that might show from a flag on the partition in gparted. If you don't have gparted installed in Ubuntu run.
```
sudo apt-get install gparted
```

Then open gparted and look for any flags if there is one right click on the partition flagged and then information and post it in a screen shot or in text. While your in gparted also take a screen shot of it and post that as well. Be careful with gparted we don't want to run anything just look at it and check for flags on the XP or any partition.

Also we generally use the bootscript in my signature to get to the root so to speak of things, it might help if there are no flags seen in gparted. Post it in code tags as described in my sig, i you can it makes it easier to read.

Did you run the sudo update-grub command?

---

### Post by Terryracoon on 2010-09-18
Ok.... I used GParted... It says it can't read the partition windows is on....
And... By flags you mean things like if it's the boot partition or something? If such then "boot" is the only flag!

---

### Post by wilee-nilee on 2010-09-18
> **Terryracoon said:**
> Ok.... I used GParted... It says it can't read the partition windows is on....
And... By flags you mean things like if it's the boot partition or something? If such then "boot" is the only flag!

No we are looking for a yellow caution like triangle on the far left under the partition header, take a screen shot of gparted. I suspect you need to run a chkdsk, that is why I was hoping to get the right click on the partition-information. It may say you need to run a chkdsk.

A chkdsk can be run or set to run from the safe mode or a install cd.

Have you tried also as soon as you choose XP hitting the f8 key repeatedly to get to the safe mode.

---

### Post by Terryracoon on 2010-09-18
[http://img46.imageshack.us/img46/5746/scrw.png](http://img46.imageshack.us/img46/5746/scrw.png)
Here's the printscreen you asked for.... I'll reboot now and try chkdsk...

---

### Post by wilee-nilee on 2010-09-18
> **Terryracoon said:**
> [http://img46.imageshack.us/img46/5746/scrw.png](http://img46.imageshack.us/img46/5746/scrw.png)
Here's the printscreen you asked for.... I'll reboot now and try chkdsk...

I think after the chkdsk you will be okay run chkdsk /f/r.

Also chkdsk /p/r is okay as well.

I am assuming you know how to do this ask if needed, we all just want you up and running.;)

---

### Post by Terryracoon on 2010-09-18
ehm.... I don't D=
Sorry for being a complete noob... I've probably already annoyed the hell out of you xD

---

### Post by wilee-nilee on 2010-09-18
> **Terryracoon said:**
> ehm.... I don't D=
Sorry for being a complete noob... I've probably already annoyed the hell out of you xD


Nah it's all good.;)

So here is a link for a XP ISO if you need one to run the ```
chkdsk /f/r 
``` You just have to burn it to a cd
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Here is a link on how to get to the command line when booting the XP install cd.
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

Here is a great AV program that can be set to not run continuously and is recommended by my friends who do this for a living. Not any single AV program gets everything so it is good to have some options. Also the best way to run the AV is from safe mode=f8 prompt at booting XP for scanning.
[http://www.superantispyware.com/](http://www.superantispyware.com/)

Get the free version.

---

