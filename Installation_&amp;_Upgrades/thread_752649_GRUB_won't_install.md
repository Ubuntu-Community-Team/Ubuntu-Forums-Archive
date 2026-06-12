---
title: "GRUB won't install"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by Jordanwb on 2008-04-11
I'm installing 8.04 onto my laptop. I got to the point where it would install Grub but it keeps saying that it failed. Is there some way to figure out what's going on?

---

### Post by twist2b on 2008-04-11
the partition is prob messed up, like not enough space. Get the GRUB cd and install outside Ubuntu:

[http://www.gnu.org/software/grub/grub-legacy-download.en.html](http://www.gnu.org/software/grub/grub-legacy-download.en.html)

I would go with Legacy I believe. I don't remember though I don't think it matters which you choose.

---

### Post by Jordanwb on 2008-04-11
When I got to the point to set up the partitions I selected "Use entire disk". The laptop has 20GB of space, 768 MB is used for Swap, the rest is for Ext3. I have GParted on a CD. I'll delete the partitions.

---

### Post by Pumalite on 2008-04-11
Are you trying to dual boot with Vista? If so, partitioning has to be done with Vista partitioner. You cannot partition with Ubuntu CD.

---

### Post by warp99 on 2008-04-11
Boot to the install disc. When you get to the section on partitioning your drive choose to manually edit the partition table:

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png)

---

### Post by Jordanwb on 2008-04-11
I'm uisng the Text based installer due to the nature of the Laptop. But I'll try to set up the partitions manually.

---

### Post by warp99 on 2008-04-11
You can also set them up manually with the alternative CD so go ahead and try that.

---

### Post by Pumalite on 2008-04-11
How much memory do you have?

---

### Post by Jordanwb on 2008-04-11
256 Mb. At the menu I selected install, now all I get is the flashing cursor on a black screen.

[Edit] About three installs back I chose to install LILO instead of Grub. I deleted all the partitions on the drive yet Linux is still working. I think Gparted hopped on the fail boat.

