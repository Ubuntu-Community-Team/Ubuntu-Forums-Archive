---
title: "Grub error17"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Sandsound on 2006-06-05
Hi all

I have a problem with Grub.

I have installed Ubuntu on a pc that controls internet, printer and filebackup, and that part went smooth. But the pc has five HD's (four IDE and one SATA) so I had to remove one to make room for the CD-drive, and now when i put the HD back it gives me a Grub error17 ?

Is there any way to fix this without having to run a CD ?

My drives are :

primary master : hda1  120Gb ntfs windoze xp
primary slave  :hdb1? 160Gb ntfs misc. backup
(the one i replaced with a CD-drive to install Ubuntu)

secondary master :hdc1  250Gb ntfs misc. backup
secondary slave :hdd1  160Gb ext3 Ubuntu (with two partitions, / and swap)

sata : sda1  180Gb ntfs misc. backup

I know that this might not be the optimal way to do it, but I didnt expect the install of Ubuntu to go so smooth :-) and I wanted to keep my windoze around so I at least could boot up on that when my husband wanted to check his mail or something like that.
Maybe I should just start over and format my old windoze disk, it looks like Im not gonna be useing this anymore (fingers crossed).


btw... Ubunto rocks... It only took me about 2 hours to install the pc with shared backup-drives, shared printer, shared internet. Not bad for a girl whos only been running Ubuntu for about 10 days :-)

---

### Post by SkyNet2029 on 2006-06-05
Based on the Grub error code tables:

> 17 : "Invalid device requested"
 This error is returned if a device string is recognizable but does not fall under the other device errors.

I too have come across this error from time to time, and only know that in my circumstances I had mis-configured the HDD jumper settings. Trial and error got things back to sane-ness. That was in my situation though, so not sure if this even applies in yours. I too was running multiple drives (3 HDD/ 1 Dvd R/W ) and also had yanked a drive to allow for Cd usage, also was dual booting with Winblows at the time. I managed to duplicate the instance on many fresh installs with that same configuration (jumpers set incorrectly) and it corrected once jumpers were in correct config. Sheer hit and miss speculation though, at best.

This page may be of more use to you, as it has a nifty table of all of Grub's error codes and their meanings, with possible solutions to said.

[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

-EDIT- I had meant to post this [http://www.gnu.org/software/grub/manual/grub.htm]("http://www.gnu.org/software/grub/manual/grub.htm")
link as opposed to the first one. Obviously, me and Klipper are having issues today. :-0  . The first link is just redundancy of the second (and appropriate URI), as it is the Grub manual itself.

---

### Post by Sandsound on 2006-06-05
Thanks for the link, but I have allready been starring me blind at that page ([http://www.gnu.org/software/grub/manual/grub.html)](http://www.gnu.org/software/grub/manual/grub.html)).

I cant edit the grub configuration when its a Stage 1.5 error, and if i boot up without the problem-hd (works fine btw...) I cant see what to call the hd, or can I ?

I have doublechecked my jumperconfig on all hd, and still I cant see why it should be a problem that i replace the cd-drive with a hd... Ubuntu is placed on the secondary slave and the extra disk is placed on primary slave, and unpluging/pluging the primary slave shouldnt change the fact that Ubuntu is hdd1 and that its placed on secondary slave... or am I totaly mistaken ?

:-k 

Maybe I should just move my linux-disk to primary-master, and get rid of windoze, after all its just taking up space right now :-)

---

### Post by SkyNet2029 on 2006-06-05
Just a couple of possible ways to get into your system to see just what and where the grub.conf is reporting as your /boot path is 
1.| 
By using a live CD to access the system and then using the CLI and 
#fdisk -l  
to list all partitions on the machine   OR
2.|
Since you said you can boot up without the 'problem' HD, you could access the machine that way and using the CLI do this:
#more /etc/fstab 
to see what your mount points are listed as on the system. Since 
you are only changing the physical media (HD) config and not the actual file system config by booting up this way, it will allow you to 'see what to call the HDD' . 

*Important info: 
The first hard drive is (hd0) and the first partition on the hard drive is (hd0,0)
Where Linux numbering conventions use hda, b, etc, Grub uses 0, 1, 2 etc. Where Linux would indicate the partition with 1,2, et al Grub uses 0,1 and so on. So, the device is written as hdX where X is the number of the device. Counting starts at 0. The partition is hdX,Y where Y is the number of the partition. Again, counting starts at 0. Lastly, the device name is in parentheses and is followed by a comma, then the number of the partition, beginning with 0.
A few examples:
Linux: /dev/hda1 Grub: (hd0,0)
Linux: /dev/hdb2 Grub: (hd1,1)

If this all seems like a headache in the making, and to simplify life, once booted up, as long as you can access the CLI, now would be a good time to 'hit the books' that ubuntu comes with.
$man grub
This pulls up the MANual for grub. You can substitute 'grub' in the line for just about every command in linux and kazaam, up comes the manual for said command. Nifty. Hope this helps.

---

### Post by Sandsound on 2006-06-05
[QUOTE=SkyNet2029]If this all seems like a headache in the making...[/QUOTE]

It shure does :-)

If hda1 = (hd0,0) then hdd1 must be (hd3,0) if I use three hd ?
and if i use four, hdd1 will be (hd4,0) because it is a secondary slave ??

Im not so great with manuals, more of a "trial and error kind'a girl". Most manuals expects the reader to be at the same level as the writer, and because Im new to this Linux-way-of-doing-things, I often run into something thats a bit strange or at least different, took me a while to guess that CLI is the terminal :-)

Will try to poke around with the settings in Grub, and if I cant figure it out, Ill simply remove the windoze disk and place my Ubuntu as a primary master.
But what happens if i remove the boot-drive (hd0,0)... what about Grub... I guess I dont nead it if I run i single OS system, but can my Ubuntu boot without it ?

Anyway... thanks for the help so far

---

### Post by Sandsound on 2006-06-06
Just a little follow-up.

I ended up deleting my windoze-partition and installing a new Dapper on my primary master.
But I have learned a quite few things of all this, thanks for all the help.

---

