---
title: "Can't install Xubuntu 18.04 32 bit"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by genialloyd95 on 2018-05-09
Hello everyone. This is not my first time dealing with a Linux OS installtion, in the past I have used Ubuntu 7.04 and worked some time with Kubuntu and Mint, eventually going back to Windows for various reasons.
So, I have this old desktop PC from where I'm writing right now, through the live USB, which I wanted to give new life to, using Xubuntu. Since it has no CD reading unit, I used USB drives. Unfortunately, after many attempts, it seems I'm still doing something wrong. I've tried everything, but the installer still crashes at some point ("This is often due to a faulty CD/DVD"), after also at least one warning while copying the files that a file doesn't correspond to the original on the support. The errors I get are practically the same every time, with "Errno5: Input/Output" being the most common. I've followed the guide to create an installation USB drive thoroughly, but it doesn't work. I tried to burn the .iso image of Xubuntu 18.04 (32bit) from my main desktop PC running Windows 10 (64bit), using two different USB drives in different several attempts, but nothing. The two different USB drives have always worked fine as regular archives for files. The hard disk I'm using on this old PC is a brand new 500GB SATA drive, since the original one was broken. This PC has 3GB of DDR3 RAM and an AMD Phenom II (can't remember the clock), I'm using the motherboard integrated graphic card.

What I have done to try preventing any error from happening:
[LIST]
[*]**I checked the md5sum** of the downloaded .iso: it matches.
[*]Before running Rufus, I disabled my antivirus and closed any running program and any superfluous background process and, while Rufus was working, I didn't do/touch anything at all.
[*]I asked Rufus to check for badblocks on the drives (1 pass), nothing wrong was found on any drive, while leaving any other option set on its default value as suggested by the official guide.
[*]After several attempts, once booted into live USB, I tried to uncheck the "Download updates while installing" and "Install 3rd party software" options to free the installation from some duties, with no final benefit.
[/LIST]

I've ran out of resources, I have no idea of what to do, please help. Ask for any information you think is useful for figuring out a solution.

---

### Post by Xian on 2018-05-10
Try writing to the USB in DD image mode.

[[IMG]http://i.imgur.com/y5GoukPm.png[/IMG]]("https://imgur.com/y5GoukP")

---

### Post by sudodus on 2018-05-10
Have you checked that the RAM is good? You can do it with **memtest** from the boot menu of the live system (when booted from the USB pendrive). A thorough test lasts for a long time (overnight) and **there should be no error at all**.

You can also check/replace the connecting wires to the internal hard disk. Maybe it is enough to unplug and plug in again to remove some oxide layer and get a good connection again.

An alternative is to download [Xubuntu Core](https://unit193.net/xubuntu/core/)

```
663M apr 26 21:58 xubuntu-18.04-core-amd64.iso
```

which is small enough to fit in a CD disk, but I think your USB boot drives are OK (which you can check too) according to this link,

[Check the packages in the install drive with the boot menu option 'Check the disk for defects'](https://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

---

### Post by genialloyd95 on 2018-05-10
Good morning, thanks for answering.
> **Xian said:**
> Try writing to the USB in DD image mode.
Unfortunately, nothing changed: as usual, while copying the files, I got a warning that a file wasn't the same as the one on the "CD", then "Errno5: Input/Output" occurred.

> **sudodus said:**
> Have you checked that the RAM is good? You can do it with **memtest** from the boot menu of the live system (when booted from the USB pendrive). A thorough test lasts for a long time (overnight) and **there should be no error at all**.

You can also check/replace the connecting wires to the internal hard disk. Maybe it is enough to unplug and plug in again to remove some oxide layer and get a good connection again.

An alternative is to download [Xubuntu Core]("https://unit193.net/xubuntu/core/")

```
663M apr 26 21:58 xubuntu-18.04-core-amd64.iso
```

which is small enough to fit in a CD disk, but I think your USB boot drives are OK (which you can check too) according to this link,

[Check the packages in the install drive with the boot menu option 'Check the disk for defects']("https://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608")

I tried running a "check defects on the disk", but this error occurred: 
[IMG]http://i64.tinypic.com/142x74m.jpg[/IMG]

The first three lines actually occurr every single time I boot from the live USB, before coming into the Xubuntu loading screen and then the choice between "try" and "install", but I've never seen the other lines, I don't know their meaning.
After rebooting, **I ran the memtest** instead: it's been running for only 10 minutes and it has already found 103.000+ errors (the lower half of the screen is full of red lines). I guess we figured out what the actual problem is... The RAM. There's no solution other than getting a new one, right?

---

### Post by sudodus on 2018-05-11
That's right, I am rather sure that you need new RAM. But if you have more than one RAM stick, you can unplug them (and run memtest again) so that you can find which stick is good and which is bad.

It is important to have the same kind of RAM sticks, so be careful, when you buy a new one.

---

### Post by ubfan1 on 2018-05-11
Try reseating the  ram cards/chips also.

---

### Post by Autodave on 2018-05-11
Changing the order of the sticks sometimes will help, too.

---

### Post by marcel.espinosa on 2018-08-02
Any luck with the installation? I have the same problem with xubuntu 18.04 64 bits. I've downloaded from torrent and from direct link, also the derivative Voyager Linux 64, both from torrent and direct link. Burn CD's in KDE with k3b, and in another computer with xfburn. Nothing works. I'm trying with a usb using nautilus right click, both xubuntu and voyager. Is not the hard disk, as I'm able to install ubuntu and lubuntu without problems. Is not the RAM, as this happen in two different computers. Both of my computers have only 2 Gb of RAM, but can run ubuntu, lubuntu, manjaro or kaos. What can be happening?

Thanks in advance

M.

---

### Post by oldos2er on 2018-08-03
[marcel.espinosa]("https://ubuntuforums.org/member.php?u=2103570"), please start your own thread. genialloyd95 hasn't returned to the forum since May.

---

