---
title: "Post Ubuntu Install Headache"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by Maelstrom65 on 2005-04-22
I installed Ubuntu on my C: drive alongside WindowsXP Home.  The install went off smoothly and Grub was installed in the MBR as my bootloader.  When I restarted my computer to complete the install, I got "error loading operating system".

I booted to the windows recovery console and did a "fixmbr" and a "fixboot" but that didn't work.  I tried re-installing windows (no effect) and then reinstalling Ubuntu (with LILO as boot loader this time)...still nothing.

I can still see the data on the C: Drive, but I can not boot from it.  I even tried making my other hard drive the boot drive by changing around the settings in my BIOS (the drive/partition was Active and bootable) and then I was going to run "bootcfg /rebuild" to get windows to write a new boot.ini file pointing to my windows installation.

Upon rebooting with the new config, I was suprised to see LILO kick in and Ubuntu booted.  Great, except I didn't install Ubuntu on that drive nor did I put LILO on it.  To top it off, when Gnome starts, I just enter in my username and password and Gnome then restarts...over and over again.  I can't get into Ubuntu to do anything.

I just ran fdisk.mbr from my win98se startup disk to see if that might do anything as I've run out of other options...and upon rebooting the error message has changed to "missing operating system".  So now I'm doing the fixmbr, fixboot and rebuildcfg commands one more time.  I thought I'd try this forum so to see if anyone else had any ideas.

Any help would be much appreciated...

Cheers

---

### Post by Levander on 2005-04-23
I would be surprised if LILO got there by itself. 

I'm wondering if you didn't misunderstand the prompts on the setup process?  /dev/hda is the disk that's plugged into the connector on the end of the primary IDE cable.  This makes it the primary master.  /dev/hdb is the disk thats plugged into the connector that's closer to the middle of the primary IDE cable.  This makes it the primary slave.

/dev/hdc is the secondary master - plugged into the connector on the end of the secondary IDE cable.  /dev/hdd is the secondary slave.

Whether the IDE cable is for the primary IDE devices or the secondary IDE devices depends upon where the cables are plugged into your motherboard.

Hope this helps.  I'm really kind of guessing as to what the problem is, so I don't know that it will.

Good luck.

---

### Post by Maelstrom65 on 2005-04-23
Oh ya, I understand all that.  In fact, during the install process, Ubuntu showed me all my disk's and the partitions on them so it was easy to pick which one I wanted...and it was the hda drive (C drive)...the drive I am finding LILO on is actually a SATA drive on a secondary SATA controller card (My MB has a controller built in as well)...so this facet of the process remains a mystery.  Thanks for the response though.

Cheers

---

### Post by mudra on 2005-04-23
I had the same problem with a Fedora core installation, the problem comes from error messages that get put into the MBR by mistake. If you have a live CD that you can boot from it is possible to remove them.

I used the following command I found someplace, it worked for me but I cannot guarantee that it will work for you.

sfdisk -d /dev/sda | egrep -v '^(Warning|DOS)' | sfdisk --no-reread -H255 /dev/hda

This reads the current geometry from the disk with sfdisk, strips out any superfluous warning information with egrep and writes it back to the disk with a corrected heads value.

For more information see [http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/) (Its about Fedora Core installation but has information on problem MBR's).

Hope that this helps, but please remember, there are no guarantees that this is the problem that you have, and that this will cure it. I only know that it worked for me.

Hope that this helps you.

Mudra.

---

### Post by tread on 2005-04-23
Wasn't there some problem with ubuntu and SATA drives? I seem to recollect reading something about it .. some guy said that what he had to do was disconnect the SATA, install ubuntu and then reconnect the SATA drive. Try searching for that and seeing if you have the same problem.

---

### Post by Maelstrom65 on 2005-04-25
Thanks for the assist guys...I appreciate it.  Unfortunately, after much hair pulling and gnashing of teeth trying out different fixxes and suggestions, I couldn't wait any longer and ended up reinstalling WinblowsXP on another drive and basically starting from scratch.  I can still access the old drive, I just can't boot from it.  Ubuntu is still there and maybe one day I'll get it running.  Thanks again for the help.

Cheers

---

### Post by Maelstrom65 on 2005-04-28
Well, as if this saga wasn't strange enough, it just got even stranger.  After giving up trying to boot to that drive and re-installing XP on another drive...reinstalling all my apps and generally getting things somewhat back to normal, I thought I'd try one more time to boot to Ubuntu on the old drive before getting rid of the partition completely.  

Well, wouldn't you know it when lo and behold, Grub started up and gave me the option of loading Linux or (the now non-existant) Windows XP.  I picked Linux and was presented with the Ubuntu desktop (I think it's GDM).  My only problem now is that GDM keeps restarting on me every 30 sec or so.  Just enough time to type in my username and password and have the desktop start up.  It's constant....

Any ideas as to what might be causing it?

My system is a P4 2.6Ghz, 2Gb RAM, ATI Radeon 9800 Pro (dual monitors...1 LCD, 1 CRT)

Be gentle as I am relatively new to Linux. I've used Red Hat and Mandrake in the past and had some experience with SCO and Solaris Unix as well.  Nothing realy in depth.

---

### Post by jonny_boy27 on 2005-05-23
i also have this problem except that i have windows and ubuntu on separate disks and i installed GRUB not LILO. i tried mudra's advice using a knoppix cd (replacind dev\hda with \dev\hdc - where ubuntu is installed) but bash threw up "access denied" errors. can anyone shed any further light on this?

---

### Post by aveline on 2005-07-26
[QUOTE=jonny_boy27]i also have this problem except that i have windows and ubuntu on separate disks and i installed GRUB not LILO. i tried mudra's advice using a knoppix cd (replacind dev\hda with \dev\hdc - where ubuntu is installed) but bash threw up "access denied" errors. can anyone shed any further light on this?[/QUOTE]

The only way I found to cure this was use an MBR tool from the ultimate boot disc & make my xp partition active again.  For some god knows what reason, ubuntu made the xp partion inactive!  I had to reactivate it but i'd tried all the other fixes the original poster said above BEFORE i remember this one might work... so when it booted finally, it installed xp in repair mode. *sigh* I didn't lose anything cept a few hours of headaches.  I know i'm late to this thread but I hope it helps someone else.   I posted about this problem on this forum as well a few days ago.

Aveline

---

