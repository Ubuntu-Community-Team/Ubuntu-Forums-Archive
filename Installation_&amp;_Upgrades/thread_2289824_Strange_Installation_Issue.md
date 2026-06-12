---
title: "Strange Installation Issue"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by sougata2 on 2015-08-07
I have an Asus 1013E running on Win 7 64 bit Ultimate. I am trying to Install Ubuntu for the first time. I tried running the installer but it could not detect Windows. I consulted previous posts. I have now assessed that:

1. My windows is booting on** legacy** mode but I have **UEFI** hardware

2. Boot partition is the 100 MB system partition

3. I have two primary NTFS partitions C: and D: and a 30 GB RAW space which I had curved out of my second physical partition for Ubuntu via Windows MiniTool utility

4. Gparted can detect all the NTFS partitions and the RAW space yet the installer is not letting me install Ubuntu along side WIndows

5. The installer is trying to enforce 'UEFI' installation when I try to install it with the threat that I won't be able to boot into any other OS using the legacy option. Hence I did not pursue it further

I do not want to format my hard drive and start from scratch. I require dual booting. I am afraid if I try the "something else" option and install manually by partitioning the 30 GB space, I will lose my ability to boot into Windows.

I am running Ubuntu 15 Live using a flash drive.

Solution requested.

---

### Post by grahammechanical on 2015-08-07
I do not understand what you mean by RAW space. Is that somekind of disk format type? Or do you mean free space or unallocated space?

---

### Post by sougata2 on 2015-08-07
Gparted is reporting it as unknown as it has not been formatted yet.

---

### Post by sougata2 on 2015-08-07
Also, please note that the 100 MB partition has been correctly flagged as** boot** by gparted.

---

### Post by yancek on 2015-08-07
The fact that your hardware is capable of using UEFI doesn't mean you have to use it.  If your windows 7 is using MBR, which it seems it is because of the 100MB partition which is likely a boot partition, you should be able to install Ubuntu in MBR also.  I'm not sure this option will be available if you try to use the auto option, install Alongside.  Also, you have no control over what is happening.  You do with the Something Else option which is basically a manual install.  The possibility of being unable to boot windows after installing with the Alongside method is much higher than using the Something Else option.  If you have no experience installing Ubuntu, try the extremely detailed tutorial below.  There is a step by step guide down the page on dual-booting as well as a section on partitioning.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by sougata2 on 2015-08-07
Thank you. Will take the plunge and do manual install. I just want to know whether it will be possible to rectify the situation without losing data in case I don't get to boot into Windows after installing it. Dual boot is a must for me.

---

### Post by coffeecat on 2015-08-07
> **sougata2 said:**
> 
5. The installer is trying to enforce 'UEFI' installation when I try to install it with the threat that I won't be able to boot into any other OS using the legacy option.

That sounds as though you are inadvertently booting the live USB/CD, or whatever you are using, in UEFI mode, even though Windows is booting in legacy mode. You can tell the difference when first booting up the live session. In UEFI mode, it displays a white on black GRUB menu at first. In legacy mode, you see a purple screen with two icons - a stick figure and keyboard - at the bottom of the page immediately after it starts booting.

Have a look in your UEFI BIOS. You should be able to decide whether to boot the live session in legacy or UEFI mode. UEFI BIOS's vary from make to make, so I can't be more specific.

By the way, I've removed the mass of (invisible) base64 code from your first post. You triggered a Firefox bug by dragging and dropping an image into the message editor. Vbulletin doesn't support that. If you wish to add an image to your post, you can use the manage attachments button below the advanced editor to upload your image and add a thumbnail to your post.

---

### Post by sougata2 on 2015-08-07
Sorry about the image thingy. Yes, I was trying to paste an image of gparted. I did get a white on black menu asking me to choose between install/live/check disc etc. I thought the "grub" menu came after a successful install. WIll look into my bios and force it to run in legacy mode. Let's see.

---

### Post by sougata2 on 2015-08-07
Yes, it is the grub screen alright (noticed the title on top). My BIOS apparently has no option to force boot into legacy. Noticed that my flash drive is coming up in to boot order as EFI. Any way to by pass this? Read some where that deleting the EFI folder in the flash drive may help but I have tried that. Didn't work. WIndows got loaded up instead as if the flash drive did not exist!

---

