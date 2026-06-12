---
title: "risk of windows installation"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by davetheman on 2006-07-21
I've tried Ubuntu on the live cd and I like what I saw. Now, I am interested in installing it on my computer. My question is, How do I do it without risking my Windows installation? On my computer, I have 3 partitons that were included with my computer. One with Windows itself on it, a bigger empty partition, and a hidden partiton for the restore utility. The file system is NTFS.

---

### Post by K.Mandla on 2006-07-22
There's a very good guide here. ...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

In short, you need to resize your partitions to make space for Ubuntu. In my experience, it's easier to leave the empty space unpartitioned and let the automated partitioning system guide you. When you have more experience with partitions and installing, you'll be more comfortable drawing them how you like.

Good luck!

---

### Post by zxee on 2006-07-22
Do you have the install cd? I only ask because I have seen posts where there have been problems installing from the live cd although generally there shouldn't be a problem.
If you have a empty partition it makes sense to use that. Depending how large it is you can resize it and keep some of the space for something else. Be sure to back up personal files in windows because you never know. If all goes well, which is the majority of the time grub-the bootloader will set up your windows install so that you can dual boot.

---

### Post by davetheman on 2006-07-22
I have the latest version of Ubuntu, it has the live cd and the installer combined. How should I resize my partitions? Is it possible to resize one of the partitions?

---

### Post by IYY on 2006-07-22
If you follow the steps provided above, you should be alright BUT remember to back up your data. An 100% risk free installation of any OS is not possible.

---

### Post by davetheman on 2006-07-22
I'm going to try using that qtparted program. Did that program ever cause problems?

---

### Post by SkyNet2029 on 2006-07-22
For some reason qtparted does not do a rescan properly after you finish your partitioning and save your changes. Sometimes.
What I mean is that on a few installs using qtparted I have had to reboot the machine for qtparted to recognize the newly created partitions, before the installer would go any further than that. I have never had that problem using Gparted, however.

---

### Post by bryonhowley on 2006-07-22
I never could get the full version to work(the cd with live cd and installer on one). I would setup the partions with /boot / /swap click next the installer would show those partions to format but clicking next it would only format /swap and then thow an error that there is no / partion. Used the Ubuntu server cd and worked fine with same partions strange.

---

### Post by davetheman on 2006-07-22
I ran Gparted on the live cd. It detected my external hard drive, and it had 2.7gb of unpartitioned data. I made a ext3 partiton out of it. Should I use that for Ubuntu and is it possible to put the boot loader, let's say, on a floppy or something, or can the boot loader just boot of the external hard drive?

---

