---
title: "Can I upgrade to Hardy Heron from CD?"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by ogost on 2008-04-24
Can I just ask a tiny question? Is it possible to upgrade from a downloaded and properly burned Ubuntu Hardy Heron CD? Or upgrading is only possible through the update-manager?

---

### Post by Ub1476 on 2008-04-24
I believe you can upgrade to Hardy if you use the alternate CD.

---

### Post by Patsoe on 2008-04-24
see [http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

> Use this method if the system being upgraded is not connected to the Internet.

   1. Download and burn the alternate installation CD.
   2. Insert it into your CD-ROM drive.
   3. A dialog will be displayed offering you the opportunity to upgrade using that CD.
   4.Follow the on-screen instructions.

If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2:

gksu "sh /cdrom/cdromupgrade"

Or in Kubuntu run the following command using Alt+F2:

kdesu "sh /cdrom/cdromupgrade"


---

### Post by ogost on 2008-04-24
Thanks, guys! I'm off to download the alternate CD :)

---

### Post by Aikon- on 2008-04-24
> **Patsoe said:**
> see [http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](http://www.ubuntu.com/getubuntu/upgrading#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

Does one necessarily have to burn the image to disc? Or can you just mount the ISO and upgrade from there?

---

### Post by CarpKing on 2008-04-24
> **Aikon- said:**
> Does one necessarily have to burn the image to disc? Or can you just mount the ISO and upgrade from there?

I've never heard of doing this, but I can't imagine why it wouldn't work.  Make sure you back important files up first.

---

### Post by zvacet on 2008-04-24
@ **Aikon-**

You can try [this.]("http://ubuntuforums.org/showthread.php?t=743943&highlight=iso")

---

### Post by daverave999 on 2008-04-24
So is it not possible from the Desktop CD?

---

### Post by forkd on 2008-04-24
> **CarpKing said:**
> I've never heard of doing this, but I can't imagine why it wouldn't work.  Make sure you back important files up first.


you can mount the image but I decided to burn because I FedEx the disks to my step-father.  While he is computer savy, it is a lot easier to overnight the disks to him than to explain how to mount an iso (which begins with the conversation of what an iso is) over the phone.

---

### Post by ssam on 2008-04-24
> **daverave999 said:**
> So is it not possible from the Desktop CD?

the desktop cd does not contain the package files. it contains a disk image with all the packages already installed on to it.

the alternate cd installer works by installing all the packages one by one. the desktop cd installer works by copying the image of an installed system onto your disk.

however, you can get the desktop installer to do a clean install without deleting your home folder. so you get advantages of a clean install, and advantage of not having to copy your files back afterawards. you still should back up before you install, just incase.

---

### Post by Pumalite on 2008-04-24
> **Aikon- said:**
> Does one necessarily have to burn the image to disc? Or can you just mount the ISO and upgrade from there?

You can try this:
[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by ptcbus on 2008-04-24
Yes you can ugrade using CD. But have to use an alternate setup CD.
I just upgraded and have listed all the steps here: [http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/]("http://ptcbus.wordpress.com/2008/06/10/upgrading-from-ubuntu-710-gutsy-gibbon-to-ubuntu-804-hardy-heron/")

---

### Post by ogost on 2008-04-26
Thanks for the help guys! I've upgraded with the alternate CD, now I'm under Hardy Heron :) just need to update the video driver, and i'll be ok :)

---

### Post by Ajaxus on 2008-04-26
I downloaded the AMD64 Server iso (not the alternate cd) and after burning to CD it offered me the option to upgrade. I chose that and saw it through. 

On restart I lost my nvidia driver setting, but I could reset that, using the Conifg. option. Then on loading I had only the 640 x 480 resolution and no wireless connection.

Any ideas on 
1. Resetting the Screen Res; and
2. Reconnecting to WLAN?

Thnks.

---

