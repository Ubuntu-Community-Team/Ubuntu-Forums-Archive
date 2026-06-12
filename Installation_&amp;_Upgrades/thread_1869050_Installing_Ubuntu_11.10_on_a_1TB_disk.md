---
title: "Installing Ubuntu 11.10 on a 1TB disk"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by arvinoids on 2011-10-25
Hi. I have a problem installing 11.10 on a 1TB disk with existing partitions. I currently have 4 partitions on it, but when I choose "something else" on the installation type, it does not show the partitions, instead shows /dev/sda as the only item. And the only clickable button is "New Partition Table" and "Revert". So how do I go about this?

Thanks

Edit: Just to make sure I did not break my partition table, I booted to windows and found they are all fine. Attached is a screenshot of my partition table.

---

### Post by jnorthr on 2011-10-25
i would definitely NOT choose 'new partition table' option as it will probably blizt your whole drive and you'll need to rebuild it. You could try finding a live CD of any linux installation like ubuntu, linux mint, etc. These are often found on the front of computers magazines. If you boot from a live CD with your 1TB attached, you'll be able to run linux which has a nice utility called gparted. it is a partition management tool we use to setup and format one or several partitions. It looks like your screenshot show a 40GB partition formatted as ext3 which is a linux format, so your 1TB may already be setup for a linux installation.

---

### Post by Mark Phelps on 2011-10-26
BEFORE you attempt any kind of Ubuntu installation, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by arvinoids on 2011-10-26
I have been using Super Grub Disk to recover the Windows partition since I knew about it and it's been working real great, so I have no trouble recovering boot sectors. I am suspecting a problem with Ubuntu having trouble recognizing the partition table I have modified using MiniTool Partition Wizard. Note that I used the Windows 7 installer to create the initial partition table, then edited it with MiniTool to create the ext3 and hfs partitions.

---

### Post by Mark Phelps on 2011-10-26
One Windows partitioning tool that has shown good results is Partition Wizard.  It is strongly recommended in the Windows 7 forums.  You can download the ISO for free from their site, burn that to CD, and see if that will repair the partition table for you.

---

