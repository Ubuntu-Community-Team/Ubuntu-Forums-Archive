---
title: "How can I install iso to mounted hard drive?"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by slixz85 on 2011-12-12
hi, this is my deal. i am using iqunix wich has been a decent desktop and I want to save because I have downloaded alot of games to it.

i have 3 partitions on my hard drive this simple sda 1 swap sda 2 iqunix sda 3 i have pinguy but it is broken. me being new to linux was trying to shrink it down to make it smaller and must of uninstalled something wrong of course. I don't want pinguy anyway. I have a pretty fast computer but I play games like nexuiz, sauerbraten, open arena and so forth, so i like a minimal system on memory and all.

so i have a iso file of peppermint ice which really flies. I have normally installed them by and these two os's i have now by flash drive with unetbootin but my flash drive is broken. I am wanting to use this peppermint ice iso because the internet works alot better for me and I am going to stick with it actually for this pc plus it plays games quicker.

so if i clean the partition of sda3 pinguy to put peppermint ice on it. how can i do this by extracting files? is it possible? or does the iso really have to boot from the bios?

thanks to any help appreciated

---

### Post by MAFoElffen on 2011-12-12
> **slixz85 said:**
> hi, this is my deal. i am using iqunix wich has been a decent desktop and I want to save because I have downloaded alot of games to it.

i have 3 partitions on my hard drive this simple sda 1 swap sda 2 iqunix sda 3 i have pinguy but it is broken. me being new to linux was trying to shrink it down to make it smaller and must of uninstalled something wrong of course. I don't want pinguy anyway. I have a pretty fast computer but I play games like nexuiz, sauerbraten, open arena and so forth, so i like a minimal system on memory and all.

so i have a iso file of peppermint ice which really flies. I have normally installed them by and these two os's i have now by flash drive with unetbootin but my flash drive is broken. I am wanting to use this peppermint ice iso because the internet works alot better for me and I am going to stick with it actually for this pc plus it plays games quicker.

so if i clean the partition of sda3 pinguy to put peppermint ice on it. how can i do this by extracting files? is it possible? or does the iso really have to boot from the bios?

thanks to any help appreciated
You could copy to anywhere on any drive connected- as the ISO file.  Create a menu item for that ISO in your grub menu to boot it... I know iqunix is an Ubuntu derivative. Here is some good info on that:
[_ISO Booting with Grub 2 Menu Entries_]("http://ubuntuforums.org/showthread.php?t=1549847")

You could also install from that HDD resident file... (hint)

Next tip... Linux will boot from Logical Partitions without worry of the number of partitions you have....to save primary partitions for those that don't.

---

