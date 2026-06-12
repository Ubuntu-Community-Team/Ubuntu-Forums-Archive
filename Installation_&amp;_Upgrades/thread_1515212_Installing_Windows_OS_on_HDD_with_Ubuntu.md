---
title: "Installing Windows OS on HDD with Ubuntu"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by Baldrick_NZ on 2010-06-22
Hi all,

Is it at all possible for a hard drive with only Ubuntu on it to have XP also installed as a dual boot?

I know it can be done the other way round, but can it be done where Ubuntu is currently the only OS on the disc?

If windows can be installed along side Ubuntu, this noob would really appreciate some tips please.

Cheers.

---

### Post by Mark1959 on 2010-06-22
I am very much a noob too and an attempting to do the same thing. I have been using Ubuntu exclusively now for over a year but need to keep some windoze fluency so I can use computers at work. 

Th way I am doing it is I have a win7.iso I downloaded from Pirate bay burned to CD and am gonna install on a HDD with my other OSs on different HDDs unpluged. I will then run a fresh install afterwards with all the HDDs pluged back in and let GRUB sort it out for me. Very crude I know and I wouldnt suggest you do it like that just coz I say so since I know from nothing. 

I am sure there are much more elegant ways. I have googled it around and like you struck out however. 

FWIW

---

### Post by varunendra on 2010-06-22
Yes. Resize Ubuntu partition with Gparted, install XP in a partition created in the emptied up space (5GB or more), then reinstall & update Grub/Grub2.

Whether you'll have to install Grub or Grub2 depends upon the version of Ubuntu currently installed (Ubuntu 9.10 onwards uses Grub2).

EDIT: Sorry Mark/Baldrick, I didn't notice Mark's post while posting mine.
You guys don't need to bother reinstalling both OS again. If it is Win7 that you are about to install, then a little precaution is needed in choosing the partition type. Else everything is as simple as told above.

_One more advice_: If gaming or 3D graphics is not what you care about, then perhaps installing Windows **over Virtualbox** is more convenient & safe. However, performance would be much slower than dual boot. Brighter side is: you can use both OS at the same time!

---

### Post by wilee-nilee on 2010-06-22
> **Mark1959 said:**
> I am very much a noob too and an attempting to do the same thing. I have been using Ubuntu exclusively now for over a year but need to keep some windoze fluency so I can use computers at work. 

Th way I am doing it is I have a win7.iso I downloaded from Pirate bay burned to CD and am gonna install on a HDD with my other OSs on different HDDs unpluged. I will then run a fresh install afterwards with all the HDDs pluged back in and let GRUB sort it out for me. Very crude I know and I wouldnt suggest you do it like that just coz I say so since I know from nothing. 

I am sure there are much more elegant ways. I have googled it around and like you struck out however. 

FWIW

Enjoy the rootkits.

---

### Post by darkod on 2010-06-22
Like already said, you need to resize your partition(s) so that you make unallocated space for windows. After that it's best to use Gparted and create primary ntfs partition from that space, especially for win7 because that allows it not to create the 100MB boot partition wasting another primary partition for you.
Then simply start the windows installer and point it to use the existing ntfs partition you created.

If you have a single hdd grub2 on the MBR will get overwritten by windows bootloader, so don't get freaked out when you see windows booting directly. Some people install ubuntu again straight away just to get grub2 back, and create further mess with that.

Reinstalling grub1 or grub2 instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Watch out which version you use and which liveCD to use.

---

### Post by coskierken on 2010-06-22
If your system is robust enough (3Gigs ram+), I would use VMPlayer (free) and create a virtual Windoze machine.  You don't have to reboot if you need use Windoze for normal activity (not games... well not intense 3d games).  I have dual boot with Win7 (to play games) and Ubuntu 10.04 and then still have Win7 run virtually if I want to do certain task without rebooting (I have not quite got down the settings to print CDs on the epson in Ubuntu :confused:).  The unity function on VMPlayer is great!  I have been able to use Win7 virtually with full functionallity (internet, network, printers, etc).  Good Luck! ):P

---

### Post by Baldrick_NZ on 2010-06-24
> **darkod said:**
> 

Reinstalling grub1 or grub2 instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


Thanks for that.

Ok, so I've got all the way through to successfully installing XP along side Ubuntu 10.04.

I followed the instructions on the link above implicitly, but now on boot I get this very annoying message:

"Minimal BASH-like line is supported. (Then goes into various options when you hit TAB. None of which make sense to this noob, though I tried a few.)

GRUB >"

What's that all about? How to I actually get this to preform properly by giving me the option of which OS I'd like to boot from?

Really need help fast on this, as I'm wanting to watch NZ play Paraguay in just over 2 hours from now. And guess what? My PC is my TV!

Any help would be greatly appreciated!

PS: I'm currently using LiveCD from Shipit to write this from.

Below is the sudo fdisk -l I get, if it's any help...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000692ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       56602   454654541   83  Linux
/dev/sda2   *       56603       60427    30724312+   7  HPFS/NTFS
/dev/sda3           60428       60802     3005441    5  Extended
/dev/sda5           60428       60802     3005440   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by darkod on 2010-06-24
If you had extremely bad luck, the root partition might have been corrupted when resizing it. That's why I try to always plan if possible, and not resize anything later.

From live mode, try reinstalling grub2 again with:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If that doesn't work to get ubuntu running, also from live mode try to run a check on the partition:

sudo fsck /dev/sda1

---

### Post by Baldrick_NZ on 2010-06-24
Sorted. 

Re-ran the final script again, and it now works fine. Phew! Just in time for the footy. GO THE ALL WHITES!

---

