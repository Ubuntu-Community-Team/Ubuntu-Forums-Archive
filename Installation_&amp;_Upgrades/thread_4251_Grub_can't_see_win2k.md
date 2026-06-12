---
title: "Grub can't see win2k"
date: 2004-11-13
forum: Installation &amp; Upgrades
---

### Post by bubbamctavish on 2004-11-13
Hi there...

I'm not sure if this was posted before, but i did search the forums and found nothing....maybe someone could point me to the correct thread if possible. Thanks.

Several days ago i decided to install a dual boot with windows 2000 and linux (ubuntu was recommended by a friend of mine). Having never used linux or set up a dual boot before I decided to try it out. So i formatted my computer (after backing up the necessities).

I've partitioned my drive in half. 20Gb for win2k on fat32 file system and another 20gb for the linux installation supposedly for the ext3 or unpartitioned space (when i format it linux installation begins). So after about a 10 minute installation procedure (downloading updates, unpackaging etc.) I can log into Ubuntu and use it fine but when i reboot it automatically loads the linux distribution. When i load the boot menu, it doesn't show windows. I'm assuming the problem is in where, in the partition menu during setup, i specify the mount point. I've tried using "/windows", "/dos", and "/winnt" (the latter being a manual input) but to no avail.

I installed win2k first and when I insert a floppy boot disk during bootup i can see that the win2k installation is still there in the C:\winnt folder. (I used all the default options when installing win2k). 

Any help would be appreciated; this is my first time installing any linux distribution and I was hoping to try it out. 

Thanks

---

### Post by wfx on 2004-11-13
ho does you /boot/grub/menu.lst look?

for windows there should be anything like:
...
title Windows
rootnoverify (hd0,0)
chainloader +1
makeactive
...

---

### Post by bubbamctavish on 2004-11-13
[QUOTE=wfx]ho does you /boot/grub/menu.lst look?

for windows there should be anything like:
...
title Windows
rootnoverify (hd0,0)
chainloader +1
makeactive
...[/QUOTE]
 Thanks.

I edited the menu.lst file under the linux load terminal editor thingy (still new to linux) and when I rebooted I had to edit the command line in the boot manager editor manually to what was above. 

Having accomplished that I've received two different outcomes (the latter of which I received after rebooting from the first):

-I was taken to a command prompt "grub>" with a bunch of available commands like root, rootnoverify, boot etc., stating that grub was capable of low/high? bit interfacing of somethng; i can't remember. 

-After rebooting, when i selected windows from the boot menu it just blinked and didn't change. I could do this an endless amount of times. I noted that the command lines had also changed again. When i edited those with the command line editor and exited the changes were erased and reset when i returned to the main boot menu....

I'll probably just format/remove all partitions and install win2k only...i've downloaded a tutorial on how to install linux and win2k on a dual boot but it was for a redhat distro, which is similar (i'm assuming). But i've spent many hours trying to fix this problem in the last few days (at least 8 hrs now) and I think i need a break. I'll try it again some other time.

Thanks for your help.

---

### Post by TravisNewman on 2004-11-13
You need to go into your bios and set your hard drive to LBA access. It's probably on auto right now. Don't give up just yet :)

---

### Post by Magneto on 2004-11-13
are you sure you have grub looking at the right partition?
is your windows partition the first partition on the first ide drive on the first controller?

grub isnt seeing your windows partition - you dont need to delete anything- you just need to figure out where your partitions are and tell grub the correct info- besides- every will tell you to install windows first then install linux unless you plan on using system commander or bootmagic instead of grub

whats listed when u type 

sudo cfdisk



grub is letting you manually enter/edit your boot options it does not save these changes to /boot/grub/menu.lst
please reply with your disk partition layout -  hda1 = reiserfs hda2=swap etc and we can get you up and running

---

### Post by guyran on 2004-11-22
I had the same problem as the originator of this thread, as my working W2k partition became unusable after a Ubuntu installation because the Grub config could no longer allow me to start Windows. I think it is due to an alteration in the partition table where Ubuntu took a chunk out of the first Win partition instead of taking space at the end of the disk. As a result, I have two W95 FAT32 (LBA) partitions separated by a Linux partition and with the swap partition at the end.
The persistent message on trying to boot from Windows was NTLDR missing so I tried some of the procedures I found elsewhere on the Net concerning this problem and ended up with no access to either W2k or Ubuntu.
Restoring the MBR with a W98 floppy has left me with messages about corrupt system files in the WINNT directory. I can only start the computer using Tom's ROOTBOOT floppy, so at least I hope to save something of my W2k installation, but I can't say I was pleased with the Ubuntu installation procedure leaving me in this mess. My fault for not backing up everything on my Win partition I suppose.
But it's a pity that someone doesn't put a message about these problems - with a warning to imprudent users like myself that a Ubuntu installation can make your W2k or XP partition inaccessible.
 ](*,) 
guyran

---

### Post by Magneto on 2004-11-22
It's not Ubuntu's fault that you chose not to read up and understand everything you were doing.
Grub will install to the MBR -which won't hurt any Windows installation- You just did something wrong. 

Please don't blame Ubuntu for your lack of knowledge or planning.  Most people who use Linux have gone through the learning process. It is essential to figure out how you will layout the partitions in a dual boot system PRIOR TO INSTALLATION.  It also helps to find out as much as possible about ANY SOFTWARE YOU INSTALL on your system, if you care about that system.
Lastly, NEVER EVER do such potentially harmful things to your pc without having a full backup of critical data.

