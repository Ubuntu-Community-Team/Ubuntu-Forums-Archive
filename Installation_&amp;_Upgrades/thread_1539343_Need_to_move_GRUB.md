---
title: "Need to move GRUB"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by Karl1982 on 2010-07-26
I changed out my laptop's hard drive recently.  It used to have Ubuntu and Windows 7.  Usually the way I like to do this is have Ubuntu install GRUB to its own partition boot sector so 1.) Windows will leave it alone, and 2.) I can later replace the boot loader with GRUB4DOS and chainload the partition directly, thus getting Ubuntu's original GRUB menu.  That way Ubuntu can update/modify its own GRUB config (including new kernels and arguments) as it sees fit and I don't have to worry about it.

I decided to go with a clean installation since my previous one had been through a few distro upgrades.  I haven't even put Windows on it yet, but on my new Ubuntu installation, I accidentally let it install GRUB to sda instead of sda1, so it wrote it to the MBR instead of its partition BS.  I dropped GRUB4DOS on it anyway, and I could directly load the kernel or the GRUB core... but next time GRUB updated, it blew out my GRUB4DOS on sda and replaced it with its own GRUB again.

Basically, I want to reinstall/retarget GRUB to sda1 so I can get things back how I want them, and I'd like to do it without having to reinstall.  I know my way around GRUB4DOS, but I'm not very familiar with GNU GRUB.  I was afraid I might do something that would mess up the way Ubuntu is updating its own GRUB config.  It's Ubuntu Desktop 10.04 with GNU GRUB 1.98-1ubuntu7.  What do I need to do?

---

### Post by oldfred on 2010-07-26
I have learned to like grub2, but it is more complex because it offers more features.

Grub2 does not like to be installed to a partition as then you have to use blocklists. As I understand it a blocklist is hard coded addresses, so if your boot files get moved on an update (or even by a filecheck) then boot will fail. You would have to reinstall to fix. I think they are trying to make it more difficult but the old procedure was to add --force to the install command.

Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 


General info:
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Karl1982 on 2010-07-26
To be clear, I'm talking about on the last screen of Ubuntu installation, there is a button (Advanced, if I recall) that allows you to specify where to install the GRUB boot loader.  I've selected sda1 instead of sda on several installations of Ubuntu and never had a problem, even after distro upgrades.

But you're telling me this is an unstable configuration?  *grub-setup --help* even uses this as an example: *DEVICE must be a GRUB device (e.g. `(hd0,1)').*

So if I run *sudo grub-setup (hd0,1)*, leaving everything as defaults, it'll install the boot code to its partition bootsector (that is the correct device and partition), and leave the existing GRUB config files untouched?  Or do I want to use *grub-install*?  I also need it to not overwrite GRUB4DOS when GNU GRUB is updated in the future.

---

### Post by confused57 on 2010-07-26
> **Karl1982 said:**
> To be clear, I'm talking about on the last screen of Ubuntu installation, there is a button (Advanced, if I recall) that allows you to specify where to install the GRUB boot loader.  I've selected sda1 instead of sda on several installations of Ubuntu and never had a problem, even after distro upgrades.

But you're telling me this is an unstable configuration?  *grub-setup --help* even uses this as an example: *DEVICE must be a GRUB device (e.g. `(hd0,1)').*

So if I run *sudo grub-setup (hd0,1)*, leaving everything as defaults, it'll install the boot code to its partition bootsector (that is the correct device and partition), and leave the existing GRUB config files untouched?  Or do I want to use *grub-install*?  I also need it to not overwrite GRUB4DOS when GNU GRUB is updated in the future.

If this is what you need or want to do you can run:
```
sudo dpkg-reconfigure grub-pc
```
then just select your Ubuntu partition(e.g. /dev/sda1) to install grub to, when update-grub is run.  As long as Ubuntu 10.04 with grub2 is on a primary partition, you should have no problems chainloading to it...I haven't been able to chainload to 10.04 on a logical partition.

---

### Post by Karl1982 on 2010-07-26
That's exactly what I needed, thank you.

---

