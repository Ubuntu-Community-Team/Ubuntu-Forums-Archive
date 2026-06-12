---
title: "Oh no! Partition issue during install :("
date: 2007-02-23
forum: Installation &amp; Upgrades
---

### Post by herbster on 2007-02-23
Hi folks, here is my setup:

IDE1 Seagate 40gb = XP SP2
IDE2 Maxtor 40gb = Blank
SATA 320gb = Vista Ultimate

The situation is that I had IDE2 wiped clean, with the intention of installing Ubuntu onto it. However, for some absolutely insane reason I cannot recall right now I selected my IDE1 during Live CD install of Ubuntu 6.10 and then selected the partition option, and it was busy doing its thing but it just sat there with the busy cursor. Well, it sat there for a long time and so I rebooted my PC and ran Live CD install again, this time installing to my IDE2 (empty at that point).

So now this is what is happening-- I plug in all 3 drives, and I get grub with all options and can boot to Ubuntu and to XP, but not to Vista-- when I boot to Vista, the system completely hangs right after the "Microsoft" text and green shaded progress bar appears.

When I go into BIOS and tell it to boot off SATA, Vista hangs in the same way. The only way I can get into Vista is to physically disconnect my IDE1, leaving IDE2 and SATA plugged in and boot off SATA. To use Ubuntu and XP, I have to plug my IDE1 back in to get Grub.

So I am in XP right now copying over all my important files to my SATA. Now, I am fine with formatting this drive and reinstalling XP (IDE1), however, it is the drive with Grub (sorry for terminology, but it has the "boot record" I believe) and so if I format it how can I ever boot into Ubuntu? What do I do?

Thanks so much in advance to anyone who can help.

---

### Post by rsambuca on 2007-02-23
Did you install Vista from within XP, or a boot from the DVD.  In any event, I believe you will have to "hide" XP and Vista from each other.  there is an entry in grub for this, but I don't know what it is off hand.  If you search for grub, hide, xp, vista, I am sure you will find it here.  Sorry, I don't have time to find it right now.  If you can wait until tomorrow morning (for me), I can look it up for you.

---

### Post by herbster on 2007-02-23
> **rsambuca said:**
> Did you install Vista from within XP, or a boot from the DVD.  In any event, I believe you will have to "hide" XP and Vista from each other.  there is an entry in grub for this, but I don't know what it is off hand.  If you search for grub, hide, xp, vista, I am sure you will find it here.  Sorry, I don't have time to find it right now.  If you can wait until tomorrow morning (for me), I can look it up for you.

rsambuca,

I didn't know that!!! As a matter of fact, what I was normally doing prior to installing Ubuntu is simply going into BIOS at startup and selecting which drive to boot from depending on which Windows I wanted to use. I guess now Grub changes that?

I am going to perform a search and will reply if I have found it, if not please by all means your help is appreciated... thanks!

---

