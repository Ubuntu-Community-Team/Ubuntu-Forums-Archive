---
title: "Grub error : no such partition"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by pauljwells on 2010-04-29
I have an HP desktop machine which had a clean installation of XP and a recovery partition:

D: recovery partition is sda1 (FAT)
C: XP partiton is sda2 (NTFS)

I did a 'vanilla' install of Lucid as 'side by side', which has created a logical partition sda3 with / on sda5 and swap on sda6

When I rebooted after the install I get to grub rescue with an error : no such partition.

ls gives:
(hd0) (hd0,2) (hd0,1)

each of these gives 'unknown file system' if I try to ls (...)/

I have booted from live CD and run grub-install, following this thread [http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

No change

I can't find anything on the web that addresses this particular scenario that I can use.
I just spent two solid days reinstalling XP after a similar problem trying to upgrade from Karmic to Lucid and really don't want to have to go through all that again.

If I try to boot windows using the fixntlldr CD I get hal.dll corrupt or missing...

How can I get grub to see my linux partition?

---

### Post by RJARRRPCGP on 2010-04-29
> **pauljwells said:**
> 

If I try to boot windows using the fixntlldr CD I get hal.dll corrupt or missing...


Please check the HDD. You may have bad sectors.

---

### Post by Improviz on 2010-04-29
I've had luck using gparted from the Live CD to move the existing partitions "over" just a bit. Alll booted fine after that. Just a thought. I don't think it will kill your Ubuntu install, not sure about Win.

---

### Post by bumanie on 2010-04-29
Go to [this page]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305") and then scroll down to point 15 - it gives instructions to operate in grub_rescue. Hope it helps.
*Just saw the above post - I would not use gparted to do that if I were you.

---

### Post by pauljwells on 2010-04-29
Already tried something similar and the problem is I can't even find those files from the grub rescue prompt.
I DID find in the Ubuntu Doc official guide that you should resize the xp partition and then reboot windows so that the windows bootloader can update its partition table, but since I used the automagic resize during the install this obviously didn't happen. Looks like a nasty bug to me... I've already done yet another XP reinstall and am now trying to resize the partition from the liveCD then rebooting XP, then installing to see if the theory is correct. If so. Launchpad gets a visit...

---

### Post by infamous-online on 2010-04-29
> **pauljwells said:**
> I have an HP desktop machine which had a clean installation of XP and a recovery partition:

D: recovery partition is sda1 (FAT)
C: XP partiton is sda2 (NTFS)

I did a 'vanilla' install of Lucid as 'side by side', which has created a logical partition sda3 with / on sda5 and swap on sda6

When I rebooted after the install I get to grub rescue with an error : no such partition.

ls gives:
(hd0) (hd0,2) (hd0,1)

each of these gives 'unknown file system' if I try to ls (...)/

I have booted from live CD and run grub-install, following this thread [http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

No change

I can't find anything on the web that addresses this particular scenario that I can use.
I just spent two solid days reinstalling XP after a similar problem trying to upgrade from Karmic to Lucid and really don't want to have to go through all that again.

If I try to boot windows using the fixntlldr CD I get hal.dll corrupt or missing...

How can I get grub to see my linux partition?

My guess sounds like you didn't install the grub installer, did you accidentally uncheck it by mistake?

---

### Post by pauljwells on 2010-04-29
Read the thread. I installed grub once during install then twice manually.

Anyway. I just tried plan B: make space on the drive, reboot windows a couple of times to run chkdsk and then install lucid on the continuous free space. This time I just get a flashing cursor, no grub, nothing.

Supergrub CD just booted windows :) Looks like I'll be trying Acronis next

---

### Post by slvr42 on 2010-04-29
I had this happen when I switched the HD my OS was on.  I had to boot up gparted live and format the entire partition as ext4 or whatever fs you are using and reinstall.

---

### Post by pauljwells on 2010-04-29
God I hate GRUB!!

---

### Post by pauljwells on 2010-04-29
> **slvr42 said:**
> I had this happen when I switched the HD my OS was on.  I had to boot up gparted live and format the entire partition as ext4 or whatever fs you are using and reinstall.

That's really not encouraging :(

I'm not a n00b, I've been using ubuntu since 5.04 I've never had this much trouble before!

The main trouble is I've not found a single post or document that gives a simple, sensible explanation of what grub does, where it sits, how it interacts with the windows loader. There's just a mass of contradictory detail or 'fixit recipes' that don't work...

hohum, I know, I should write it myself...

---

### Post by slvr42 on 2010-04-29
I know you probably already looked at this, but your root partition is bootable right?

---

### Post by pauljwells on 2010-04-29
yes :(
Not even Acronis worked. Normally rock solid, but I'm trying to do it the pure linux way.

I found one little gem though, 

[http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx]("http://www.sysint.no/products/Download/tabid/536/language/en-US/Default.aspx")

MBRFix! I boot into xp using the supergrub live cd and then run this command to repair the MBR and return to single boot.

---

### Post by pauljwells on 2010-04-30
I'm beginning to wonder if Grub2 has problems with extended partitions when there's a recovery partition (in my case 5GB) on the first partition...
My next plan is to manually set up primary partitions for / and swap then install and see if that works. After that I give up and try wubi

---

### Post by wilee-nilee on 2010-04-30
> **pauljwells said:**
> I'm beginning to wonder if Grub2 has problems with extended partitions when there's a recovery partition (in my case 5GB) on the first partition...
My next plan is to manually set up primary partitions for / and swap then install and see if that works. After that I give up and try wubi

Post this boot script in code tags please.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pauljwells on 2010-04-30
> **wilee-nilee said:**
> Post this boot script in code tags please.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Too late :(
I'm just in the middle of reinstalling 300MB of XP updates.

Are you a grub expert? What would you recommend I do? I'm reluctant to try any of the things I did before and there are enough threads of Grub problems on this forum to make me think there's something very wrong

---

### Post by wilee-nilee on 2010-04-30
> **pauljwells said:**
> Too late :(
I'm just in the middle of reinstalling 300MB of XP updates.

Are you a grub expert? What would you recommend I do? I'm reluctant to try any of the things I did before and there are enough threads of Grub problems on this forum to make me think there's something very wrong

No I'm not a expert, but remember that when you see problems on this site, that this is a site to come to when you have problems, so a cause and effect=grub is messing things up is anecdotal evidence. Most of the time it is user error in the end, hey it is alright we all do this on occasion. 

The best way to do a dual boot is to have the XP in it's partition leaving a unallocated space for the Ubuntu install then choose install in empty space. But you want to make sure that you don't have to many partitions already so that it gets borked.

Grub is quite easy to manipulate if you know what your doing. 

So if you want to install Ubuntu again, post before doing so with a screen shot of the the HD from gparted on a Live CD, and or a run sudo fdisk -l from a live CD  l=small case L. It just takes a few times to get the trick of multi booting OS's.

---

### Post by pauljwells on 2010-05-01
Thanks for that :)
I wasn't doubting your ability to help, I was just curious as I think I could use a Grub expert right now! I'm quite happy to hack a system and I also code, so I'm not inexperienced, but I'm starting from zero with the whole grub/mbr thing.

The point is I have done many installs of many linuxes, and all Ubuntus from 5.04 onwards on this very machine, and always by doing as you said. Make an empty space on the HD, reboot Win to run chkdsk and then back to the installer to use the 'largest continuous space' option. I never had a single problem rebooting anything before, including Karmic with Grub2 so even that can't be the problem.

I just finished reinstalling XP, this time making a proper backup image ;) , and I installed Lucid on a USB HD I had lying around, that apart from a slow bootup, runs amazingly well.

I guess I'll try and do a proper install on the main HD tomorrow. I'll let you know when I'm starting.

Cheers!

---

### Post by pauljwells on 2010-05-04
Had another go last night using the alternate install CD. everything worked perfectly, grub even found a backup on an external USB drive. Back on the horse! :)

---

