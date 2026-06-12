---
title: "How to create a Windows 7 boot disc from a pre-installed PC?"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by coober85 on 2011-05-05
Hi there, 

  I have a Lenovo laptop with Windows 7 pre-installed. I would like to dual boot Win 7 and Ubuntu or Linux Mint.

  In my old laptop I had an OEM Win XP disc that I bought specifically for dual boot purposes (didn't want the pre-installed vista). This only has a one PC usage though unfortunately.

 Can anyone give me straight-forward directions on how to make a windows 7 boot disk? I made a RECOVERY disk already, but I don't think that will work as a boot disk right? Particularly if I completely wipe out or swap out the HDD (which I might do).

fyi: I NEED Win7 for a few special programs for my school. WINE will  not work and VirtualBox puts to much strain on my computer.

Thanks for your response!

---

### Post by satanselbow on 2011-05-05
It is not possible to create a W7 "clean setup" disc from an existing installation.

A couple of suggestions for you:

1) Create an image of your existing setup using something like Ghost or EASUS Backup (which is freeware so gets my vote). Ensure you backup and delete as much data (music / video) before you create the image to keep the filesize down. On a relatively new W7 installation and with compression you should be able to keep it to 1 DVD, check the backup integrity thoroughly and redo if necessary - burn a few extra copies for security and treat the with the care you would afford you 1st born child.


2) The more suspect though usually more useful way is to "find" ;) an ISO of an original W7 DVD and use the key stickered on the back of you machine to reinstall from there if you need to. Just enure you find an ISO that matches the language and preferably the  OEM of your original machine (not essential but you could potential end up with different branding) and that you only try and install the same version ie Home Prem / Business if the worst comes to the worst.

Good Luck ;)

---

### Post by coober85 on 2011-05-05
> **satanselbow said:**
> It is not possible to create a W7 "clean setup" disc from an existing installation.

A couple of suggestions for you:

1) Create an image of your existing setup using something like Ghost or EASUS Backup (which is freeware so gets my vote). Ensure you backup and delete as much data (music / video) before you create the image to keep the filesize down. On a relatively new W7 installation and with compression you should be able to keep it to 1 DVD, check the backup integrity thoroughly and redo if necessary - burn a few extra copies for security and treat the with the care you would afford you 1st born child.


2) The more suspect though usually more useful way is to "find" ;) an ISO of an original W7 DVD and use the key stickered on the back of you machine to reinstall from there if you need to. Just enure you find an ISO that matches the language and preferably the  OEM of your original machine (not essential but you could potential end up with different branding) and that you only try and install the same version ie Home Prem / Business if the worst comes to the worst.

Good Luck ;)

Thanks so much for your quick reply! I think I'd go with option 1. I've heard that you used to be able to call your manufacturer and order a Disk... is this still doable(for free?)?

 I've been trying to slim everything down and haven't put much on my system 'cept for programs like Libre Office and FoxIt Reader... yet my C Drive is still almost 40Gb (no music or videos)! I guess I will delete all of the extra Lenovo ThinkPad Software, and ANYTHING that I can safely dispose of,  but even at that- I don't know if it will be able to compress to a DVD. has anyone done this and if so, could they tell me how low I need to go?

Just to be clear though... I can wipe the hard drive, Stick this DVD image in and put Windows back on my comp (maybe with the help of Linux)?

---

### Post by coffeecat on 2011-05-05
> **coober85 said:**
> I made a RECOVERY disk already, but I don't think that will work as a boot disk right? Particularly if I completely wipe out or swap out the HDD (which I might do).

One or several disks, and CD or DVD? And was the utility you used to create the disk(s) a Lenovo one or part of Windows7? Because if you used the functionality built into Windows 7, you would have ended up with a repair CD which only has some repair utilities on it.

I have no experience of Lenovo but most manufacturers provide a utility to create a set of DVDs from the (usually hidden) recovery partition. These are bootable and are used to restore Windows to its factory condition - useful if you want to change the HD. They vary in functionality. On my Sony laptop, I get a lot of flexibility with the restore DVDs. I can vary the size of the C: partition, add a D: partition and decide whether or not to include a recovery partition. With my Acer laptop, it's much more basic. One size fits all and no option to recreate the recovery partition.

Also, a +1 to satanselbow's suggestion to use imaging software. I use that in addition to making sure I have made a set of recovery DVDs. Double-insurance. Here's another good imaging application, proprietary but with a perfectly good free edition:

[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

---

### Post by satanselbow on 2011-05-05
Hindsight being a beautiful thing - stating that you would get a W7 image on 1 DVD was somewhat of an under estimate ;)

Is the 40GB all used space? I have a full CS5 installation on my W7 and it does not weigh in that heavy! You may be looking at the size of the partition rather than the disc space used ;) Using a tool such as EASUS Todo Backup would create a backup at the same size as **used** disc space or smaller with compression.

You would also need a boot disc (CD) to restore the backup but that can be created from within EASUS and is very flexible as to what and where you restore you OS.

The biggest problem - as Coffeecat says - is that OEM equipped W7 restore solutions are generally pretty variable, aggressive and indescriminate as to how they restore and frequently wipe an entire harddrive (including any ubuntu/linux installs on same disc).

You may want to think about getting an HDD just to store you W7 backup on - smaller (ie sub 100GB) are about half the cost of a W7 installation disc ;)

The biggest advantage of an original W7 DVD over image software created backup is that it will not be locked to your current specific hardware - any image will only be good for restoring on the same machine. It would not be a problem to change/upgrade the HDD but expecting it to work on a change of motherboard/cpu would be out of the question.

Hope that clarifies a few things ;) I personally think it is quick scandalous that OEM no longer supply original Windows OS media as standard or have the cheek to charge for it as an extra.

---

