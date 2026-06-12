---
title: "How to Remove GRUB 2 (Ubuntu 9.10) and replace it with Windows MBR?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by Mr.ALMohammady on 2009-12-19
Hi Everyone
I just Installed Ubuntu 9.10 in my laptop since 2 days ago.. today I've back to my works that in Windows 7 OS.. Before that I Installed Ubuntu in an external Hard desk.... then I Surprised that I Should plug the hard desk evey time that I want to Lunch my device!!!!!! ever if I don't want Ubuntu OS.... so.. I hope that someone help me in my problem and I want to remove this Stubbed GRUB please ... how to do it???
Pleeeeeeeeeeeeeeeeeeeeese help me I have a many many Important works and I don't have a time to check every time if the hard desk with me or not....

---

### Post by darkod on 2009-12-19
Instructions to restore various bootloaders here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Greenwidth on 2009-12-19
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Mark Phelps on 2009-12-19
The MS instructions presume you have a Win7 Installation DVD.  If you have that, you can follow the instructions there and restore your MBR.

If you don't have that, since you have _many important files_ on your system, you did at least take the 5 MINUTES needed to create and burn a Win7 Recovery CD from inside Win7, right?

IF not, you're basically hosed.

---

### Post by darkod on 2009-12-19
> **Mark Phelps said:**
> The MS instructions presume you have a Win7 Installation DVD.  If you have that, you can follow the instructions there and restore your MBR.

If you don't have that, since you have _many important files_ on your system, you did at least take the 5 MINUTES needed to create and burn a Win7 Recovery CD from inside Win7, right?

IF not, you're basically hosed.

Not exactly, although you should have made a backup first and a recovery disc. You can find win7 repair disc image here. This disc will only allow you to repair the boot process, NOT to install full win7 installation.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by kansasnoob on 2009-12-19
> **Mr.ALMohammady said:**
> Hi Everyone
I just Installed Ubuntu 9.10 in my laptop since 2 days ago.. today I've back to my works that in Windows 7 OS.. Before that I Installed Ubuntu in an external Hard desk.... then I Surprised that I Should plug the hard desk evey time that I want to Lunch my device!!!!!! ever if I don't want Ubuntu OS.... so.. I hope that someone help me in my problem and I want to remove this Stubbed GRUB please ... how to do it???
Pleeeeeeeeeeeeeeeeeeeeese help me I have a many many Important works and I don't have a time to check every time if the hard desk with me or not....

If you would please either boot into Ubuntu or boot the Ubuntu live CD and post the output from terminal of:

```
sudo fdisk -l
```

BTW that's a lower case L.

You're actually hard to read, but I assume you installed Ubuntu to an external drive and now can't boot Windows unless the external drive is plugged in.

Also since this is a laptop it probably has only one internal hard drive. If that's true you should be able to get Win 7 booting on it's own again by either booting into the Ubuntu drive or the Ubuntu Live CD and running:

```
sudo apt-get install mbr
``` then:

```
sudo install-mbr /dev/sda
```

**[COLOR="Red"]NOTE: I'm using sda there BUT THAT MAY NOT BE CORRECT![/COLOR]**

I first need to see the output of "sudo fdisk -l"!

Slow down, take a breath and let's work it out!

It would also be helpful to know what type of drive you installed Ubuntu on, as I assume you'd like to be able to boot it again someday????

---

### Post by Jim_in_Omaha on 2010-04-24
kansasnoob,

You don't know how much I appreciate what you put in this post.

1000 thank you's....

---

