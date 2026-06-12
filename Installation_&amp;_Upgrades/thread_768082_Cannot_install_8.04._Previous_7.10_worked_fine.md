---
title: "Cannot install 8.04. Previous 7.10 worked fine"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by neyuru on 2008-04-26
Unlike it's previous version (7.10), hardy's Live CD doesn't have a text based installation option when booted from CD. I don't know if this is actually meant to be this way or not. Im stuck with the normal install or by first "trying" Ubuntu and then selecting the install icon on the desktop.

Either these two ways, when I select the "Guided partitioning option" (step 4 out of 7 of the install process) the interface transports me to the "Who are you?" step right away... I don't have the opportunity to "Resize IDE1 master, partition #1 (hda1) and use freed space" as in the Gutsy version. 

If I try the manual partitioning method, I must leave the partitioning as it is (aka "Don't use this partition") or I must format all of the space in the HDD. Either way, (suppose I try to format all the partition) and when I finish the step 5 of 7 (the "Who are you" step) the installer skips righ to the final step (7 of 7) Where did the step 6 go???

Any help would be appreciated, I would like to dual boot both Ubuntu and WinXP. The ISO and CD integrity are verified.

---

### Post by Partyboi2 on 2008-04-26
> Unlike it's previous version (7.10), hardy's Live CD doesn't have a text based installation option when booted from CD. I don't know if this is actually meant to be this way or not. Im stuck with the normal install or by first "trying" Ubuntu and then selecting the install icon on the desktop. If you are wanting to the text base installler, use the alternate cd.
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by kai60 on 2008-04-26
Hi mate,

you could always try to use Gparted on the Live CD and then partition your harddisk from there. I always repartition using that as it gives me a good level of control. 

I would then just install Ubuntu into the space that you have created for it and make sure that you set it as the / mount point and all should be well for you.

Cheers and good luck

---

### Post by neyuru on 2008-04-26
Thanks guys,

I've used gparted to try to make some space on my ntfs disk but there's something weird about it: it has some form of locking mechanism because Gparted can't resize the primary partition: (where windows XP is) the disk is unsizable: it has 40 GB of minimum space and 40 GB of maximum space. Can you help me here? I thought Gparted would easily resize my HDD but I didn't count on this.

thanks!

---

### Post by neyuru on 2008-04-26
There appears to be some kind of warning sign in GPARTED next to the name of the hard disk hda1 that is something like a black bordered - yellow triangle with an exclamation point in it.... What does it mean? Maybe this has something to do with me can't resizing the hard disk.

---

### Post by Partyboi2 on 2008-04-26
Make sure that the windows partition is umounted first before working on it and that windows was shut down cleanly.

---

### Post by neyuru on 2008-04-27
> **Partyboi2 said:**
> Make sure that the windows partition is umounted first before working on it and that windows was shut down cleanly.

How do I unmount the partition? I checked some information GPARTED gave me about my HD and it said something like a Bad Sector... because of this GPARTED could not resize the partition. Gparted prompted me to do a Checkdisk to repair posible bad sectors (if any) I did a off-line Checkdisk 3 times but with no change. Windows seems to work fine. The Live CD is booting before the HD so I think Windows is shut down cleanly... if not.. How do I do this?

thanks

---

