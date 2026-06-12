---
title: "Vista Won't Boot After Ubuntu (6.06) Install"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Blyn on 2007-06-06
Okay... well i finally got around to giving ubuntu a shot yesterday and ran into a few problems.

The plan was to dual boot both OSes on the same HDD... so currently there is a vista partition and the ubntu root and swap partitions are both in an extended partition (is this bad... i wasn't sure what it was).  Vista got installed fine - it was all stable before the Ubuntu install - had it running for about a day or two (just installed basic programs etc).  

The thing was that when i went to install ubuntu, i sort of forgot to defrag the windows partition.  Then somehow ended up resizing the windows partition, resulting in cutting out about 500mb.  Install went fine, Ubuntu booted up fine... but soon after i did a reboot, tried vista (it was recognized by boot loader as apparently it shoot be), but vista will not boot.  Instead it hangs at the loading screen (big black screen with annoying progress bar).  Left it for about an hour - nothing.  

Now, i don't have Grub installed, but my impression so far is that windows should still be able to boot fine without it installed.  Could i have messed up the windows partition by resizing it without defraging?  Or is this as simple as installing grub, or possibly repairing the windows boot.  I realize this isn't a windows forum... but it seemed more appropriate than the alternative.  I can post specs if they are needed... didn't think they would be.  Thanks for any help!

---

### Post by tgalati4 on 2007-06-06
How did grub not get installed?  It's the only way that I know of to use dual-boot.

Boot the Ubuntu Live CD and install grub.  There are plenty of tutorials on the forums.  Search "install grub"

How big is the Ubuntu partition?  It needs to be ~4GB.  I'm not sure how the Windows partition would shrink unless you took steps to shrink it yourself.

The Windows data should be safe, but there is always that risk when resizing partitions.

---

### Post by confused57 on 2007-06-06
> **Blyn said:**
> Okay... well i finally got around to giving ubuntu a shot yesterday and ran into a few problems.

The plan was to dual boot both OSes on the same HDD... so currently there is a vista partition and the ubntu root and swap partitions are both in an extended partition (is this bad... i wasn't sure what it was).  Vista got installed fine - it was all stable before the Ubuntu install - had it running for about a day or two (just installed basic programs etc).  

The thing was that when i went to install ubuntu, i sort of forgot to defrag the windows partition.  Then somehow ended up resizing the windows partition, resulting in cutting out about 500mb.  Install went fine, Ubuntu booted up fine... but soon after i did a reboot, tried vista (it was recognized by boot loader as apparently it shoot be), but vista will not boot.  Instead it hangs at the loading screen (big black screen with annoying progress bar).  Left it for about an hour - nothing.  

Now, i don't have Grub installed, but my impression so far is that windows should still be able to boot fine without it installed.  Could i have messed up the windows partition by resizing it without defraging?  Or is this as simple as installing grub, or possibly repairing the windows boot.  I realize this isn't a windows forum... but it seemed more appropriate than the alternative.  I can post specs if they are needed... didn't think they would be.  Thanks for any help!

If you resized your Vista partition with the Ubuntu live cd, you might be able to boot up your Vista install disk and repair your Vista filesystem.  Once you're able to boot into Vista, then you can reinstall grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Gparted on the live cd isn't recommended for resizing Vista's NTFS filesystem...resizing XP NTFS usually isn't a problem.

---

### Post by Elrohir on 2007-06-06
I believe I know what he did... From the start, it all goes wrong... sorry dude, but here is how it's done:

First: boot the Live CD, go to System > Preferences > Removables Drives and Media and deselect Mount Removable drives when hot-plugged and Mount removable media when inserted..
Second: Partition properly the HD with gparted ```
gksudo gparted
```, for instance my HD is 120GB, 50GB for Vista the rest for Ubuntu, say 6GB for root 70GB for /home and the rest is an extended partition where you'll place the swap partition (1GB should do fine). Give the partitions their proper filesystem (Vista, NTFS; Ubuntu ext3); what to do with the rest of unallocated space? assign a FAT32 filesystem and you may use it for sharing files between OSes...

Third: Restart the machine and pop in the Vista DVD. Install Vista on the NTFS partition, then Ubuntu and assign the mounting points according the previous partition settings.

Fourth: Enjoy!

Now, coming back to your case, I believe the resizing of the Vista partition might have messed up some system files (wouldn't surprise me, really), so you may have to reinstall, so on Ubuntu back up your data from Vista, then reinstall Vista and reinstall grub.

Reinstalling GRUB:
boot live CD
on terminal: ```
sudo grub
find /boot/grub/stage1
```this should give you an output such as (hdX,Y), being X and Y numbers, then
```
root (hdX,Y)
setup (hdX)
```and you should be set!

---

### Post by Neobuntu on 2007-06-06
Before anything, always have a backup. Then...

First of all, the fact that the gparted CD works with XP and not with Vista should tell you something about Microsoft.

Second, we dropped the ball with the Feisty CD partitioner. Here, the lead dog in the migration fight can't install a dual boot (but their is a way). Unacceptable.

Third, why can't a message pop up and say partition resizing (use gparted CD instead of Feisty CD) has worked generally well up through XP (even with NTFS; without resizing) but you had better read up on the latest with Vista. See how others have worked around the road blocks.

Lastly, Vista offers little that todays open software can not do and do better. Open software has MUCH more that Windows can not even do (and more important things). Plus, open software is improving faster. What you need to do is seek out (using the automated package manager; not from a web site download) a native open software replacement for your old, costly, tiered Windows apps. Kmymoney in place of Quicken for example. This even though last years Quicken can be run (easily) via WINE in Kubuntu. Native is always better. That's why you dual boot (Or use two computers; the faster one for Kubuntu). So then you may run Win apps natively and GNU/Linux based apps natively; in their native habitat. If anything needs to be simplified, it is computers.

I understand and recommend dual booting for the newbie (Just don't buy Windows). The thing is, it's more initial and ongoing work (by far). Windows is a beast to "properly" maintain and still, it is no where near secured.  If you can get what you need from say-- Kubuntu, then that's your ultimate maintainable goal. Kubuntu only. Keeping in mind that updating within a release is EXCELLENT but when a new release emerges (the CD) you either need to wait (about Six months) to use the Upgrade Manager or back up your home directory and do a new; clean install. Even then, the further you go away from the release date, the more the excellent automatic on-line upgrades (and not just security upgrades) will improve your system.

Oh yeah, it's all free (and legal) to you as well.

---

