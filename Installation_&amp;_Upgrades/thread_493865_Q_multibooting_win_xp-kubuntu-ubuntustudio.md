---
title: "Q: multibooting win xp-kubuntu-ubuntustudio"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by octaedro7 on 2007-07-06
Hi there,
Currently I'm running win xp and kubuntu in dual boot, using grub (installed on MBR), both placed on the same fisical sata2 HD.  I wan't to try ubuntu studio with the realtime kernel but  installed on an external esata2 HD inside a coolermaster box.
How can I have an ubuntustudio entry on the existent grub, is it automatically?
Can I share the same /home partition with my Kubuntu?

Here's the scenario:

1st sata2 HD, directly plugged on motherboard's #1 sata connector, 7 partitions in the following order:

1) win xp-ntfs
2) fat 32
3) ntfs,
4) ntfs,
5) Kubuntu swap
6) Kubuntu ext3 root
7) Kubuntu ext3 home

2nd esata2 HD, plugged to motherboard's #2 sata connector through an esata bracket supplied with the box, 5 partitions:

1) Ntfs
2) Ntfs
3) Ntfs
4) Ntfs
6) ext3 (ubuntu studio root, this is where I would want it to be)

The idea is having not to change the boot order on BIOS every time I wan't to load Ubuntu Studio.
I'll appreciate any help because I don't want to mess things up.
Sorry for this long post and for my bad english.

---

### Post by Vajra Vrtti on 2007-07-06
That is quite similar to what I do in my system, except that I have 3 Linux partitions. It is a little tricky but not really difficult, once you understand what you are doing. I will describe the process using 2 Ubuntu partitions, since XP does not interfere and  it is the same for as may Ubuntus you want.

Let's begin at the point where you have Ubuntu installed in one partition and another partition is available to receive Studio. Also, I will consider the first Ubuntu the main one, that is, the one that I always want to boot the system.

First, just do a normal install of Studio into its own partition. If everything is OK, the system will now boot using the grub installed in the Studio partition. The new grub menu will have the main entries pointing to the kernel in the Studio partition and, under *Other Systems,* there will be entries to boot the previously existing Ubuntu and Windows XP. All partitions should be accessible from Studio and all systems should be bootable.

If you now boot the old Ubuntu you will have an error trying to mount the Studio root partition. That is because the install process formats the partition and changes its UUID, which is used in fstab to mount it. to fix that, do as follows in Studio:
[LIST]
[*]Edit the Studio's /etc/fstab.
[*]Locate the entry for the root and copy its UUID to the clipboard.
[*]Edit the Ubuntu's fstab (/media/*volumename*/etc/fstab).
[*]Locate the Studio's volume and corrrect its UUID with the one copied above.
[*]Save Ubuntu's fstab.
[/LIST]
Now, if you boot Ubuntu you will have access to the Studio's volume.

The next step is to make the system boot using Ubunt's grub again. To do that, follow [these instructions]("http://ubuntuforums.org/showthread.php?t=224351").

However, Ubuntu's grub menu.lst does not know about Studio. To fix that you have to edit /boot/grub/menu.lst in both systems and manualy copy the entry about Studio (the main one) to the *Other Systems* section of Ubuntu's menu.lst, that is, put it just above or bellow the XP entry.

And that's it. At this point you have a system that will bot using the previous installed grub and with the option to boot Ubuntu, Studio and XP.

You just have to be concerned about Studio's kernel updates. This will update the menu.lst in Studio's partition and not the one you will be using. The updated entry have to be copied again from the menu.lst in Studio to the one in Ubuntu.

I hope i could make it clear.

Good luck.

---

### Post by Vajra Vrtti on 2007-07-06
By the away, if anyone knows an easier way to do it, please post.

---

### Post by dabl on 2007-07-06
That's probably about as easy as it gets, Vajra.  Personally, I follow the theory of "Last Linux Wins".  In other words, you know that a new boot menu will be written by the last Linux that you install, and it will set itself as the top/default kernel to boot on the menu.  So if you sequence the installations in a pre-planned fashion, you can end up with the menu looking and working the way you want, without a lot of of manual editing.  :popcorn:

---

### Post by octaedro7 on 2007-07-06
thanks dabl, i'm about to install US now.
Still two doubts:
If I install Ubuntu studio in my external HD and my BIOS is configured to boot first from the internal HD, will US's grub appear at boot anyway?
Are there  some significant differences between US with RT kernel and my already customized to the bone Kubuntu also with RT kernel, in terms of audio and video production and stability?

Thanks again

---

### Post by dabl on 2007-07-06
Speaking from zero experience with your setup, I will speculate that there's no difference with an external SATA drive, assuming that it is "seen" during the installation process as just another hard drive.  I'm assuming you don't have it formatted as NTFS or anything real specialized with its configuration.

Are you putting Grub on the internal hard drive's Master Boot Record?  If you install US first, make sure you point the Grub placement to the drive where you actually want it.  Then stick with that same MBR for your subsequent Grub locations. The low-latency and RT kernel stuff is irrelevant to the boot menu placement.  BTW, I've had best luck with the "Alternate Install" CD images.

I just noticed you're only showing 1 partition for US.  Isn't it a full Linux system -- doesn't it need /root, /{swap}, and /home partitions same as Kubuntu? If so, you can use the same /{swap} partition as you do for Kubuntu (#5 on disk 1), but you still need two separate partitions for / and /home.

---

### Post by Vajra Vrtti on 2007-07-06
> If I install Ubuntu studio in my external HD and my BIOS is configured to boot first from the internal HD, will US's grub appear at boot anyway?

Your BIOS boot from the first HD and grub will take care of the rest. In my case, I boot from my primary SATA HD but the Ubuntu partitions are on the secondary one.

> Can I share the same /home partition with my Kubuntu?

You can, but I don't think it's a good idea. The main advantage would be to share application settings, so that you don't have to configure the same thing twice. The main advantage would also be to share application settings so that, if you mess one the you mess both. I've already made my system unbootable doing that.

That said, I keep my personal data in a different partition, shared by both systems, isolated from system installs. My /home folder is only used for application settings.

---

### Post by dabl on 2007-07-06
> **Vajra Vrtti said:**
>  My /home folder is only used for application settings.

That is an interesting approach!  I guess I do a similar thing -- in /home, there are 4 folders: /Docs, /Music, /Images, and /Downloads.  All my data are in those folders (there is a hierarchy of data within each folder).  So in the top /home folder the only files are hidden files and configuration settings.

:)

---

### Post by octaedro7 on 2007-07-06
Thank you all, valuable information thrown here!
two last questions (did I already say that?)
Can I share swap partition even if they're on different HD?
Do you know an easy method or software to compile a DVD with all Ubuntu flavors, that is bootable and let me choose which one I want to instal? So far I'm burning a rewritable DVD each time I want to try one and I't will be lovely to have them all toghether.

---

### Post by dabl on 2007-07-06
> **octaedro7 said:**
> 
Can I share swap partition even if they're on different HD?

YES

> 
Do you know an easy method or software to compile a DVD with all Ubuntu flavors, that is bootable and let me choose which one I want to instal? So far I'm burning a rewritable DVD each time I want to try one and I't will be lovely to have them all together.

NO.

But, I use CDs -- they're way cheaper!  :popcorn:

---

