---
title: "How to correctly dual boot?"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by ASchlosser on 2010-11-23
Hey all!

After recently looking around the Linux world, I decided that I would also like to try fedora.  Primarily because of the BTRFS file system that I would like to try out while still having Ubuntu as my main OS.

Normally, I'd just partition as usual as I would with any of my other OSs, however this is the first time I have tried to dual boot two Linux installs on two different file systems.

Does anybody have a better method of going about this?  Or to just go about it as usual and install on two different partitions?

Also, I do not want to wipe the data from the computer as it is now.  I have it all backed up, but I don't really want to go through the hassle.

Thanks guys!

Andy

---

### Post by davidmohammed on 2010-11-23
There are many similar threads you could find using search.

Personally, if you are just trying, suggest one of the following

1. installing ubuntu on a usb stick and running from there.
2. using a wubi - install ubuntu via windows.  When you've finished, just use windows add-remove programs to delete.
3. installing a virtualisation tool in windows such as vmware player, virtualpc etc and installing ubuntu into a virtual guest

once you've settled on a distro, then consider dual booting.  multibooting fedora, ubuntu and windows can be tricky but is possible.

---

### Post by ASchlosser on 2010-11-23
I did search for it, I just didn't know if anything became different once I changed file systems (I didn't see anything like that once I searched it)

Ubuntu is my main distro now -- I don't even have windows installed actually.  I already have been playing with Fedora 14 in Virtualbox, so I'm sure I want to dual boot it.

The main reason for it is that I want to play with BTRFS after checking out some benchmarks with it outperforming EXT4 in random writes.

I probably should have specified that in the original post -- I was just trying to keep it short and sweet though.  Oh well, live and learn.

---

### Post by davidmohammed on 2010-11-23
ok - suggest use [this]("https://help.ubuntu.com/community/HowtoPartition") guide to partition ubuntu.

Then install fedora into one of the partitions, and when installing format the partition using btfrs.

You'll need to play around with grub to get ubuntu and fedora to dual boot.  See this [thread]("http://forums.fedoraforum.org/showthread.php?t=166818") for an example of the issues you will encounter.

---

### Post by ASchlosser on 2010-11-23
Awesome, thank you.  Thats actually the same guide I found -- I just didn't know if anything changed over the various releases.

I kinda figured that they wouldn't play nice right away, I just didn't want it to be catastrophic.

---

### Post by davidmohammed on 2010-11-23
...

remember backup - backup - backup! ... use clonezilla or something similar to do the backup and any subsequent restore.

Good luck!

---

### Post by oldfred on 2010-11-23
I do not know Fedora. Most distributions let you choose where to install the boot loader. I think Fedora still uses old grub which will not let you boot Ubuntu if Ubuntu is ext4. Ubuntu's old grub was updated to work with ext4 partitions.

You can install Fedora's grub to its boot partitions which I think it requires as it will not boot directly into BTRFS. Ubuntu should find the boot partition and add it to your boot menu, but I have seen some with issues. If you have Fedora's grub in the partition boot sector of the Fedora /boot you could then chainload to it just like we chainload to windows. Would require a custom entry in 40_custom.

If Fedora does overwrite the MBR you need to be able to reinstall Ubuntu's grub2, so be sure to have a working liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by ASchlosser on 2010-11-23
Excellent!

I haven't gotten around to trying it yet -- my Fedora ISO is still burning (USB Stick failed 3 times :rolleyes:)

But all of that makes sense.  I was thinking of simply install Burg instead of worrying about reconfiguring all of Grub/Grub2 -- just let it do its thing.

And good call with the clonezilla!  I just used simple backup before, but I'm liking clonezilla much better.

Hopefully its all good now, I'll set the thread to solved and post the results once I'm done and done.

---

