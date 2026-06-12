---
title: "2 disk drive installation"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by Unotforme on 2011-04-18
Hello All,

I have an acer aspire with AMD Phenom 9550 quad core, w/ 4M ram.
I have a 640 GB harddrive (SATA with 2 partitions, c:/d:) with windows Vista 64 bit installed. I recently purchased a new 750 GB Harddrive (SATA), that I wish to install Ubuntu 10.10 onto. The drive is brand new (has not been formatted, no data). I have 2 questions. What do I need to do to the new drive to prep for install of Ubuntu (if anything), and where should I install the Ubuntu boot loader (the new disk or old one with windows on it)?

Thanks

---

### Post by oldfred on 2011-04-18
If your BIOS (and I think all SATA BIOS let you) lets you choose which drive to boot, I would install Ubuntu's boot loader to the second drive and set BIOS to boot that drive. Grub's os-prober will find windows and let you boot either, but if the new drive fails you can still boot via BIOS the first drive.

We have two schools of thought here. One is to total disconnect the windows drive and install. That absolutely makes sure grub's boot loader is not installed to the windows drive. Others suggest using manual install and that then gives the options on which drive to install grub's bootloader. All the automatic installs default to installing grub's boot loader to sda as it automatically assumes you want to dual boot without having to change BIOS.

Lots of detail - not as complex as it looks as Herman explains so much.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