Read [http://www.ubuntulinux.org/legal/view?searchterm=disclaimer](http://www.ubuntulinux.org/legal/view?searchterm=disclaimer)

[B]

Disclaimer

This website and all information, products and services on it are provided on an “as is” basis, without warrenty of any kind, either express or implied. Your use of this website is at your own risk. Canonical Ltd. disclaims all warranties, express or implied, including without limitation, warranties of merchantibility and fitness for a particular purpose.

Canonical Ltd. disclaims liability for any direct, indirect, incidental, special, consequential, exemplary, punitive or other damages, or lost profits, that may result directly or indirectly from the use of this website and any material that is downloaded or obtained throught the use of this website.

This includes, without limitation, any damage to computer systems, hardware or software, loss of data, or any other performance failures, any errors, bugs, viruses or other defects that result from, or are associated with the use of this website.[/B]

---

### Post by famic on 2004-11-25
I am having the same problem after installing Ubuntu on 2 dual boot boxes.

I fixed it on one of them by setting LBA mode instead of AUTO in the bios, but the other is a laptop and its bios doesn't allow such option. 

Isn't there something i could do in /boot/grub/menu.lst to make it work?

Or some other solution ?

Looking for infos, i found many having the same problem, but barely any answer...Suse offers a fix for its distrib it seems, but i dunno how i could use it here.

Any help would be much appreciated   :-k

---

### Post by wallijonn on 2004-11-25
A temporary work around may be to create a GRUB boot floppy (I just wrote a HOWTO in the HOWTO/FAQ section), then boot from the WXP CD, f8, Recovery Console -> fixboot to have it re-write a new MBR. You would then boot without the GRUB floppy to boot into WXP and boot with the GRUB floppy to get into Ubuntu.

---

### Post by Scuzzy on 2005-01-06
[QUOTE=Magneto]It's not Ubuntu's fault that you chose not to read up and understand everything you were doing.
[/QUOTE]
That's a bit harsh.  FWIW, here's my little story on this :
I just built a new PC, and am playing with quite how I'll lay it out, and which OS's I actually want on it, but for starters I decided to put Win2K in partition 1 (/dev/hda1), and then install Warty Warthog in partition 2 (/dev/hda2).   I'm afraid the Warthog installer just stomped over my MBR without so much as a by your leave.  This is **not polite**.   I've been using Debian for years, and it *never* did that to me - Debian *always* asks you if it's okay to install its bootloader in your MBR, and if not then where would you like it ?

What's worse is that it tried but  **failed** to install Grub in my MBR (it reported the failure) and that failure is what killed my MBR (==> "Error loading operating system" when I try to boot from the HD) - all without any warning.

It's okay though - I hadn't got very far with the Win2K install - I'll just install it again, but this time I'll add Debian.

[QUOTE=Magneto]
Grub will install to the MBR -which won't hurt any Windows installation- You just did something wrong. 
[/QUOTE]
No - it's wrong for Ubuntu to install its own bootloader over the top of whatever bootloader I may already be using, without even asking whether I'd like it to.

[QUOTE=Magneto]
Please don't blame Ubuntu for your lack of knowledge or planning.  
[/QUOTE]
Sure - that wouldn't be fair at all - but I can and shall blame its installer for being unfriendly or impolite.

[QUOTE=Magneto]
Most people who use Linux have gone through the learning process. 
[/QUOTE]
Oh yes - many times  8-) 
It's certainly educational.

[QUOTE=Magneto]It is essential to figure out how you will layout the partitions in a dual boot system PRIOR TO INSTALLATION.  It also helps to find out as much as possible about ANY SOFTWARE YOU INSTALL on your system, if you care about that system.
[/QUOTE]
Couldn't agree more - my mistake for just diving straight in I guess - but this experience has surprised me - I expected better testing from the developers.

[QUOTE=Magneto]Lastly, NEVER EVER do such potentially harmful things to your pc without having a full backup of critical data.
[/QUOTE]
Well yes, can't argue with that ... unless it's just an experiment of course ;-)

Cheers
Scuzzy

---

### Post by Magneto on 2005-01-07
look before you leap
Installing an alternate OS is not formatting a floppy

ROB

Read Or Bleed :) aka RTFM

---

### Post by phpman on 2006-02-28
I had this same problem. I tried altering /etc/fstab and /boot/grub/menu.lst to no avail. My friend, an Ubuntu expert told me to try this:

Set your bios to the next drive letter after C: and boot. Since my 2 CDs are E; and F:, I set the first boot device to D: and it booted windoze, pretty as you please!

In my case, C: in Bios was assigned to the Ubuntu drive and Win2k was assigned to D:.

Good Luck!

-phpman

---

### Post by OZSYD on 2007-03-16
I am very new to Linux and only last week I installed Edgy (still Canon 1120 printer and canoscan 5000F are not operational).  I had a dual boot with WIN98 and WIN2K  and I installed Ubuntu on top of that.  I don't know what has gone right but I can boot up with all the three OS without any problem. 

Some specifics:  I had used Partition magic (on WIN98 ) to partition the hard disk before installing the Win2K.  Hence the partition table could be different from raw windows installation.   
Win2K is on partition 7 and not on a primary partition.  While installing Ubuntu I did not select the manual partition option and let the Ubuntu installer create whatever partitions it needed. 

All these are not very useful but if any of you want to investigate this further, just send me the command that I should type on the terminal and I will post the output here. 

What am I doing in this thread if I have no problems?  I thought I will clean up the PC and just have Win2k (I want to print and scan) and Ubuntu only and scanned for related info.  After seeing the info here I have decided to postpone the clean up.

---

