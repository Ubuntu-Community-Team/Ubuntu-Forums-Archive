---
title: "Question: Importing WindowsXP before/while installing Ubuntu?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Jokermx on 2007-10-18
Alright, first let me give a bit of a background story of what's happening:

I used PartitionMagic to make two partitions on my HDD, one part for Windows XP, and one part for Ubuntu. I recently had to delete one of these partitions since I ran out of space (80GB HDD), so I decided to delete the Ubuntu partition with PartitionMagic, and resized my XP part to the whole 80GB possible. I then copied all stuff I wasn't using onto DVD's to clear up space.

Upon restarting (and trying to install Ubuntu, again), I noticed that instead of having the OS boot selection screen, an error showed up, and there was no way to load up XP. So now I'm using the 6.04 Live CD, and while I can see all the files on the Windows side (disk), I want to know if there's a way to install Ubuntu **AND** import all my music and videos without having to make back-up CD's/DVD's?

Alright, let me put it more simple: Can I copy/drag music and video files to the Live CD desktop, install Ubuntu and **NOT** lose said files? Nothing shows up in the "Import files from partitions" installation menu.

---

### Post by cchester on 2007-10-18
> **Jokermx said:**
> Alright, first let me give a bit of a background story of what's happening:

I used PartitionMagic to make two partitions on my HDD, one part for Windows XP, and one part for Ubuntu. I recently had to delete one of these partitions since I ran out of space (80GB HDD), so I decided to delete the Ubuntu partition with PartitionMagic, and resized my XP part to the whole 80GB possible. I then copied all stuff I wasn't using onto DVD's to clear up space.

Upon restarting (and trying to install Ubuntu, again), I noticed that instead of having the OS boot selection screen, an error showed up, and there was no way to load up XP. So now I'm using the 6.04 Live CD, and while I can see all the files on the Windows side (disk), I want to know if there's a way to install Ubuntu **AND** import all my music and videos without having to make back-up CD's/DVD's?

Alright, let me put it more simple: Can I copy/drag music and video files to the Live CD desktop, install Ubuntu and **NOT** lose said files? Nothing shows up in the "Import files from partitions" installation menu.

Ok if you have reinstalled Ubuntu which it kinda looks like that is what you are saying then yes within Ubuntu you can copy the files over to your Ubuntu installation. You just need to make sure you have NTFS support installed and working which it seems you do since you are saying that you can see the files. If your Win XP is on a Fat32 partition then you are already set.

I am just a little confused because one of your statements mention you are using a live CD so if you are running Ubuntu using that and are looking at your WIN XP partition without having Ubuntu installed then no you can not copy the files over (that I know of so please correct me if I am wrong).

It looks like maybe the reason why WIN XP is not booting from the grub menu if that is what you are picking it from then it could be a grub issue of why WIN XP wont boot. If so then we will need to know the grub error to help more. The good news is that it seems like your WIN XP installation is still there so it should be able to be fixed.

Here is a link to Super Grub Disc which can also help in repairing your problem and should make it so you will be able to boot back into WIN XP if you need to.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

Hope this helps.

---

### Post by spii on 2007-10-18
You will have lost grub (the boot loader - it gave you the OS boot selection screen) when you wiped out your ubuntu partition. I've done this too :)

Put your XP CD in and look for recovery/repair options (don't reinstall, that will wipe out your files). The command you want is fixmbr (to fix the master boot record). You'll want to find better instructions than these before giving it a go, but it is fairly painless. Once fixed, your system will boot up XP immediately (like it did before you ever installed ubuntu). If you later reinstall ubuntu, it will come with grub again and you'll get the OS boot selection screen (and if you wipe it out you'll need to do the XP fixmbr thing again).

Best of luck :)

---

### Post by dweez on 2007-10-18
Did you have XP installed on the second partition?  If so, when you deleted the one and resized the second, your partition number for your XP install changed and your boot.ini file is pointing at the wrong location.

For instance, in the above explanation, your boot.ini would be something like the following:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\Windows
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\Windows="Windows XP Professional" /noexecute=optout /fastdetect

```

But now your partition location has changed to the first partition so you would need to edit your boot.ini and change the "2"s to "1"s.

---

