---
title: "Installation advice: Multibooting."
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by jayton.okada on 2008-05-17
Good day everyone, :)

I'm fairly new to the Ubuntu world, I've been interested in it back when Breezy and Dapper came out but never dwelve into ubuntu. Well, I am a computer tech, and I'm aiming to get a CompTIA Linux+ in the coming years. Because I do a lot of repairs and I'd like to further educate myself with Linux, I was wondering what advice you folks here on the forum could give me concerning multibooting. I've read up on some tutes about it, and there were some very informative ones, but I'd like to direct you folks with the setup I'm aiming to achieve:

I'm running a Intel C2D E6550 2.33GHz on an ASUS P5KL-VM Board.
4GB DDR2-667 PC5300 (2x2GB)

Drive Configurations:
Lite-on DVD+/-RW drive (IDE Master) 
Seagate 320GB IDE Drive used for Data/backup/music (IDE Slave)
Western Digital 320 GB Sata Drive #1 running Windows Vista Ultimate 
Seagate 250GB Drive Sata Drive #2 running Ubuntu

I would like to keep my windows vista drive alone without partitioning, I've got a lot of tools, programs, and other documents I use for music recording, photography, webdesign, and computer repair apps, etc.... I've got them all backed up on my 500GB external, but I'd like to not have to deal with reinstalling vista, or transferring all my info.

On my Seagate Sata drive I'd like to partition and install Ubuntu 8.04, the new Fedora 9, and Solaris 10. Is this configuration ill advised?

I will be keeping my Vista drive disconnecting during these installations and boot into vista using my BIOS Boot menu.

I really want to know if I could easily put Solaris on a multi-partitioned drive with Ubuntu and Fedora, or should I just go and put it on another disk drive?

I'm really interested in using Solaris as some business clients I've met over the past few months have converted from windows to Sun Micro. products such as Sun's blade servers and Sparc/sun ultra desktops.

So once more, I'm aiming to have Vista left alone on one drive, I have  no intention of booting into vista using Grub, this hdd will be disconnected during installation of the other OS's. 
On a second drive I want to multiboot Ubuntu Hardy, Fedora 9, and Sun's Solaris 10. I also intend to play around with Mandriva, openSUSE, Debian, gOS, and maybe centOS someday just to have a feel for the different distros out there.
I did read the one multiboot tute on 145 total os's and a handful of the ones here on the forums mainly directed at vista, xp, ubuntu, and fedora multiboots, my main concern is installing solaris.

Any advice info would be greatly appreciated.

Sorry if this post is a bit long

---

### Post by logos34 on 2008-05-17
> **jayton.okada said:**
> I really want to know if I could easily put Solaris on a multi-partitioned drive with Ubuntu and Fedora, or should I just go and put it on another disk drive?

Solaris has been using Grub bootloader (what the other use) for some time now, so there shouldn't be a problem.

You might consider making an extended partition on part or all of the target drive, and put OS's inside on logical partitions.  You can then subdivide it up into dozens of partitions (otherwise if you go with primary partitions the limit is four).

You can probably even boot vista from grub if you [follow this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Mandriva, though, might be hard to boot from any grub other than its own.  I can't seem to just add mine to ubuntu grub--I have to write it to a floppy and boot it that way (?)

---

### Post by jayton.okada on 2008-05-17
thanks, I'll try it soon.

As for vista, I do prefer to keep it separate from Grub, and yeah Mandriva I've heard some issues with mandriva and minor issues with debian on multi boots.
 I'll see how things go once I get some time in tonight.

---

### Post by Kevbert on 2008-05-17
You shouldn't need to disconnect the Vista drive.
If you decide to install all three Linux OS then install Fedora first as it doesn't always recognize other Linux distros.  Ubuntu should see all other OS so I'd install that last.  In the Grub startup menu Ubuntu will be run by default.  If you need to change this you'll need to edit the /boot/grub/menu.lst file.  Look for the line default 0 and change the number to which ever menu item you wish to boot (counting from 0).
I hope I'm not teaching you how to suck eggs, sorry if I am.
I'm running Win XP with Kubuntu 8.04, Fedora 8 and Ubuntu 7.10.

---

### Post by teaker1s on 2008-05-17
Be careful, firstly you you want to ```
chkdsk /f
``` to verify windows ntfs file system.

Secondly do not use gparted live boot cd to repartition as sometimes this corrupts ntfs file system (can be fixed with knoppix fixntfs)

Boot up ubuntu cd and use guided partitioning follow through the prompts and there is a advanced tab, select this and install grub to ubuntu partition and not mbr. **Failure to do this will stop vista sp1 installing and kill bitlocker encyption/tpm module**

when install has finished reboot and you will notice that it boots to vista, this can be solved easily using easybcd tutorial with screen shots here
[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://http://neosmart.net/wiki/display/EBCD/Ubuntu")

so now vista boot loader chain loads to grub

---

### Post by housam on 2008-05-17
Look at this [[COLOR="Red"]_guide_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=724817") by Bodhi.zazen

---