[Edit #2] I remembered I have some blank CD-RW's so I'll burn a copy of SealTools for DOS to completly erase the drive.

---

### Post by Pumalite on 2008-04-11
You should try this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
(Alternate)
It's your best bet

---

### Post by warp99 on 2008-04-11
> **Jordanwb said:**
> 256 Mb. At the menu I selected install, now all I get is the flashing cursor on a black screen.

[Edit] About three installs back I chose to install LILO instead of Grub. I deleted all the partitions on the drive yet Linux is still working. I think Gparted hopped on the fail boat.

If it's only grub that's the problem you can get the Super Grub disc and install grub first, then complete the remaining install to the disk since you've already partitioned the drive. You can get the disc here:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Jordanwb on 2008-04-11
First I want to completly erase (Full format) before I do anything else. Know any programs that I can do that? And by full erase I mean I won't find a single 1 on the hard drive.

---

### Post by Pumalite on 2008-04-11
Get Gparted Live CD. Burn to disk and boot from it. It can do the job

---

### Post by warp99 on 2008-04-11
> **Jordanwb said:**
> First I want to completly erase (Full format) before I do anything else. Know any programs that I can do that? And by full erase I mean I won't find a single 1 on the hard drive.

If you boot to a command prompt with the install disk you can use fdisk or cfdisk to wipe the partitions or even make them if you want. Cfdisk does have an easier interface then fdisk. Just type 'man fdisk' or 'man cfdisk' at the prompt on how to use.

---

### Post by Jordanwb on 2008-04-12
> **Pumalite said:**
> Get Gparted Live CD. Burn to disk and boot from it. It can do the job

I've already done that. Gparted only does a quick format, not a full; Maxtor's PowerMax does.

> **warp99 said:**
> If you boot to a command prompt with the install disk you can use fdisk or cfdisk to wipe the partitions or even make them if you want. Cfdisk does have an easier interface then fdisk. Just type 'man fdisk' or 'man cfdisk' at the prompt on how to use.

I got Maxtor's PowerMax for Dos software, put it onto a floppy then burned it onto a cd using Nero's "Create a bootable Cd"

I still can't install Grub.

---

### Post by Pumalite on 2008-04-12
Use DBan and follow with Gparted then:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by warp99 on 2008-04-12
> **Jordanwb said:**
> 

I still can't install Grub.

Did you try the Super Grub Disk?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

This is a not only a Grub recovery/install disk but it's also a diagnostic tool. At least it may give you some clues if you can't install Grub with these tools.

---

### Post by Jordanwb on 2008-04-12
I've already done a full format with Maxtor's PowerMax. So should I try to install Ubuntu first before using SuperGrub?

---

### Post by warp99 on 2008-04-12
No get the Super Grub disk and install Grub first, then complete the rest of the Ubuntu install. Once grub is installed the Ubuntu installer will not prompt you to install Grub again. If it does just skip that part and complete the remaining installation of Ubuntu. We can always build a new menu.lst file with the Grub Super Disk if needed after Ubuntu is on the partition. Got it!

---

### Post by Jordanwb on 2008-04-12
I'm at the partition screen in Ubuntu. There is:

Guided - Resize SCSI
Guided - use entire disk
Guided - use entire disk and set up VLM
Guided - use entire disk and set up encrypted VLM
Manual

[Edit]It's 10 PM Local time. I'll re-re-re-re-restart the installation on day three. :(

I don't think I had enough "re-"'s maybe I need to write a triple nested for loop where each loop runs a thousand times.

---

### Post by Jordanwb on 2008-04-13
> **warp99 said:**
> No get the Super Grub disk and install Grub first, then complete the rest of the Ubuntu install. Once grub is installed the Ubuntu installer will not prompt you to install Grub again. If it does just skip that part and complete the remaining installation of Ubuntu. We can always build a new menu.lst file with the Grub Super Disk if needed after Ubuntu is on the partition. Got it!

Ok I think I figured out what I need to do:

1: Install XP (I need Microsoft Streets and Trips) onto a 7 GB partition
2: Install Ubuntu, when I get the Grub installation failed screen I restart the computer, and stick in SGD
3: Then when SGD loads I...?
4: When after that I stick the Ubuntu disk back in, then how do I get back to where I was?

---

### Post by binxboll on 2008-04-13
The problem is that during installation apt-get accesses network repositories which have been updated with some newer packages. It so happens that these updates require that one package be removed. Apparently removals are not allowed. This causes an error in apt-get. Grub is not installed properly. This causes the whole installation to fail.

I have installed the JeOS beta several times successfully in the past two weeks. But suddenly, installations started failing with an error about grub. After digging I found that disconnecting the ethernet cable after completing dhcp and ntp configuration solved the grub error. I presume that this will be fixed once 8.04 is released. In the meantime, use the cable disconnect workaround so that apt does not see any package updates.

---

### Post by Jordanwb on 2008-04-14
Your theory makes the most sense. I'll try that. Do I even need the ethernet cable plugged in in the first place?

---

### Post by koenn on 2008-04-14
it helps you get throught the "configure nework" step easily (the installer will attempt dhcp and without network cable, it will faill)
once you're past this step (or skip it), and you don't have network, the installer will use just what's available on the CD, which should do just fine. 
so no, you don't really need it.

---

### Post by Jordanwb on 2008-04-14
I didn't plug in the network cable and "Installation Complete". Binxboll you get a "Thanks".

---

### Post by bag123 on 2008-05-02
Thanks from me too - unplugging the cable worked for me too.  I'd been struggling for weeks with this- installing, reinstalling, screwing up the system, reinstalling...

It was a nightmare.  Now, having unplugged the cable, I have a fully installed base system in less than 30 minutes.  Now to the long task of updating it and setting it up how I like it.

Thanks to Binxboll.

Bag123

---

