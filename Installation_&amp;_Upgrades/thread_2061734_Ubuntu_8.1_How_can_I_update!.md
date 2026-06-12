---
title: "Ubuntu 8.1 How can I update?!"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by alexinexile83 on 2012-09-23
I installed ubuntu 8.1 on an old PC a few years ago to test it out. 

Last week end my laptop running ubuntu 11 died (either motherboard or psu) and i just cant afford to get it fixed at the moment.

So ive dug out my old pc with Ubuntu 8.1. However I cant update anything on it. I still had the USB Drive and files to install Ubuntu 11 BUT for some reason I dont have a standard BIOS menu.

Just GRUB. I am no Linux expert. I dont code. I just cant set it to boot from USB and I cant update Ubuntu 8.1 through update manager.

Can someone PLEASE tell me in plain english how to either update my system or find the blasted USB drive to reinstall!

I have spent 4 hours of my sunday off trying to fix this and right now I just want to smash the damn computer to pieces!:confused:

---

### Post by overdrank on 2012-09-23
Hi and this may help. [_EOLUpgrades_]("https://help.ubuntu.com/community/EOLUpgrades")

---

### Post by alexinexile83 on 2012-09-23
> **overdrank said:**
> Hi and this may help. [_EOLUpgrades_]("https://help.ubuntu.com/community/EOLUpgrades")

Ok...

How do I do this? Everything with Linux seems to assume a certain level of familiarity which I just dont have!

"Please make sure you have the following sources.list (/etc/apt/sources.list)."

What does this mean? What are sources? How do I get them? Where does all this text it keeps showing go? Do I open the 'Terminal'?

---

### Post by jerrrys on 2012-09-23
Why not just take the easy way out and do a fresh install.  In your case with old equipment I would suggest ubuntu 10.04

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by OrangeCrate on 2012-09-23
> **alexinexile83 said:**
> Ok...

**How do I do this? Everything with Linux seems to assume a certain level of familiarity which I just dont have!**

"Please make sure you have the following sources.list (/etc/apt/sources.list)."

**What does this mean? What are sources? How do I get them? Where does all this text it keeps showing go? Do I open the 'Terminal'?**

Since 8.10 has reached it's "end of life", as already mentioned, install a newer version, and then you won't have to worry about the suggestions from our kind Mod who particpated here.

Since you had 11.something on another computer, I assume you know how to burn a disk. If so, just get a copy of a current version and do a fresh install:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

(the last two options are probably better for older machines)

Also, please keep in mind, that a lot of members won't bother to help people where it is clear, that they have not attempted to find information or solutions on their own, prior to posting on the forums. Sad, but it is the mind-set of many here.

---

### Post by alexinexile83 on 2012-09-23
> **jerrrys said:**
> Why not just take the easy way out and do a fresh install.  In your case with old equipment I would suggest ubuntu 10.04

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Can I do that without creating a USB boot drive or burning a CD though?

---

### Post by Bucky Ball on 2012-09-23
*Thread moved to **Installation & Upgrades***

---

### Post by jerrrys on 2012-09-23
> **alexinexile83 said:**
> Can I do that without creating a USB boot drive or burning a CD though?

Nope :(

---

### Post by alexinexile83 on 2012-09-23
> **jerrrys said:**
> Nope :(

Well I cant do either of those! Ive tried but my Ubuntu is too old to run any USB creator programs. And I cant tell the pc to boot from USB anyway! >.<;

---

### Post by alexinexile83 on 2012-09-23
> **OrangeCrate said:**
> Since 8.10 has reached it's "end of life", as already mentioned, install a newer version, and then you won't have to worry about the suggestions from our kind Mod who particpated here.

Since you had 11.something on another computer, I assume you know how to burn a disk. If so, just get a copy of a current version and do a fresh install:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

(the last two options are probably better for older machines)

Also, please keep in mind, that a lot of members won't bother to help people where it is clear, that they have not attempted to find information or solutions on their own, prior to posting on the forums. Sad, but it is the mind-set of many here.

I spent 4 hours of my time this morning google searching answers and reading forum posts. Waste of time! I found instructions on how to set LInux to boot from USB using grub...

But couldnt find the usb drive! (I did use the find command on (hd1,0) to (hd9,0))

 I dont know GRUB and if it has a directory for all connected drives?

Id love to do a fresh install. On my laptop it was a piece of cake!

---

### Post by OrangeCrate on 2012-09-23
> **alexinexile83 said:**
> I spent 4 hours of my time this morning google searching answers and reading forum posts. Waste of time! I found instructions on how to set LInux to boot from USB using grub...

But couldnt find the usb drive! (I did use the find command on (hd1,0) to (hd9,0))

 I dont know GRUB and if it has a directory for all connected drives?

Id love to do a fresh install. On my laptop it was a piece of cake!

If you don't have a friend that would allow you to burn a disk on their computer, I don't know what else to add to help you. Good luck.

---

### Post by Bucky Ball on 2012-09-23
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

You could try downloading the ISO and using Unetbootin. The link's above if it's not in the repository for 8.10, if there still is one!

---

### Post by oldfred on 2012-09-24
BIOS controls booting from a device's MBR, then grub controls what to boot.

It was about 2006 that vendors converted BIOS to boot from USB ports. If an older computer, does it have USB as a boot option. Often you have to have bootable flash or hard drive connected before option appears, but older BIOS will never show it.

Some have said this works to boot when BIOS does not allow it.
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

---

### Post by Hylas de Niall on 2012-09-24
If you're in the UK, you could nip in to WHSmiths (Other newsagents may stock it too) and buy a copy of 'Ubuntu User', which comes with a live cd of the latest _L_ubuntu.

I hope that doesn't get rapped as spam, because it really isn't.

Hope that helps

Hy

---

