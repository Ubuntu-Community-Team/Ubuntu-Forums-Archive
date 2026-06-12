---
title: "Stuck at partitioning"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by xmastree on 2006-07-02
So, I'm trying to install Dapper on my dad's new(ish) computer. It's not that new, it's an athlon 800/256 which ought to be good enough. The live session comes up ok, although it's very slow.
However, when I go for the install and eventually reach the partitioning, it always stops dead at step 5/6 after I tell it which disk to use (in this case, erase the entire hdb). Well, it doesn't stop dead, the disks rattle for a while but nothing else happens. Then it freezes. I waited hours, just in case it was being really slow.

Is there a non-graphical install? That may help. This graphical-only thing is awful compared to previous releases. I'm sure that's been discussed to death, but I've been away for a while and dad's on a dial-up (which makes it a complete pain to search the forums too...).

---

### Post by confused57 on 2006-07-02
You probably need the Dapper-alternate CD, but since you're on dial-up it's probably out of the question to download.
I read on another thread, that you can press "Esc" after pressing the install icon on the live cd & it will bring up a text-based installer...I don't know, I haven't tried it.

---

### Post by highfructosecorn on 2006-07-02
i am having a similar issue but i have tried both the graphical and text based installs off the dvd. there are a couple of similar threads with suggestions ranging from "repartition your drive" to "youre hard drive is broken" and a couple other tips but no one has confirmed if any of these have worked. Did breezy have any trouble like this?

---

### Post by xmastree on 2006-07-03
Hmm... I thought the alternate CD was for upgrading.
As for repartitioning, originally the drive containeda Win98 installation, and it was the only drive in the conputer. I removed it from that and installed it as a primary slave in the new one, primarily to retriece his documents etc.
I have deleted the partition using fdisk, but that didn't help.

Rats! If only I had known, I have 5.04 installation discs at home (philippines) but I didn't bring them with me as I didn't realise i would need them.

I'll try the 'Esc' thing, but what I really want to do is install without loading the desktop at all, thus giving more resources for the installer.

---

### Post by Skeptik on 2006-07-03
I'm having a similar problem. I can get the live CD to load (after a while of waiting) but selecting 'install' from the GUI starts working until it reaches part3 (keyboard layout selection). I then get a perpetual revolving beachball.

I tried Dapper Server edition which worked fine. I then loaded Gentoo and Mepis, which seemed to work well as live or disk installs.

Whoever setup the install of DAPPER needs his bum kicked - and hard!!

I then decided to see if I could reload Windowz XP and start again. For some reason Dapper HAS to load the LIVE CD first - before you can install to disk ...WHY?? On a slowish PC this is just a time-waster. Why not just have another menu option - Install to Disk?:confused: 

It seems testing is down to those who took the trouble to get it off the toaster and stick it in their drives.

---

### Post by houstonbofh on 2006-07-03
The "alternate" install is simply a non-graphical installer.  They push the graphical live CD because it is easier for most people.  Also it is one CD to test, show off, and install.  But it is a poor choice for some hardware.  They did state this, but they could have been clearer.

---

### Post by xmastree on 2006-07-04
Is there a way to kill the desktop (killall gdm?) and run a command to install it?

---

### Post by six on 2006-07-04
Have you tried partitioning the disk before you try installing Dapper?

I use Partition Magic to set up partitions for all my distros (up to 13 of them).

Select the "Custom" radio button when you get to Dapper's install screen, then setup your mountpoints manually for swap /boot and / etc. (If you're dual-booting, you really only need two; swap and / but if you're multi-booting it's probably better to have /boot on it's own partition).

Blank out all the other partitions you don't want Dapper to know about, by scrolling up to the first blank line for both mountpoints and partitions.

I tried using the Alternate installation CD, but didn't have any luck with it at all. (I think it died on me half way through).

One thing to be aware of - Ubuntu's graphical partitioner can only cope a maximum of 13 partitions (12 preferably), as it doesn't have a scroll bar.

If you don't have Partition Magic, you could try using qtparted off a rescue boot CD:

