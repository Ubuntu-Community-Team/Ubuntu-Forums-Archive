---
title: "Issues Booting Ubuntu 18.04 LTS (Server) after cloning from another drive"
date: 2020-08-31
forum: Installation &amp; Upgrades
---

### Post by jdo300 on 2020-08-31
Hello All,

I have an Ubuntu server running 18.04 LTS. Not long ago, I had to clone the drive of this server to another machine to make repairs, and now I need to reclone it back to the server again. This time, I used the GPartd boot disk following [these instructions here]("https://www.addictivetips.com/ubuntu-linux-tips/clone-a-linux-hard-drive-with-gparted/#:~:text=To%20copy%20a%20partition%20in,to%20it%20in%20the%20app.") to copy the boot and EXT4 partitions from the second drive to the server.

After cloning the drive back. I tried to reboot the server but it just went into an infinite reboot loop after trying to start the drive. I'm assuming something got messed up with the grub configuration, so I next created a Boot-repair-Disk on a USB drive and followed [these instructions here]("https://sourceforge.net/p/boot-repair-cd/home/Home/") to try and repair Grub. Unfortunately, It failed, but I had it output the error report and posted it here:

[http://paste.ubuntu.com/p/4gbg8F4xnH/](http://paste.ubuntu.com/p/4gbg8F4xnH/)

I hope this will be useful, as I'm not sure what to try next.

Thank you all,

Jason O

---

### Post by rsteinmetz70112 on 2020-08-31
When you cloned the drive were you able to boot the cloned drive?
Do you see the grub menu? 
At what point does the computer reboot?

---

### Post by oldfred on 2020-08-31
You show sda1 as both bios_grub and /boot? Not possible.
The bios_grub is 1 or 2 MB unformatted partition with bios_grub flag for grub to correctly install in gpt partitioned drives in the old BIOS boot mode (not UEFI). 
You are showing it as ext4?

You also show menu.lst which is from grub legacy or old grub. Ubuntu has used grub2 since 2010.

Change sda1 to unformatted with bios_grub flag. 
And then in Boot-Repair run the full reinstall of grub, so it can correctly use the bios_grub partition.

Some systems need a boot flagged partition, but grub does not use a boot flag. So you can put a boot flag on sda2, if your motherboard requires it.

---

### Post by jdo300 on 2020-09-01
> **rsteinmetz70112 said:**
> When you cloned the drive were you able to boot the cloned drive?
Do you see the grub menu? 
At what point does the computer reboot?

On the computer that I cloned the server's drive to, I do see a grub menu when it boots and can select Ubuntu and it comes up fine. But on the server, the cloned drive just tries to goto the hard drive after post and then reboots again (doesn't show anything).

---

### Post by jdo300 on 2020-09-01
> **oldfred said:**
> You show sda1 as both bios_grub and /boot? Not possible.
The bios_grub is 1 or 2 MB unformatted partition with bios_grub flag for grub to correctly install in gpt partitioned drives in the old BIOS boot mode (not UEFI). 
You are showing it as ext4?

You also show menu.lst which is from grub legacy or old grub. Ubuntu has used grub2 since 2010.

Change sda1 to unformatted with bios_grub flag. 
And then in Boot-Repair run the full reinstall of grub, so it can correctly use the bios_grub partition.

Some systems need a boot flagged partition, but grub does not use a boot flag. So you can put a boot flag on sda2, if your motherboard requires it.

Thank you for your feedback. I booted the server up with the GParted boot disk and cleared set the partition with grub to be formatted as cleared. I also confirmed that the Grub flag was set on the partition and that the boot flag was not set. Then I booted into the Boot-Repair-Disk and tried to run the automatic install and it failed again. Here's an updated paste-bin report from the fail:

[http://paste.ubuntu.com/p/pGrtVWzWgm/](http://paste.ubuntu.com/p/pGrtVWzWgm/)

There must be something silly I'm still missing...

**NOTE: **I also went into to GParted and completely deleted and reallocated the partition and got the exact same result. I noticed that the pastebin report is showing the partition as being a "BIOS Boot Partition" Even though I haven't assigned any file system type. Could this have something to do with it? Here's a screenshot of what it looks like in Gparted:

[ATTACH=CONFIG]286852[/ATTACH]

- Jason O

---

### Post by oldfred on 2020-09-01
I saw this but did not know if just reporting something or not.
> sda:300GB:scsi:512:512:gpt:ServeRA RAID 1 Array:;

Was drive part of RAID before.
If so, it has meta-data that interferes with grub normal install using desktop installer like Boot-Repair runs. If you have true RAID, then you probably need to chroot into system to repair it.

I do not know know RAID, but it used to be this command. If you have RAID, do not run this:
sudo dmraid -E -r /dev/sda

But mdadm has replaced dmraid.
15.04 or later now uses mdadm to support intel fakeraids 
sudo mdadm --detail-platform
mdadm --zero-superblock /dev/sda1

---

### Post by jdo300 on 2020-09-01
> **oldfred said:**
> I saw this but did not know if just reporting something or not.


Was drive part of RAID before.
If so, it has meta-data that interferes with grub normal install using desktop installer like Boot-Repair runs. If you have true RAID, then you probably need to chroot into system to repair it.

I do not know know RAID, but it used to be this command. If you have RAID, do not run this:
sudo dmraid -E -r /dev/sda

But mdadm has replaced dmraid.
15.04 or later now uses mdadm to support intel fakeraids 
sudo mdadm --detail-platform
mdadm --zero-superblock /dev/sda1

Yes, the server does have a hardware RAID system with two drives (currently only one of the drives is inserted - need to replace the other one). THe system seemed to boot fine before with only the one drive in, but I'm not sure what to do now if that is somehow interfering with the Boot-Repair utility...

Ok, Dumb question. If I installed a clean copy of Ubuntu on the server and then overwrite only the ubuntu partition with the cloned one, would that work, or would it kill something again?

---

### Post by oldfred on 2020-09-01
I would expect clean install to work, but that will overwrite any configuration files you have with the defaults.

And then restoring from your clone erases the new install.

I just do not use cloned copies and believe in new clean installs. 
But then you have to have good backups of all your data, configuration files, server type apps & data in / like database or web, and list of installed apps to make it easy to reinstall.

---

### Post by jdo300 on 2020-09-01
Ok. I finally found a solution. I created a Ubuntu 18.04 LTS (SERVER) boot disk, and was able to use it's repair option to reinstall Grub and get it to boot. Here's the guide I followed to get it to work:

[https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/amp/](https://www.tecmint.com/rescue-repair-and-reinstall-grub-boot-loader-in-ubuntu/amp/)

---

