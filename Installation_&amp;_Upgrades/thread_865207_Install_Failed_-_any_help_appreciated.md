---
title: "Install Failed - any help appreciated"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by tom1234 on 2008-07-20
I just tried to install release 8.04 onto a computer with Windows XP already installed.  During installation I asked the installer to partition the hard drive as there was some windows data I wanted to keep.  The installation seemed to work, however when I try to boot the computer it:confused: seems to try and boot XP which then immediately fails.  I don't even see the grub menu so I can't ask it to try and boot Ubuntu.  I can run Ubuntu using the live CD and can see both partitions on the hard drive and the data in them so the partitioning has definitely worked.  I tried using Super Grub Disk to reinstall GRUB but that failed too.  The only clue I have is that when I looked in the GRUB directory in root both entries seemed to be for the XP OS!  However I don't know enough about Ubuntu to get any further than this.  Can anyone help - I don't want to be stuck using the live CD.:confused:

---

### Post by tom1234 on 2008-07-20
Update - I reinstalled ubuntu and now the computer no longer tries to boot windows, however GRUB hangs at stage 1.5 with error 2.  Does anyone have any ideas???????

---

### Post by coffeecat on 2008-07-20
How did you format your Ubuntu root partition, with a command line tool, Gparted from the live CD manu, or did you let the installer reformat the partition?

That grub error 2 looks depressingly familiar, but you shouldn't get it if the installer or Gparted does the formatting. [Here's the unpleasant explanation]("http://www.linuxplanet.com/linuxplanet/tutorials/6480/1/"). This may not be what went wrong for you, but if you formatted from a terminal and got an ext3 partition with 256-byte inodes, you've been bitten by the bug that's also plagued some users of several distros.

---

### Post by tom1234 on 2008-07-20
Hi coffeecat thanks for the reply.  Although I have used older versions of Ubuntu for a couple of years I am pretty much a noob as far as my real understanding of Linux goes.  I have been tearing my hair out about this for a couple of days but I don't think that my problem is the one you suggested.  I have been trying to install Ubuntu on an old computer I was given.  I didn't pay much attention to how the hardware was configured but after a lot of confusion figured out that it has two HDs in a RAID mirror configuration.  It seems that this is the problem.  If I unplug one of the HD's (literally) then I can boot Ubuntu from the other with no problems - but the interesting bit is that when I installed Ububtu the installation CD somehow broke the mirroring, one HD has been partitioned and the other hasn't.  I don't understand mirroring all that well but surely this shouldn't be possible?

---

### Post by coffeecat on 2008-07-21
I'm sorry, but I have absolutely no experience of RAID. Since you think that RAID is the problem, can I suggest you start a new thread with RAID in the title? That might attract people who know a thing or two about RAID. The title for this thread was a bit vague. This is such a busy forum that some people just skip over threads with vague titles and look for something that interests them.

There's a psychology to composing thread titles. You need the cunning of advertisers. :)

---

### Post by tom1234 on 2008-07-21
Cheers coffeecat, I think thats pretty sound advice.  I was actually so confused as to what was happening that I didn't know what to put in the title of the thread.  Anyway I figured out how to fix this problem and it was the RAID.  I have a hardware RAID setup on my motherboard so I disabled RAID in the BIOS menu, plugged the HD into an IDE port and everything worked fine - I even managed to recover all the data.  I like Ubuntu a lot but that said an OS install really shouldn't involve having to unscrew the box and do a major hardware reconfiguration.  Maybe I was just unlucky but after searching the forums it seems that some other people have had problems with RAID.  I will call this solved for now as I didn't need the RAID mirroring anyway, if anyone can really shed some light on this please post the info on this thread are there may be others with similar problems.

---

### Post by coffeecat on 2008-07-21
I'm glad you've got it fixed. [ Launchpad Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu/") is another place to see what problems people are having with RAID.

---