[http://www.sysresccd.org]("http://www.sysresccd.org")

(Type *run_qtparted* to start it.)

---

### Post by xmastree on 2006-07-04
[QUOTE=six]Have you tried partitioning the disk before you try installing Dapper?[/QUOTE]That's my next approach. I used gparted from the live to create just two partitions, 5.8GB hdb1 ext3 and 512MB hdb2 swap.
To my surprise, it used the swap when rebooted, which makes it more responsive. However, it still seem to fail at the same section. 5/6.

I opted for manual partitioning, figuring I could just tell it what to use (hdb1 for root and hdb2 for swap). The screen came up advising me to make sure I have minimum 2GB for root and 256MB for swap (I have) and I clicked next.
The window eventually disappeared before I had chance to select anything...

Afraid that it might try to use hda (the windows installation) I reset it and made sure it hadn't. Phew.8-[ 

So, now I shall physically remove hda just to be on the safe side, and try again...

---

### Post by xmastree on 2006-07-04
Nope, It got further, but refused to go beyond the partitioning stage. I was able to tell it what to use, but it just sat for an hour with the disk lights flickering and became completely unresponsive.[-( 

I thought dapper was supposed to be the best so far?

Strange thing is, on the disc cover it states **'fast graphical installer on the Live CD'**

Yeah, right. :evil:

---

### Post by six on 2006-07-04
I had a similar "stuck" issue with the Ubuntu alternate CD, but have had no trouble with any of the four graphical installers (Ubuntu, Kubuntu, Edubuntu or Xubuntu). They all use the same installer, so if one didn't work for you, the others probably won't either.

A couple of suggestions:

Send for a free copy of the "alternate" Ubuntu CD. That's a text based direct-installer, so you might get further with that. The end result is a full install of Ubuntu, just the same as the graphical live-installer. It won't cost you anything, but you might have to wait a while for it.

Buy a cheap distro DVD package from a Linux e-tailer, one that has several different distros for you to try. Or look for a magazine in a shop with a cover disc. Linux Format had a Fedora Core 5 DVD on it a couple months back.

There probably isn't a single Linux that suits everybody, or will run on practically all hardware. I suspect Dapper's no better or worse than any other in that regard - but the support for it does seem stronger than most, which is a major plus point.

All you can do is try as many distros as you can, or just keep using live CD's, such as the Ubuntu's or Knoppix.

---

### Post by six on 2006-07-04
I don't know if this is any help, but have you tried ticking/checking the "Reformat" box for both hdb1 root and hdb2 swap?

You should only be able to see the two mount points in the list:

```

swap    512Mb   Partition 2 Disc IDE/ATA (Logical) [hdb2]   Y
/       6Gb     Partition 1 Disc IDE/ATA (Logical) [hdb1]   Y

```
Blank everything else out.

If you tried assigned logical drives, try changing them to primary - or vice versa.

The next screen, "Ready to install" (Step 6/6) should come up fairly quickly after you press [Forward].

Make sure you *firmly* press the [Forward] button each time, too. (It's caught me out a few times!)

---

### Post by Skeptik on 2006-07-04
I grabbed the Alternate CD for 6.0.6 off the toaster and tried it. It seemed to get further but I just got the following error:
file:///cdrom/pool/main/u/util-linux/bsdutils_2.12r_4ubuntu6_i386.deb

I selected "ignore" and I got another one etc., but I didn't bother writing more down.

I've given up on this release. I think it is just rubbish! If Simply Mepis works perfectly - why does Ubuntu choke all the time? I'd rather have Ubuntu working but now I'm going to try Suse.

---

### Post by wpshooter on 2006-07-04
Maybe I missed it, but if this is a burned CD of Ubuntu have you checked the integrity of the CD by verifying the sum totals (in the menu at the initial boot of the live CD) ?

---

### Post by xmastree on 2006-07-05
[QUOTE=six]I don't know if this is any help, but have you tried ticking/checking the "Reformat" box for both hdb1 root and hdb2 swap?

You should only be able to see the two mount points in the list:

```

swap    512Mb   Partition 2 Disc IDE/ATA (Logical) [hdb2]   Y
/       6Gb     Partition 1 Disc IDE/ATA (Logical) [hdb1]   Y

```
Blank everything else out.
[/QUOTE]
That's as far as it got. hdb1 was checked, hdb2 wasn't. I pessed forward hard enough to grey it out, then it just rattled for an hour but achieved nothing.

The CD is ok, I checked it. It's a magazine (Linux user) coverdisc.

I've asked a friend to burn some 5.10 discs for me, I'll try that instead.

---

### Post by xmastree on 2006-07-08
Houston, we have lift off...

Some nice kind person sent me some 5.10 CDs, and all's well. Now for the fun, getting the modem to work...

---

### Post by foov2 on 2006-07-08
I also had the problem with partitioning.  So, I went into manual and deleted all the partitions on the disk.  Then, I reboated and it worked.  For me, the automatic partitioning was having problems deleting the old partitions.  fwiw.

---

