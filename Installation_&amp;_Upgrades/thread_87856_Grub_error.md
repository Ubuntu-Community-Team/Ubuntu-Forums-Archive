---
title: "Grub error"
date: 2005-11-09
forum: Installation &amp; Upgrades
---

### Post by mcrane on 2005-11-09
I just installed Ubuntu 5.10 (amd64) on a 15GB drive on a promise fasttrack66 controller. When the machine did the reboot after the initial part of the install I got grub error 17 instead of the menu. I've checked my menu.lst and device.map files and they seem to be in order. I have a boot CD with some DOS utils and this CD also has the option of booting from the hard drive. If I choose that option then the grub menu comes up and I can boot into linux.

Why would grub fail when booting straight to the hd but work if I boot to a CD and then chain to the HD?

Other details:
The drive (/dev/hdg) is the only drive on the second channel of the controller. There is a drive on the first channel of that controller as well. The motherboard has 4 PATA ports, two of those eachhave a hard drive plugged in, another has a DVD drive attached and the other a CD burner. The 4 SATA ports are empty.

---

### Post by BoxCar on 2005-11-20
McCrane, have you been able to resolve this issue? I am having similar problems -- [http://www.ubuntuforums.org/showthread.php?p=506259]("http://www.ubuntuforums.org/showthread.php?p=506259").

---

### Post by Peter Scales on 2005-11-20
See the help I got in " New Install"

My Grub errors were the same

---

### Post by mcrane on 2005-11-23
No, I've had no luck. I borrowed a copy of SuSE 10 and installed that. By default, SuSE wanted to put the swap partition first as a promary partition and put the filesystem root in an extended partition. That resulted in grub error 5, if I recall. I reinstalled again and situated the partition just like the ubuntu defaults and got the same grub error 17. Either was I could boot by booting the SuSE dvd or a utilities CD I have and then chain loading to the hard drive (this doesn't work with the Ubuntu CD, btw), but I can't boot directly from the HD.

I also found newer firmware for my PCI IDE controller (and ultra66 not fasttrack66 as I mistakenly stated above), but it made no difference.

---

### Post by BoxCar on 2005-11-28
yeah, me neither. I even updated my BIOS to no avail.

I tried this [http://software.newsforge.com/article.pl?sid=05/02/15/2023237&from=rss](http://software.newsforge.com/article.pl?sid=05/02/15/2023237&from=rss) and it didn't work either.

---

### Post by Topsiho on 2005-11-29
If you do a google search (with: grub error 17) you get swamped in information :0 on this problem. Maybe you can get precisely the information you need this way.

Seems that grub detects your partition(s) but can not determine the type(s).

Googling is quite often a very good start to fix errors ........

Topsiho

---

### Post by mcrane on 2005-12-01
[QUOTE=Topsiho]If you do a google search (with: grub error 17) you get swamped in information :0 on this problem. Maybe you can get precisely the information you need this way.

Seems that grub detects your partition(s) but can not determine the type(s).

Googling is quite often a very good start to fix errors ........

Topsiho[/QUOTE]

That's the first thing I did and I did get swamped with hits, none of which was any help.

---

### Post by Topsiho on 2005-12-02
OK, sorry

Topsiho

---

### Post by bwog on 2005-12-02
@mccrane: I had a problem with a highpoint controller, that may be similar. I solved it temporarily by putting the ubuntu hard disk on the first ide controller and reinstall. There it is denoted /dev/hda (instead of hde) and all is well.

I want it on the fast highpoint controller later and will try some bios options to do that when I have time for it.

---

### Post by ajaustin on 2005-12-22
I am currently working around this by booting from a floppy.

```
grub>root (hd0,0)
grub>kernel /vmlinuz....   root=/dev/md2
grub>initrd /initrd....
grub>setup (fd0)
```

I think its a bug and plan to report it.

Tony

---

