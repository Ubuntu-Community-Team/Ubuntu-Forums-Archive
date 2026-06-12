---
title: "Safely Removing Primary Ubuntu Install from Triple Boot system"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by mchoo on 2007-07-23
Hi.... I currently have a triple boot system: XP Pro, Ubuntu64 Feisty Fawn and Kubuntu64 Feisty Fawn. The Kubuntu was installed last, hence the GRUB was "based" on it.

Now, if I were to remove Kubuntu by simply deleting its root partition from, say, Ubuntu, I presume that I would not be able to boot my system anymore since the MBR would be looking for Kubuntu installation. Is this correct? How do I safely remove Kubuntu then?

Thanks very much...

---

### Post by MrHippocampus on 2007-07-23
Looks like you should restore the grub from your normal ubuntu install first, and then remove Kubuntu. Assuming you dont have a separate partition for any grub, the instructions should be something like:

boot into normal ubuntu and in a terminal type
```

grub

```

then type
```

root (hd0,*)
setup(hd0)

```
the * is the number of the partition the grub files you want to use are on, this starts from 0 unlike hd*/sd* which start from 1. If you restart you should then be booting from your normal ubuntu grub and can safely delete your Kubuntu

---

### Post by mchoo on 2007-07-23
Thanks. I'll try that when I'm back home (at work now...)

---

### Post by mchoo on 2007-07-25
Hi... me again... Obviously I'm an absolute newbie with Linux. I'm kinda stuck with this "safe removal of Kubuntu" business... I have absolutely no clue what's the hard drive name/number.

Now, I have 1x 40GB IDE HDD in IDE0 (Master), and a 250GB SATA. GParted refers to the IDE HDD as /dev/hda, and the SATA HDD is /dev/sda. 

The SATA has 3 primary paritions: 
Primary #1 (/dev/sda1) = NTFS
Primary #2 (/dev/sda2) = NTFS
Primary #3 (/dev/sda4) = ext3 - where Ubuntu is installed
Plus 1 extended partition (/dev/sda3) with 2 logical volumes:
Logical #1 (/dev/sda5) = NTFS
Logical #2 (/dev/sda6) = ext3 - this is where Kubuntu is installed

So... what value do I use in the "grub" command to set the Ubuntu partition as the primary boot partition, so that I can safely remove Kubuntu.

Thanks so much in advance for any assistance...

Cheers

---

### Post by MrHippocampus on 2007-07-25
ok, the easy way to do this (sorry, I really should have posted this before) is to run grub in a terminal and then type

```

find /boot/grub/stage1

```

That will search all of your drives/partitions until it finds an installation of grub, it should find the ubuntu one first and give you a location e.g. (hd0,2), this is the location you should use for the next command:

```

root (hd0,2)

```

Then you can install grub to the mbr by doing
```

setup (hd0)

```

Hopefully when you restart grub should work and be booting from your ubuntu install. However to be absolutely sure, i suggest you make a small modification to the file /boot/grub/menu.lst.

Open the file up as root ("gksudo gedit /boot/grub/menu.lst" should work) and scroll down until you see a long line with "kernel" at the start (there will be a few of them, take the top one as this will be the top one when you next see grub), go to the end of the line and remove the word "quiet", next time you restart ubuntu should come up with words beneath the ubuntu logo as it loads. This means that grub is definitely booting from your ubuntu and it is safe to remove kbuntu.

On a side note I would recommend backing up any important/valuable data you have, I highly doubt anything will go wrong but its always good practice to do it when messing around grub/deleting partitions :)

---

### Post by mchoo on 2007-07-25
Thanks mate. I'll try it later when I'm home.

---

### Post by mchoo on 2007-07-26
Hi again... I found that /boot/grub/stage1 file is not quite readable. However, I found device.map file in the same directory that told me what the HDD designation is (hd0 for the IDE, hd1 for the SATA). I also found that had I bothered to look closely into menu.lst file, I would've been able to find what I was looking for anyway! D'oh!!

Anyway, entered the right parameter into the "root" command in grub, accepted, rebooted the PC, and it appeared that the boot loader still used Kubuntu's menu.lst file (the content of the menu.lst files are different between Ubuntu and Kubuntu). This suggested to me that the boot loader is still using Kubuntu. Bugger!!

I'm willing to give it another go before I throw caution to the wind and delete the Kubuntu partition anyway (and potentially reinstalling Ubuntu).

Is there some kind of a repair utility on the Live CD, similar to Windows' FIXMBR?

Thanks.

---

### Post by MrHippocampus on 2007-07-27
Basically the way you would do it on a live CD is the same way you would do it from your k/ubuntu install, run "grub" type some commands in. I would suggest maybe playing around a bit more (specifically with the root(hdx,x) command, as thats what points grub to the correct partition). But as you say if all else fails you can reinstall :(

---

