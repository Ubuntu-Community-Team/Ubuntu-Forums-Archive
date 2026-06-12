---
title: "Ubuntu installer does't recognize data partition created in Win7"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by tomet on 2014-04-26
Hello everyone.

I try to install Ubuntu GNOME 14.04 on my computer which has Windows 7 already installed. When I start the installer for Ubuntu and choose the advanced installation options, I get to the partitioning step.The installer does recognize the Windows system partition on the C: drive (SSD). But I have a second disk (HDD) which I use as a data disk for Windows. This disk contains one partition, but the installer tells me it is all free space. I have attached a screenshot of the partition manager in windows (sorry for the German ;) )

Can anyone help me out here? I really want to install Ubuntu, but I don't want to overwrite the partition table on the HDD.

Thank you for your support

P.S.: I know there are a lot of similar threads like this. I read them, but they all dealt with Ubuntu not recognizing the main Windows partition.

EDIT: I have now started the gParted in live modus and got an error talking about GPT. I have attached a screenshot.

---

### Post by oldfred on 2014-04-26
Did you use Windows to convert sdb from gpt to MBR(msdos)? Windows does not correctly convert drive and leaves a backup gpt partition table. Then Linux tools see MBR and backup gpt and assume you want to totally erase it as it is neither.

As long as drive is not over 2TiB, it can be MBR or gpt. If larger it must be gpt to correctly use all the space. 

       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

            GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

    
If you are sure drive is MBR and that is correct you can remove the backup gpt partition table.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by tomet on 2014-04-26
Thank you for your answer.

I haven't converted sdb from gpt to mbr in Windows as ar as I know. But I don't know very much about partitioning so I can't say for sure. I don't know what it is, is there a way I can find out?

EDIT: Following this ([http://www.tomshardware.co.uk/forum/268934-32-disk](http://www.tomshardware.co.uk/forum/268934-32-disk)) tutorial, I found out that according to windows, that disk is paritioned with MBR. So shall I run fixparts now? Is it safe?

---

### Post by oldfred on 2014-04-26
It should be.  I think if you do not do the w or write fixparts does not make any changes.

You can post this:
sudo parted -l

---

