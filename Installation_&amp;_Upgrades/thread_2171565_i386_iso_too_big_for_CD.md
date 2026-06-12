---
title: "i386 iso too big for CD"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by Cal_Skeptic on 2013-08-31
The 12.04.3 file size is listed at 706Mb, but when downloaded it becomes 741Mb, which will not fit on a CD.  What is going on here?

---

### Post by oldfred on 2013-08-31
[http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead](http://www.omgubuntu.co.uk/2012/09/its-official-the-ubuntu-livecd-is-dead)

They just have too much to include for a full featured system. Since DVD are lower in cost and now most users use flash drives it is less of an issue. And a flash drive is reusable and faster to install from.

I now install directly from one hard drive to another by using grub2's loopmount feature so I do not use any external device normally.

---

### Post by hg-knight on 2013-08-31
try using a memory stick

---

### Post by grahammechanical on 2013-08-31
I do not understand how a 706MB image can be burned to a disk that is limited to 700MB capacity anyway.

> [COLOR=#FF0000][FONT=Ubuntu]Warning: This image is oversized (which is a bug) and will not fit onto a standard 703MiB CD. However, you may still test it using a DVD, a USB drive, or a virtual machine.[/FONT][/COLOR]

It is there on the download page

[http://cdimage.ubuntu.com/precise/daily-live/20130830.1/](http://cdimage.ubuntu.com/precise/daily-live/20130830.1/)

Regards.

---

### Post by prodigy_ on 2013-08-31
> **Cal_Skeptic said:**
> it becomes 741Mb
It doesn't. 1MiB = 1048576 bytes. 741,000,000 bytes / 1048576 = ~706.7 MiB.

---

### Post by ibjsb4 on 2013-08-31
Download the mini iso (<30M) and just add ubuntu-desktop to it :)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Cal_Skeptic on 2013-08-31
Thanks for the input, guys.  I guess if a computer is so old it will neither boot from a flash drive nor read a DVD, I'll just have to tell the owner to get a new one.  :)

---

### Post by mikewhatever on 2013-08-31
If the computer is so old, you probably don't need a newer kernel for better hardware support. So try [Xubuntu 12.04.1]("http://old-releases.ubuntu.com/releases/xubuntu/releases/12.04.1/release/xubuntu-12.04.1-desktop-i386.iso"), or, in case you need Ubuntu, go with [Ubuntu 12.04.1]("http://old-releases.ubuntu.com/releases/12.04.1/ubuntu-12.04.1-desktop-i386.iso").
Both have the 3.2 LTS kernel, and fit on a CD very nicely.

---

### Post by sudodus on 2013-09-02
I think [Xubuntu 12.04 LTS]("http://xubuntu.org/getxubuntu/") or [Precise Gnome Classic Tweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks") are good candidates for that computer.

An alternative, if there is USB, but it won't boot from it, is to boot from a [Plop boot manager]("http://www.plop.at/en/bootmanager/download.html"). The Plop can be on floppy, CD, or hard disk, and can install drivers, so that it will be possible to continue booting from USB.

---

### Post by VMC on 2013-09-02
> **Cal_Skeptic said:**
> Thanks for the input, guys.  I guess if a computer is so old it will neither boot from a flash drive nor read a DVD, I'll just have to tell the owner to get a new one.  :)
What's the hardware specs of the "old" computer?

---

### Post by Topsiho on 2013-09-03
If the old computer has a 32 bit processor which doesn't support pae (physical address extension), you'll not be able to put a newer Ubuntu onto it.
pae enables a 32 bit processor to recognize more than 3 à 4 GB of RAM.

Topsiho

---

### Post by mörgæs on 2013-09-03
> **Topsiho said:**
> If the old computer has a 32 bit processor which doesn't support pae (physical address extension), you'll not be able to put a newer Ubuntu onto it.
pae enables a 32 bit processor to recognize more than 3 à 4 GB of RAM.

Topsiho

This is neither correct nor relevant to original poster.

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by Topsiho on 2013-09-03
"This is neither correct nor relevant to original poster."

As far as I am aware the original poster talks Ubuntu. Ubuntu 12.04 does not run on non-pae 32 bits processors. In the other reactions this was not mentioned, so I did mention it myself, just to be sure.
I don't see what is wrong mentioning something which the OP might not be aware of, and might be helpful to him just to know it. We are here to help each other, is my idea.

On my non-pae computer I run Xubuntu, which is fine, but it is of course not Ubuntu.

Topsiho

---

