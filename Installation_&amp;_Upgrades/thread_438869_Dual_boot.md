---
title: "Dual boot"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by liberalist on 2007-05-10
Hi everyone,

This question has probably been asked before, sorry about that. I have an iMac Intel (Core 2 Duo) and wish to install Xubuntu 7.04 on a separate partition. I now have 2 partitions, 1 for Mac OS X and the other for documents. Could I reformat this last partition for use with Xubuntu? Will this remove every file present on this drive? 

Furthermore, I would like to get an option to boot into Xubuntu on every boot. If I do not choose anything a set amount of time, Mac OS X should boot by default. Is this possible? If so, could you explain how this works? 

Thank you very much in advance.

---

### Post by renzokuken on 2007-05-10
if you install to the second partition it will overwrite your documents yes. i suggest moving all your docs to the osx partition if you have space (or if not burn to CD/USB). then install xubuntu to that partition.

the installer will automatically install a bootloader called GRUB for you so when you boot up it will you be given a choice to boot to OSX or xubuntu. there is a configurable timer countdown as well. you can edit how grub works (default OS, countdown time etc) once xubuntu is installed

---

### Post by liberalist on 2007-05-10
If I upgrade my OS X installation to Leopard later this year (Mac OS X 10.5), do I need to reinstall Xubuntu and/or reconfigure GRUB?

Furthermore, can I access Linux partitions through Disk Utility in OS X and format them again? For instance, if I wish to remove Xubuntu and reformat my partitioning scheme to two partitions (instead of four). Is this possible? 

Furthermore, how many GBs do you recommend at least for a Xubuntu installation? I have 150 GB hard disk in total and 110 GB left on the second partition.

Is it true that you lose hard drive space by reformatting your drive?

---

### Post by notwen on 2007-05-10
> **liberalist said:**
> If I upgrade my OS X installation to Leopard later this year (Mac OS X 10.5), do I need to reinstall Xubuntu and/or reconfigure GRUB?

Furthermore, can I access Linux partitions through Disk Utility in OS X and format them again? For instance, if I wish to remove Xubuntu and reformat my partitioning scheme to two partitions (instead of four). Is this possible? 

Furthermore, how many GBs do you recommend at least for a Xubuntu installation? I have 150 GB hard disk in total and 110 GB left on the second partition.

1.  Shouldn't be a problem unless Leopard, which I doubt, will be adding/removing old partition during the upgrade.  It's very unlikely the upgrade would fill up the space you determine for your OSX partition either. =p

2. Disk Util will be able to see your linux(ext3, swap) partitions and create/format/remove them if you wish.

3.  To be on the safe side, since you have plenty of HDD space. I'd recommend at minimum 10gb for /, 1gb or less for swap(depends on your ram generally half of your system ram is sufficient), and the rest for /home.  

After you get Xubuntu up & running it's fairly easy to get GRUB setup to default boot OSX.  I've got an older iBook dual booting Edgy and OSX, so if I'm capable of getting it working, I'm sure you shoudn't have any issues.  Hope this helps. =]

---

### Post by renzokuken on 2007-05-10
if you upgrade to Leopard, it should not do anything to Xubuntu. there is a chance however that it may overwrite GRUB (although i am not sure). even if it does though this is not a major problem since you can simply reinstall grub.

i have no idea for your second question since i have never owned a mac.

for a base (simple) install of ubuntu you will want about 1-1.5Gb for swap and about 5gb for the xubuntu install. you could partition the rest as file store if you like in a way that both osx and xubuntu can access and share. just my opinion though

---

### Post by liberalist on 2007-05-10
> **renzokuken said:**
>  you could partition the rest as file store if you like in a way that both osx and xubuntu can access and share. just my opinion though

How can I partition the rest as a file store? Mac OS X cannot read ext3 partitions by default, namely.

Update: I have found a program that might be useful: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/) . However, this program only supports ext2. I prefer ext3 (this has a journaling feature, right?).

Furthermore, how can I reinstall GRUB? And how can I uninstall GRUB (if I decide to remove Xubuntu)? Again, thank you very much for all the kind help.

---

