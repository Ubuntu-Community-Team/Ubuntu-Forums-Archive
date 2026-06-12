---
title: "Installer Won't Recognize Different Partitions (only recognizes hard drive)"
date: 2005-08-29
forum: Installation &amp; Upgrades
---

### Post by mckay on 2005-08-29
I just got a new HP pavilion a830n with a 250 gig hard drive.  I started off by installing XP, then I set a partition and installed Ubuntu (as default).  Ubuntu worked fine and had no major problems.  Because I had a new big hard drive, I was excited to install some of my past favorite distros (before I discovered Ubuntu of couse) like Suse, Mandriva, Mepis etc...   I set up partitions for these and had various problems with them.  After I installed Mandriva (which does not work for some reason) the boot loader (that Mandriva installed) does not display Ubuntu as an option to boot.  

I am still learning about Linux and am not smart enough to know how to change Grub or be able to boot into Ubuntu.  I decided that I would just reinstall Ubunu and start over again.  When I do this it takes me to the partition section but does not display any of my partitions.  All it displays is that I have a maxdor 250 gig hard drive and that I can manually partition it.  I don't want to loose my XP partition (unfortunately this is the only OS that I can currently get to work well) or the files I have on it, so I don't want to mess with formating the hard drive.  I am surprised that it will not list the different partitions (I believe I have sda1~ sda7).

Does any one know what my problem is or how I can get it to recognize the partitions?  Or does anyone know how I can boot into Ubuntu (incidentally tonight I just installed Overclockix [which does not work (grr)] and it installed lilo with Kernal 3.4 and 3.6 and Windows as options).

---

### Post by duminas on 2005-08-29
[QUOTE=mckay]I just got a new HP pavilion a830n with a 250 gig hard drive.  I started off by installing XP, then I set a partition and installed Ubuntu (as default).  Ubuntu worked fine and had no major problems.  Because I had a new big hard drive, I was excited to install some of my past favorite distros (before I discovered Ubuntu of couse) like Suse, Mandriva, Mepis etc...   I set up partitions for these and had various problems with them.  After I installed Mandriva (which does not work for some reason) the boot loader (that Mandriva installed) does not display Ubuntu as an option to boot.  

I am still learning about Linux and am not smart enough to know how to change Grub or be able to boot into Ubuntu.  I decided that I would just reinstall Ubunu and start over again.  When I do this it takes me to the partition section but does not display any of my partitions.  All it displays is that I have a maxdor 250 gig hard drive and that I can manually partition it.  I don't want to loose my XP partition (unfortunately this is the only OS that I can currently get to work well) or the files I have on it, so I don't want to mess with formating the hard drive.  I am surprised that it will not list the different partitions (I believe I have sda1~ sda7).

Does any one know what my problem is or how I can get it to recognize the partitions?  Or does anyone know how I can boot into Ubuntu (incidentally tonight I just installed Overclockix [which does not work (grr)] and it installed lilo with Kernal 3.4 and 3.6 and Windows as options).[/QUOTE]
 I, to this day, have NEVER figured out how to get Ubuntu's installer to behave differently.
Heck, to get it to not nuke the Windows partitions I had, I needed to use Partition Magic within Windows to make some clear space--3 partitions (reiser, swap, ext3), and only then could I get Ubuntu to not blow up all the data on the drive.

Sorry I can't be of more help.

[size=1]And it's 2.4 and 2.6, sir. :P[/size]

---

