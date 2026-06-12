---
title: "Dual Booting - Ubuntu (5.10) + Suse 9.3"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by azteech on 2005-11-07
Hello,

I am thinking of trying out Suse linux. I recently obtained a 9.3 version on DVD, and thought I would give it a try.

However, I want to maintain ubuntu as my primary linux distro, and have Ubuntu Grub remain as my boot loader.

In reviewing several googled forum entries, it seems everyone out there is letting Suse over write Grub and take over as the boot loader. I don't want this to happen.

Using fdisk, it shows I have the following set up for my hard drive partitions

Disk /dev/hda: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          36      289138+  83  Linux
/dev/hda2              37        3075    24410767+  83  Linux
/dev/hda3            3076        3322     1984027+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4875    39158406   83  Linux

Using fdisk /dev/hdb and verifying partitions, I find I have

Expert command (m for help): v
38988179 unallocated sectors

I know I left a portion of /dev/hdb free for future testing/installing different versions of linux. So, knowing this, I believe I have approx 30 GB free to install Suse to. 
Please correct me if I am wrong in assuming that Suse installer will find the un-partitioned space and try to install to it, instead of over-writing my existing partitions.

Additionally, I want to be able to use the existing /boot partition (/dev/hda1) , swap partition (/dev/hda3), and /home partition (/dev/hdb1), and not have Suse re-create them.

This means I will be installing the Suse 9.3 / (root) to /dev/hdb2)

Will Suse 9.3 allow me to only setup and install root, while using the existing /swap and /home partitions?

How do I protect the Grub Boot loader for Ubuntu, so that Suse does not over-write it? Then, if that is possible, how do I set up Grub (From within Ubuntu) to add Suse 9.3 to the list of bootable partitions?

How do would I tell Suse to use the existing swap, and home directories, and not over-write/format them?

Any help would be appreciated.

---

### Post by paddyg on 2005-11-08
well, i don't think it's a good idea.

When i used Fedora and Yoper the only thing they shared was the swap partitions.

How can you be so sure Suse won't mess up all your hidden/config files in your home? Perhaps, i'm too cautious, but I'd keep them apart. If you need your ubuntu home, why don't you just mount it?

Also, i think Suse installer will ask you where to install and what to format.

As for Grub, i think Suse installer can let you update Grub instead of installing it again. I think that will add a new block (title, root, kernel etc) to your ubuntu boot sequence in /boot/grub/menu.lst

---

### Post by metoo on 2005-11-08
I'm anotherone, who cannot directly give you an answer.
However, I'm running 2 systems kubunut/SuSE10.0 .

So why would you want to use SuSE 9.3? SuSE like ubuntu improves with every version. Not really a fair comparison that will give you any valuable information.

I let SuSE (10.0 not 9.3) overwrite grub. Now I have a SuSE boot logo with grub. Other than that, it forgot to add kubuntu, which was no problem, as there was a /boot/grub/menu.lst.bak, so I could copy the menu entries for ubuntu from there.
Then I could not boot ubuntu. No problem. In grub, hit e, select the ubuntu entry, hit e and select SAVEDEFAULT, hit d. hit b to boot.
You have to comment out the SAVEDEFAULT line from the ubunut entries in /boot/grub/menu.lst with the SuSE grub bootloader.
So you might be right to stick with the ubuntu grub, even so,  the other one is doing it's job OK now.

The lines to add to start SuSE manually depend on your system setup. I use an extra partition for /boot, so both distros install into that. I would recommend to let grub do the magic. You may still re-run/re-configure grub from within ubuntu later, after saving the SuSE entries to get rid of the SuSE grub stuff if you wish.

Sharing swap is OK.

But sharing /home is not 100% OK. I tried this for the 1st time myself to spare me some time to configure everything, but it did not take over all settings 100% (had to adjust quiet a lot in SuSE). So as the poster before mentioned, this idea is not so good.

A last tip. I found cfdisk much easier to use compared to  fdisk when partitioning hds. 'cfdisk /dev/hda' if you want to try it. Don't forget to 'write' before exiting, otherwise nothing will be changed.

---

