---
title: "Dual (or several, multiple, trial, whatever...) boot"
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by steffen on 2004-10-20
I am currently using Fedora Core 2, dual boot with Win XP. I would very much like to convert to Ubuntu, but as I'm using a laptop with a lot of custom configuration that took me a long time, I would like to be able to boot into Fedora as well in the beginning - just in case.

Does anyone know how to set this up? Will the Ubuntu install overwrite my Fedora or format those partitions, or can I easily just install Ubuntu on the side? Will I have to set up a new, or several new partitions for Ubuntu?

Thanks - from a 2 month old Linux user!

---

### Post by iwasbiggs on 2004-10-20
You will need at least 1 partition for ubuntu.

During the install you can skip the grub installation, then later boot in fedora (or any boot cd) and copy the (ubuntupartition)/boot/* stuff over to your boot partition (I don't know how fedora works in this respect).

---

### Post by steffen on 2004-10-20
So I take it there is no automatic procedure for installing Ubuntu alongside another Linux, on a different partition...?

What would happen if I install Grub?[/img]

---

### Post by woodstock on 2004-10-20
If you install grub, the ubuntu grub settings will overwrite everything in your MBR and you would have to reconfigure grub from within ubuntu and add entries for Fedora and Windows (If it didn't already did auto-detect windows and set it up)

For your initail post, you'll have to make a seperate partition for ubuntu, it will be able to share the swap partition with fedora.

Good luck.

---

### Post by ErikN on 2004-10-20
I have Windows, SLack and Ubuntu as a triple boot.

Installed Windows, then Slack on a deperate partition and then left free space for ubuntu, during installation u will be given the option to use the free space for ubuntu. After installation the Grub installation will detect other OS's on your system and asks you to add them, confirm this and next time when you boot you will be given the option to boot into the OS of choice =)

---

### Post by steffen on 2004-10-21
I just booted System Rescue CD to run QT Parted to resize my old Windows XP NTFS partition, that is excessively huge. I resized the partition, but now I have 9 GB of free space on my disk, that is not being used for anything, and when I start the Ubuntu installer these 9 GBs are labelled "unusable".

In QT Parted I can't find any tools for setting up a partition with this extra space. Anyone know?

---

### Post by ErikN on 2004-10-21
THe way around this would be to go into XP and go into computer management ( Administrative Tools - Computer Management ) , then select disk management and you should see the free space there, create a logical drive and format it, when its done delete the logical drive making it free space again.  

After this run the ubuntu installer again and it should detect the free space,  one thing that i would recommend tho is to split the 9 gigs into 2 sections, one fat32 partition and the rest for free space, this will make it easier for yourself to swap files between windows and linux.

HTH

---

### Post by steffen on 2004-10-21
Thanks for helping out! :)

I go into Win XP, but when I click on the free space, the button for 'Make partition' is greyed out. I couldn't find any way of doing this in Win XP.

I went back to Fedora and made an attempt with parted. I first attempted creating a logical partition, but got an error, so I did a Google and found a printout from someone who had attempted something similar ([http://www.suse.de/cgi-bin/print_page_www.pl?NPSPath=/webredesign/htdocs/en/private/support/online_help/howto/parted/index.html](http://www.suse.de/cgi-bin/print_page_www.pl?NPSPath=/webredesign/htdocs/en/private/support/online_help/howto/parted/index.html)), and tried again with a primary partition. 

When I hit enter, I only get the black box blinking in my bash-window. Nothing happens. Here's a printout of what I did:

```
&#91;root@localhost sbin&#93;# parted /dev/hda
GNU Parted 1.6.9
Copyright &#40;C&#41; 1998, 1999, 2000, 2001, 2002, 2003 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.
 
This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.
 
Using /dev/hda
Information&#58; The operating system thinks the geometry on /dev/hda is 58140/16/63.
Therefore, cylinder 1024 ends at 503,999M.
&#40;parted&#41; print
Disk geometry for /dev/hda&#58; 0.000-28615,781 megabytes
Disk label type&#58; msdos
Minor    Start       End     Type      Filesystem  Flags
1          0,031   5681,812  primary   ntfs        boot
2      14881,781  14981,695  primary   ext3
3      14981,695  23795,789  extended              lba
5      14981,726  23059,968  logical   ext3
6      23060,000  23795,789  logical   linux-swap
4      23795,789  28615,781  primary   fat32       lba
&#40;parted&#41; mkpartfs logical fat32 5681,812 14881,781
Warning&#58; Unable to align partition properly.  This probably means that another
partitioning tool generated an incorrect partition table, because it didn't have the
correct BIOS geometry.  It is safe to ignore,but ignoring may cause &#40;fixable&#41; problemswith some boot loaders.
Ignore/Cancel? i
Error&#58; Unable to satisfy all constraints on the partition.
&#40;parted&#41; mkpartfs primary ext3 5681,812 14881,781                                                                          

```

...and here's when nothing happens after I press enter... The black box is just blinking... So I press enter and it says: 'Segmentation fault'

I've also attempted the same with ext2 partition, and extended partition. I get either of these results every time.

---

### Post by steffen on 2004-10-22
Anyone know any other apps I could try, apart from Qt_parted, parted and Win XP?

---

### Post by FLeiXiuS on 2004-10-22
If you want a partition program, I would definately recommend Partion Magic 8 for Windows Operating Systems.  This is perhaps a very strong program indeed.  Allows you to do so much to your drives.  

If you want to do this in linux, then you can get the linux-ntfs package and resize the NTFS drive.  (Considering its ntfs 8) )
[http://linux-ntfs.sourceforge.net/](http://linux-ntfs.sourceforge.net/)

I haven't tried resizing in VFAT...

Good Luck!

---

### Post by steffen on 2004-10-23
Thanks for the swift replies and the help, everyone! 

...the problem solved itself - sort of :)

I installed Partition Magic 8 in Windows. I received error 25, which I looked up, and found a couple of postings suggesting I should use sdisk to fix my partitions. I tried, but after going through it, and doing some stuff I didn't understand (usually a bad idea) my whole HD was gone. 

Luckily I have a fairly recent backup.

Anyway, that solved my problem for good, since I can now forget about Fedora and Windows, and just install Ubuntu. Hope all the good reviews are true...only one way to find out ;)

...and actually, I have some problems installing Ubuntu as well (might be the only one it seems), but I've posted that in another thread.

---

