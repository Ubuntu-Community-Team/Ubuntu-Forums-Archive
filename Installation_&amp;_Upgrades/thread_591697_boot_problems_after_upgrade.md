---
title: "boot problems after upgrade"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by thanato5 on 2007-10-25
I have encountered an interesting issue.  Maybe someone could help me out.  I have an 250 GB IDE hard drive dedicated to storing a little over 100 Gig of MP3's (all legitimately grip'd off of CD's b.t.w.)  My processor fan died and the processor fried.  I put the HD in a Compaq Presario SR1675CL, booting off of the SATA drive that came with the compaq.  I installed ubuntu 7.04 (on the SATA drive) and everything worked GREAT.  7.10 came out and, since I enjoy editing music, I tried to run a fresh install of Ubuntu Studio 7.10.  I chose to just wipe that drive and run a fresh install because I hadn't really installed anything over the base system.  I kept getting an error about an incompatible file system on my IDE/Music drive.  I ran fsck on said partition and it said the drive was clean.  I ran fsck -f and it found no problems.  I continued with the installation.  When I rebooted after that install, grub would pop up, but when I selected the system to run, I got "Error 22: no such partition"

I swore quite loudly and tried putting the studio install disk in to see if I could reload grub.  It flashed something on the top of the screen too fast for me to read and popped up to grub with the same issues.

I swore loudly again and punched my monitor, bruising my knuckles.  I re-installed 7.04 only to have the same grub issue.  At this point, I went outside and beat on my pell for 20 min. or so with a piece of rattan, realizing I didn't want to hurt myself or my computer any more than I already had.  I then had a nice stiff drink.

I put the 7.04 live-cd in and booted the PC and booted it up until I got to the cd's boot option screen and realized I should write down my grub config info, so I selected "boot from first HD".  I wrote everything down and bumped the "b" key (boot).  Strangely, Ubuntu 7.04 booted off of my SATA drive fine.

Any clue why when I boot without the CD I get an Error 22, but when I put a live-cd in and select the boot from HD option it works without fail?  Backing up my mp3's is problematic because I don't have 146+ blank CDs, so how do I fix it without losing my data?  Is there any way I could make punching my monitor less painful?

---

### Post by thanato5 on 2007-10-25
*update*  I changed a boot parameter in grub--the boot partition was (hd1,2) and I changed it to (hd0,2) and it worked!  I guess the CDROM was taking the place of hd0 but why?  It's still an interesting question.  when I "sudo grub" and then "find /boot/grub/stage1"  it still says "root (hd1,2)".  Why and is this gonna cause me problems in the future?

---

