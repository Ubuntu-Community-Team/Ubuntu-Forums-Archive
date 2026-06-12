---
title: "Can I install a dual-boot without burning a CD?"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by dark.developer on 2006-11-01
Hi to EVERYONE,
and Hats Off to "Ubuntu Community",

This is my first post!

Actually I want to dual boot Ubuntu and WindowsXP with conditions:
1) without destroying my previously installed WindowsXP.
2) _installing Ubuntu directly from hard-disk._:KS 

Is it really possible somebody plz answer.

Thanks in advance.
Bye for now.

"Live and Let Live!!!"

---

### Post by 23meg on 2006-11-01
> 1) without destroying my previously installed WindowsXP.[You can]("http://users.bigpond.net.au/hermanzone//").
> 2) installing Ubuntu directly from hard-disk. As far as I know you can't with a single machine. You have to burn the image to a CD and boot with it, or do a network install.

---

### Post by aysiu on 2006-11-01
Ubuntu shouldn't destroy your Windows XP installation if you know what you're doing, but you should **always back up your data** before you install a new operating system.

A couple of dual boot guides you might find handy:

**Desktop CD**:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

**Alternate CD**:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by dark.developer on 2006-11-02
Hi,
Thanks for the response,
Gee, many geeks out there. But I think I am being mis-interpreted.
Let me tell u this way I just don't want burn a new CD for every new "Ubuntu" in the market. I just want to install it directly for the disk image from the hard disk.

?? Waiting for my ques to be correctly interpreted!

Bye,
Thanks Anyway for the response!

"Live and Let Live!!!":mrgreen:

---

### Post by aysiu on 2006-11-02
You don't have to burn a new CD for every new Ubuntu in the market.

Burn it once for the current version. Once you have the current version installed, you can upgrade to newer releases over the internet without having to reinstall.

---

### Post by jgcamp99 on 2006-11-02
> **dark.developer said:**
> Hi,
Thanks for the response,
Gee, many geeks out there. But I think I am being mis-interpreted.
Let me tell u this way I just don't want burn a new CD for every new "Ubuntu" in the market. I just want to install it directly for the disk image from the hard disk.

?? Waiting for my ques to be correctly interpreted!

Bye,
Thanks Anyway for the response!

"Live and Let Live!!!":mrgreen:

I know where you're coming from on this one. You want to download the iso image and install without having to burn a cdr. WTH, if you downloaded the iso, what would it take to burn that to cdr and have a copy ? The cdr's I burned it on are 15 cents and a few minutes of your time.

I attempted an upgrade of Dapper the way I interpret that you are interested in installing Edgy. I had the iso image on a usb drive, mounted the drive and then tried to incorporate it into the upgrade process, it still wound up downloading 700+ MB from the Edgy repositories and in the end fglrx was deleted and all I could do was a dos looking command line login with no gui. I went ahead and did a clean install and got this system back to where I had Dapper, it took a couple of days, the  same amount of time it took me to fail at the upgrade. I'm not complaining, just relaying my experience. I burned the first Edgy cdr and that wouldn't boot by itself, figures, I did it with a G4 867 Apple Powerbook. The next time I burned the cdr, it was with Nero in Windows XP, it booted fine from the optical drive.

My suggestion, when it's at worst a $ 1 to spend on burning a cdr, spend it, that way you have something that will install as a live cdrom and you can at least do some recovery if your install/upgrade screws something up. It's a backup plan.

---

### Post by dark.developer on 2006-11-03
Post failed to follow forum guidelines for conduct.  Remember always be considerate of others, even if they upset you.

---

### Post by PrinceArithon on 2006-11-03
Well, I don't know about all of you, but I had a really easy time dual booting my system.  I'll kinda give a step by step.

First I reformatted Windows (after all you need to reformat it every 6 months anyway right??)

When I reformatted it I gave windows a 60 gigs partition and Linux 40 gigs partition (I have a 100 gig harddrive for my laptop, and I had no idea I was going to convert to Linux 90% of the way)

Then from there I installed windows all the way.  Then what I did was I put in Ubuntu, let the live CD boot up, and then started to install.  From there as I was asked to choose where I wanted to put Ubuntu I chose to let it take the largest amount of free available space.

From there it installed and the GRUB took over my booting options.  Life has been nice since.

So this is just my suggestion on how to do it, it feels the safest for me.

---

### Post by DaveB on 2006-11-03
I wonder if the question arises from windoze' capability to install from a "data" partition? For example win98 can be installed to partition C: on an HD from another partition D: IF the win98 folder was somehow copied onto D: earlier. 

The contents of a downloaded iso file can be viewed in GNU/Linux by something like 

mount -t iso9660 -o ro,loop=/dev/loop0 someDownloaded.iso /cdrom

But I don't know how to proceed from there; I would be interested to find out if Ubuntu / Linux can do this trick.

Thanks.

---

### Post by raja on 2006-11-03
Hi,
I have a thinkpad without an optical drive where I changed from XP to dual booting with XP and Ubuntu. After resizing the NTFS partition with system rescue cd booted off a usb stick (supposed to be more reliable than resizing it during Ubuntu installation), I followed this [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) to install ubuntu over the net with the installer booted from grub for NT within windows. 
Hope that helps.

---

