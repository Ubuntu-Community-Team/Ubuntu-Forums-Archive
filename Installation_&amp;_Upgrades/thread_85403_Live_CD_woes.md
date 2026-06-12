---
title: "Live CD woes"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by studebakerhawk on 2005-11-02
I recently have dl'd and burned both a copy of the live and boot cds. The I cannot boot from the install cd, I have written that off as a corrupt file. What gets me is that I cannot boot off the live CD. If I mount the image, I am greeted with the beginning graphic interface and short tour, with options to install openoffice, etc. However, I simply cannot boot off the cd.The BIOS boot order is correct, I have gone as far as to completely disable booting from the HD and still- nothing. Anyone have any suggestions? I anxious to start learning my way around *nix systems.

EDIT: cannot boot off of install disk either, these problems happen on both laptop and desktop- bad disks?! 2 of them?

---

### Post by phanboy_iv on 2005-11-02
Maybe you have a corrupted ISO? Did you check the md5 sums?

From the terminal

> md5sum /path/name/of/your/iso

and compare the number/letter string it spits out to the one in the md5sum text file
in the Downloads section of the Ubuntu site.

Although from what you are saying, that's probably not it.

Oh, and you say you are getting a graphical screen with an option to install OpenOffice? Are you mounting the Live CD from Windows?

And, how did you burn the ISO's? With what programs/options, I mean. You can't just burn an ISO like a regular file.

---

### Post by studebakerhawk on 2005-11-02
I burned the file with nero. I havent verified the checksums but I can't imagine it being corrupted because when I mount the file in a virtual drive with alcohol120 (in XP), the disk appears to function normal (with the exception of actually letting me boot from ubuntu) which is what is so puzzling

---

### Post by LeXiee on 2005-11-02
I have the exact same problem!!  I also used Nero to burn the CD!  I also told it that it was going to be a boot cd.

---

### Post by phanboy_iv on 2005-11-02
> I have the exact same problem!! I also used Nero to burn the CD! I also told it that it was going to be a boot cd.

Hum. I'm not too familiar with Nero, but I don't think "boot cd" is the burn option you want. Try to find one called "burn iso image" or something like that. 

> I burned the file with nero. I havent verified the checksums but I can't imagine it being corrupted because when I mount the file in a virtual drive with alcohol120 (in XP), the disk appears to function normal (with the exception of actually letting me boot from ubuntu) which is what is so puzzling

This might be the same problem. If not expressly told to do otherwise, most burning programs just burn the ISO as a file, meaning you can't boot, but the data is still on the disc.

And if that doesn't work, try: 

1. Different CD's (maybe the're bad discs?) 

or 

2.Use a different burning program, making sure to use the "Burn iso image" or equivalent option.

---

### Post by aysiu on 2005-11-02
[QUOTE=phanboy_iv]Hum. I'm not too familiar with Nero, but I don't think "boot cd" is the burn option you want. Try to find one called "burn iso image" or something like that.[/QUOTE] [http://www.wizardskeep.org/mainhall/tutor/neroiso.html](http://www.wizardskeep.org/mainhall/tutor/neroiso.html)

---

### Post by LeXiee on 2005-11-02
I had tried doing a basic CD with just the iso image like you mentionned... same thing :)

I'll keep testing things out!

---

### Post by studebakerhawk on 2005-11-02
just as so I don't have to start another thread- I reburned the image. I can use it successfully on my desktop, but still not on the laptop (which is the main goal). The laptop won't boot off the installer cd. I am currently looking into upgrading the BIOS, but would love some suggestions.

---

### Post by phanboy_iv on 2005-11-03
[QUOTE=studebakerhawk]just as so I don't have to start another thread- I reburned the image. I can use it successfully on my desktop, but still not on the laptop (which is the main goal). The laptop won't boot off the installer cd. I am currently looking into upgrading the BIOS, but would love some suggestions.[/QUOTE]

What brand laptop is it?

Not to annoy you, but are you absolutely sure the laptop is set to boot from CD?
Is there even an option for it in the BIOS? If not, you may have to boot from a floppy, if your laptop has a floppy drive.

The live CD doesn't work either?

Actually, I had a similar problem. Most distro's install CD's wouldn't boot on my new laptop(some kind of issue with pre-2.6 Linux kernals). That's why I switched to Ubuntu. It had the newest kernal. And it worked.

Are you getting any kind of message, or does the laptop just boot into Windows as if nothing had happened? Can you hear the disc spin up before Windows boots?

---

