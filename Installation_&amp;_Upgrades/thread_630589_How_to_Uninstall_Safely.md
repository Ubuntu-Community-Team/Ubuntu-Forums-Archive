---
title: "How to Uninstall Safely"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by whitenerdy92 on 2007-12-03
How do I unitnstall Ubuntu Gutsy safely when Vista is on the same hard drive? I have heard that simply getting rid of the Ubuntu partition will make Vista unbootable, because GRUB turns Window's boot loader off. Could anyone tell me how I can safely remove Ubuntu, and put the hard drive back to its pre-Linux state?

---

### Post by Pumalite on 2007-12-03
You can use Gparted Live CD to erase the Ubuntu partition and then fix your Windows MBR with your Installation CD or Super Grub.

---

### Post by whitenerdy92 on 2007-12-03
That was my first idea, to use GParted; however, that does not work with that computer, an error message came up (I forget what it said sorry, if you need to know what it said I can try running it again).

---

### Post by whitenerdy92 on 2007-12-03
Also, the installation CD was lost; talk about inconvinient.

---

### Post by Pumalite on 2007-12-03
Use any partitioner and download and burn to a CD Super Grub and use as instructed.

---

### Post by whitenerdy92 on 2007-12-03
what partitioner would you recommend? By the way, here's what I've decided to do about booting:
1. Install a Windows-Based boot loader (VistaBootPRO, or maybe Acronis DiskDirector Trial), or
2. Install that, but then uninstall it, because (usually) the uninstaller sets the boot loader to Windows. This happened to me once accidentally.

---

### Post by erfahren on 2007-12-03
see: [http://ubuntuforums.org/showthread.php?t=482798&highlight=grub](http://ubuntuforums.org/showthread.php?t=482798&highlight=grub)

which one of the ways basically leads back to the "Uninstall" page of the popular [Illustrated Dual Boot Site](http://users.bigpond.net.au/hermanzone/) (the first site a came across when I looked into dual-booting).

Anyway, what I was going to say was that if it were me I'd first repair the MBR and then use Vista's Disk Management utility (part of the Administrative Tools) to delete/reformat the Linux partition(s).

I'd just make an extra partition out of what was there and use it for storage or whatever. That way the Vista partition wouldn't need to be messed with at all.

... but that's me

---

### Post by Pumalite on 2007-12-03
Any that boots in your computer will do because the thing is to erase the partition and restore MBR with Super Grub (which is excellent BTW)

---

### Post by whitenerdy92 on 2007-12-03
Can Vista's partition manager see ext3? If it can I'm all set :]


...It appears that it can! It just shows it as an 'unknown filesystem'.

---

### Post by erfahren on 2007-12-03
> **whitenerdy92 said:**
> Can Vista's partition manager see ext3? If it can I'm all set :]


...It appears that it can! It just shows it as an 'unknown filesystem'.
yeah, just delete the partition for Ubuntu and the one for swap and reformat the free space created to ntfs (or whatever). Windows will asign a drive letter to it. (you might've figured all that out already.)

also, this way if you want to install a Linux distro later the space is already there :)

sry to hear you're deleting it.

good kuck

---

### Post by whitenerdy92 on 2007-12-03
Yep, thats the easy and low-risk part, it's the boot loader I'm worried about, but I've backed-up most things, and I have the install disk, so even in a worst-case scenario I figure I'm pretty safe.

BTW, this isn't my computer, it's my brothers, the disk I gave him had errors and then he decided he didnt want Ubuntu any more becuase of it. I still use Ubuntu, and love it! :]

---

### Post by whitenerdy92 on 2007-12-03
> **whitenerdy92 said:**
> 
...Install a Windows-Based boot loader (VistaBootPRO, or maybe Acronis DiskDirector Trial)...


VistaBootPRO should work, right?

---

