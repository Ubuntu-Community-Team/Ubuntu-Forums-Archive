---
title: "roll back install"
date: 2017-07-31
forum: Installation &amp; Upgrades
---

### Post by Happy360 on 2017-07-31
Hi all
I was stupid, I wanted to install Ubuntu along side with DeepIn OS. I ended up choosing the wrong drive, and installing Ubuntu on my usb HDD, with the family pics on it. No problem here, all the pics are there on the other partition created by the Ubuntu install wizard...

I have now installed Ubuntu correctly along side DeepIn OS, but how do I get rid of the installation on the usb hdd in a correct way - I guess that I can't just simply delete it, no??

I want to "roll it back", can I do this somehow without deleting or having to move ALL the family pics?

Kind regards

---

### Post by yancek on 2017-07-31
So you have two install of Ubuntu and you want to remove one of them, is that correct?  You could run the command:  sudo fdisk -l(lower case letter L in command) or gdisk -l and post the output here indicating which partition you want to remove.  If you have the Ubuntu install on a separate partition from your pictures and other data and nothing else on it you could just format it and then use it for other data.  Better to post more details before proceeding.

---

### Post by vocx on 2017-07-31
> **Happy360 said:**
> Hi all
I was stupid, I wanted to install Ubuntu along side with DeepIn OS. I ended up choosing the wrong drive, and installing Ubuntu on my usb HDD, with the family pics on it. No problem here, all the pics are there on the other partition created by the Ubuntu install wizard...

I have now installed Ubuntu correctly along side DeepIn OS, but how do I get rid of the installation on the usb hdd in a correct way -** I guess that I can't just simply delete it, no??**

I want to "roll it back", can I do this somehow without deleting or having to move ALL the family pics?

Kind regards
Actually, yes, yes you can simply delete the Ubuntu installation in the external hard drive. But to answer your question, I don't think you can simply "roll back" to how it was in the past.

Basically, you had one drive, that drive became partitioned in two partitions, one with Ubuntu, and the second with your pictures.
```

# External hard drive
sda
    sda1/images, 500 GB
    sda2/ubuntu, 500 GB

```

If you remove (delete) the Ubuntu partition, it will just leave that space unallocated; your partition with the images will not grow to occupy the space, but you can expand it manually using a graphical program such as "gparted".
```

# Delete partition
sda
    sda1/images, 500 GB
    [unallocated space 500 GB]

```
```

# Expand partition to occupy the entire space of the drive
sda
    sda1/images, 1000 GB

```

> **yancek said:**
> So you have two install of Ubuntu and you want to remove one of them, is that correct?  You could run the command:  sudo fdisk -l(lower case letter L in command) or gdisk -l and post the output here indicating which partition you want to remove.  If you have the Ubuntu install on a separate partition from your pictures and other data and nothing else on it you could just format it and then use it for other data.  Better to post more details before proceeding.
Correct. Double check before actually deleting partitions.

Also, check that you can boot the computer normally without the USB drive connected. The boot loader should be installed in your fixed drive, so you don't depend on the USB external drive.

See this other thread: [https://ubuntuforums.org/showthread.php?t=2367083&highlight=external+hard+drive+boot+loader](https://ubuntuforums.org/showthread.php?t=2367083&highlight=external+hard+drive+boot+loader)
The user installed Ubuntu in an external drive, and later just wanted to delete it. There is no problem, just make sure you can actually boot the system before doing it.

---

### Post by Happy360 on 2017-07-31
Thank you for all your help

I have now deleted the Ubuntu install on the usb hdd, and deleted the partition and made a new partition - so this was a success, pics are still there...
I have now the GRUB error... - (error: no such device XXXXXXXXXX), and then GRUB rescue?!?

I have tried different guides for repairing boot sequence, boot repair tool etc but with no luck. Strange thing is, if I enter BIOS when rebooting and exit's again without save, it boots up correctly??

---

### Post by vocx on 2017-07-31
> **Happy360 said:**
> Thank you for all your help

I have now deleted the Ubuntu install on the usb hdd, and deleted the partition and made a new partition - so this was a success, pics are still there...
I have now the GRUB error... - (error: no such device XXXXXXXXXX), and then GRUB rescue?!?

I have tried different guides for repairing boot sequence, boot repair tool etc but with no luck. Strange thing is, if I enter BIOS when rebooting and exit's again without save, it boots up correctly??
You should be more specific on what guides and steps you have already tried, so that people trying to help you know.

This guide seems pretty good [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Since, I haven't experienced these problems, I will just suggest you check your BIOS, and uncheck "fast boot", and "secure boot" options. These seem to cause issues when changing partitions in a hard drive. Other than that, I can just suggest reinstalling Grub using a Live CD, so it forgets the external hard drive partition, and picks up your installed Ubuntu and DeepIn OS partitions.

---

### Post by Happy360 on 2017-08-01
Thank you vocx, I will try that...

Thank you for helping me ;-)

---

