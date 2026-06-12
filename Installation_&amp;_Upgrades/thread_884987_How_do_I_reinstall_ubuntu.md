---
title: "How do I reinstall ubuntu?"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by hgfdsa on 2008-08-09
I made my partitions incorrectly, they are not divided properly, so is there a way to delete my two ubuntu partitions completely? When I turn my computer on, it gives me 6 choices, where as before I had nothing. When I pick XP from the list, it brings me to a second list asking me to pick between xp and ubuntu again. I believe the reason for the second list is my first failed installation of ubuntu, so how do I completely remove ubuntu and also fix my bootloader or whatever it's called that shows up at startup? Also, how do I change which operating system starts up by default? Thanks.

---

### Post by cdtech on 2008-08-09
Just insert and boot from the "gparted Live CD" and you can adjust your partitions accordingly. You wont loose any data doing this......

As far as your Bootloader, after you have the partitions configured, you can run the GRUB command to repair your Bootloader. Boot into the Live CD, on a command line type:
```
grub-install /dev/**sda**
```
(sda being the primary partition)

---

### Post by hgfdsa on 2008-08-09
> **cdtech said:**
> Just insert and boot from the "gparted Live CD" and you can adjust your partitions accordingly. You wont loose any data doing this......

But I wanted to split my /home and /partitions and was told this
> **Partyboi2 said:**
> If you currently have your /home as part of the / partition and want to put it onto its own partition you can follow [[COLOR=Blue]this[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") guide. But it probably be quicker to reinstall and make the partitions.
15 gig  /
54 gig /home
1 gig swap

---

### Post by cdtech on 2008-08-09
I would need to see the output of "sudo fdisk -l" you can modify all of your partitions within "gparted" to do this.

**P.S.**
Wiping a hard drive for any reason is no way to learn Linux. Only if it is so corrupt would it be necessary to reformat I think.

Learn to correct the issue, it's a much rewarding experience to know you fixed the problem than to never know.

---

### Post by hgfdsa on 2008-08-09
> **cdtech said:**
> I would need to see the output of "sudo fdisk -l" you can modify all of your partitions within "gparted" to do this.

If I run the command, how do I save the results, because my ubuntu's network adapter isn't working yet, and my XP can't access the Ubuntu partitions at all. I'll try to get the internet on that working or else i'll post back here.

---

### Post by cdtech on 2008-08-09
This is my drive partition setup:
[ATTACH]80866[/ATTACH]
You can move partitions, resize, and create.

---

### Post by hgfdsa on 2008-08-09
> **cdtech said:**
> This is my drive partition setup:
[ATTACH]80866[/ATTACH]
You can move partitions, resize, and create.

sudo fdisk -1 didn't worl but sudo fdisk-l did and that gave me this which I wrote and am now typing, so formatting might be off.

xxxxxxxxxxxxxStartxxEndxxxID
/dev/sda1xxxx1xxxxxx784xxx12x       compaq diagnostics
/dev/sda2xxxx785xxxx15728x7  x      hpfs/ntfs
/dev/sda3xxxx15729xx24792x5   x     extended
/dev/sda5xxxx15729xx24604x83   x    linux
/dev/sda6xxxx24605xx24792x82    x   linux swap/solaris

could you also help me with this: 
[http://ubuntuforums.org/showthread.php?p=5556170](http://ubuntuforums.org/showthread.php?p=5556170)

---

### Post by hgfdsa on 2008-08-09
CDtech, you still there?

---

### Post by cdtech on 2008-08-09
You can just hi-lite anything you type, copy and paste here or copy from here and paste into your terminal (such as the "sudo fdisk -l"). Sometimes the eye will play tricks on you while typing commands. It's better to copy and paste. There is a space between the fdisk and -l.

Do you have a "gparted Live CD"? You'll find this to be of great use anytime you have to work with your "root" partition.

You can get the "gparted Live CD" from here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Burn it to disk and put it somewhere safe.

---

### Post by hgfdsa on 2008-08-09
> **cdtech said:**
> You can just hi-lite anything you type, copy and paste here or copy from here and paste into your terminal (such as the "sudo fdisk -l"). Sometimes the eye will play tricks on you while typing commands. It's better to copy and paste. There is a space between the fdisk and -l.

Do you have a "gparted Live CD"? You'll find this to be of great use anytime you have to work with your "root" partition.

You can get the "gparted Live CD" from here:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Burn it to disk and put it somewhere safe.

I just took the easy way out and used my ubuntu live cd's gparted to delete my current partitions and reinstall ubuntu.

---

### Post by cdtech on 2008-08-09
That's ok to but now you understand a little more about partitions. :)

---

