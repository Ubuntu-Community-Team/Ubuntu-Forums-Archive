---
title: "Installation Mess up"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by sic89 on 2008-10-10
I tried to install Ubuntu 8.04 onto a 80 gig external drive. During installation, I was paying attention to where the main files were being installed, so not to mess up my other hard drive. But heres where the problems lie. I got "Error 21" when booting up, then after a few tests, I realized that I might have installed grub on my Windows hard drive and not the second Ubuntu drive. My files on my Windows drive are still where they need to be, but is there a way I can erase grub without harming my windows files?

I'm somewhat new to Ubuntu.

---

### Post by sic89 on 2008-10-10
Would fixing my mbr with the windows disk work? or should I try something else?

---

### Post by tea for one on 2008-10-10
When booting up, were you trying to select your Windows OS on your internal HDD or Ubuntu on the external HDD?

Is your external HDD plugged in?

I have installed Ubuntu on an external HDD wth Windows on an internal HDD and I have to keep the external HDD plugged in because that is where the Grub resides.

Both operating systems should be accessible.

---

### Post by sic89 on 2008-10-10
> **tea for one said:**
> When booting up, were you trying to select your Windows OS on your internal HDD or Ubuntu on the external HDD?

Is your external HDD plugged in?

I have installed Ubuntu on an external HDD wth Windows on an internal HDD and I have to keep the external HDD plugged in because that is where the Grub resides.

Both operating systems should be accessible.

I was trying to get on the internal with Windows on it. Got welcomed with the Grub Loading and Error 21 messages, even with the external with Ubuntu disconnected.

During installation, I didn't notice on the advanced tab on finalization, that grub was going to be installed on internal and not external.

---

### Post by tea for one on 2008-10-10
I suspect that your Grub is on the external HDD together with the Ubuntu OS. Power down your PC, plug in your external HDD, power on and try and select an OS. Then report any error messages.

Correct me if I am mistaken error 21 is "Partition not found" or similar expression.

---

### Post by sic89 on 2008-10-10
After the first time, I turned my external into an internal by installing it to an IDE cable. Went through all the os selections and none of them worked.

---

### Post by tea for one on 2008-10-10
I am unfamiliar with the process of swapping HDDs from internal to external and vice versa. I only run a notebook with one external HDD and therefore my drives are static.

There is a thread which will help you find and reinstall your Grub, I have used it successfully four or five times when I have not been paying complete attention during installation. I hope it helps.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caljohnsmith on 2008-10-10
> **sic89 said:**
> I tried to install Ubuntu 8.04 onto a 80 gig external drive. During installation, I was paying attention to where the main files were being installed, so not to mess up my other hard drive. But heres where the problems lie. I got "Error 21" when booting up, then after a few tests, I realized that I might have installed grub on my Windows hard drive and not the second Ubuntu drive. My files on my Windows drive are still where they need to be, but is there a way I can erase grub without harming my windows files?

I'm somewhat new to Ubuntu.
Yes, probably Grub was installed to the MBR (Master Boot Record) of your internal drive, and yet Grub uses your external HDD for its system files. When you get that error 21 is it before you get a Grub menu or after you get the Grub menu and select an OS? And are you getting that error with the external drive connected or disconnected?

If you can boot your Ubuntu Live CD, open a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
Then run the following command on whichever are your drives that fdisk listed, like sda, sdb, or whichever they are:
```
sudo dd if=/dev/[COLOR="Blue"]sda[/COLOR] bs=512 count=1 2>/dev/null | strings | grep -i grub
```
And replace "sda" above with your drives, and post the output. That will give us a better picture of your setup, and we can work from there.

---

