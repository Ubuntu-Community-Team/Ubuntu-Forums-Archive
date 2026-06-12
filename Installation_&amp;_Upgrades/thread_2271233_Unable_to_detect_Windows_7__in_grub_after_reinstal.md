---
title: "Unable to detect Windows 7  in grub after reinstalling Ubuntu"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by sahil5 on 2015-03-28
I reinstalled Ubuntu through a live USB to replace a 32-bit installation with a 64-bit installation. I have (or had!) Windows 7 installed alongside Ubuntu, but it is not showing up in the grub menu anymore. My grub menu just shows Ubuntu as an option.

I booted from the live USB again and ran boot-repair and installed grub on /dev/sda. The result is here -> [http://paste.ubuntu.com/10696750/](http://paste.ubuntu.com/10696750/) . 

Would this information be sufficient? Thanks in advance!

---

### Post by Kaabi on 2015-03-29
Hey

I'm not entirely sure what's going on here.  I'm a bit confused as to why /dev/sda5 is an Extended Partition that is unused, and in between two ntfs partitions.

When you uninstalled the 32bit version of Ubuntu, did you:
a) Boot in 64 bit and wipe it from there
b) Boot into windows and delete partitions, and then start again

Honestly, the only thing I can think of is to download a windows 7 repair iso from Microsoft, and repair the windows Boot loader.  Then, when booted into windows, load the partition manager and delete all paritions except for the Windows ones.  Then boot into 64 bit Ubuntu and start over.

I might be wrong, but I think the partitioning is off.  Hopefully someone else may be more enlightened though and may have a better suggestion.

---

### Post by Mark Phelps on 2015-03-29
>  /dev/sda5 is an Extended Partition that is unusedNot true!  sda4 is the extended partition, containing sda5 (recovery), sda6 (swap) and sda7 (Linux).

Your sda1 still looks like it might have the Windows boot loader files.

Unfortunately, boot-repair does not always work -- especially when trying to "repair" Windows boot problems.

Since you can still boot into Ubuntu, then do that and run "sudo update-grub" -- and watch to see if it lists something like "Windows (loader)".

If it does not, one or more of the Windows loader files is corrupted or missing.

Since you can't boot into Win7 anymore, you can't use the Repair feature to create a repair CD; thus, you will need go to the link and purchase the repair CD ISO file for the version of Win7 you're running: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")  Burn that to a CD, boot from that CD, and run Startup Repair three times -- that's right, three times.

When done, your PC will then boot directly into Win7 and you will have to reinstall GRUB from the Ubuntu install media.

---

