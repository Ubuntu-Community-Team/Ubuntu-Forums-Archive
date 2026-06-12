---
title: "Cannot get rid of Windows Boot Mgr"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by HugeLoad on 2010-10-31
I think I have the opposite problem of many :) I need to blow Windows 7 away completely.No dual boot...just 10.10 only. 

I started with the live CD...so I don't know if this is a "wubi" thing or not. I'm trying to install onto an Intel X25 80GB SSD which formerly contained Windows 7. "Use entire disk" option chosen. The install went like a dream, a sheer joy to watch. Until I went to restart and there was Windows Boot Manager telling me there was a problem with my Windows installation. Correct, it's gone!

I started the live CD again, fired up gparted and deleted everything on on /dev/sda - the lot. Reinstalled 10.10 - rebooted - Windows Boot Manager still there. OK, yet another try. Back into live CD and this time fdisk, followed by shred, followed by verify that there's no partition table in gparted. Empty volume, no partition table.

Reinstalled 10.10 again & restarted. Yes, you guessed it. Windows Boot Manager is STILL there!

What on earth must I do to rid myself of this hated Windows Boot Manager? I feel like a complet twit, because I've installed Ubuntu over XP (etc) many times (on rotating rust, not an SSD admittedly but...a "disk" is a disk...is a disk)

Help and advice badly needed & much appreciated!

Regards & TIA!
-HH

---

### Post by 73ckn797 on 2010-10-31
When booted into the Live CD, open Applications/Accessories/Terminal and enter:
```
sudo grub-update
```That may fix the problem.
If not, go here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
It may seem to be a lot but look through it to solve the problem.

---

### Post by HugeLoad on 2010-10-31
> **73ckn797 said:**
> When booted into the Live CD, open Applications/Accessories/Terminal and enter:
```
sudo grub-update
```That may fix the problem.
If not, go here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
It may seem to be a lot but look through it to solve the problem.

I am SO gonna try that. Thank you very much for the suggestion and resource link. Back with results anon...

---

### Post by MSPdwalt on 2010-10-31
Way to dive into Ubuntu! it's awesome to see someone switching entirely.   There may be a few headaches initially, but once you get it running and customized to your liking it's pretty set and forget.  You won't want to go back ;)

---

### Post by oldfred on 2010-10-31
The sudo update-grub just scans system for operating systems and updates the menu.

You need to get grub2 in the MBR. Is the SSD not seen as sda. Or is your boot drive not the SSD. The default install usually installs grub2 to the MBR of sda. Only manual partitioning now gives you the choice of which drive to install to.

To get into Ubuntu quickly you may just be able to choose another drive in the BIOS, but to know what is where run the boot info script.

To see your entire configuration run this from the liveCD.
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Generally all you should have to do is reinstall grub2 to the MBR of the boot drive. If you can boot from another drive's MBR it is relatively easy from there to install grub to another drive's MBR. Or from liveCD you can install grub.

---

### Post by HugeLoad on 2010-11-10
> **oldfred said:**
> 

Generally all you should have to do is reinstall grub2 to the MBR of the boot drive. If you can boot from another drive's MBR it is relatively easy from there to install grub to another drive's MBR. Or from liveCD you can install grub.

Sorry to be late back with this one. For posterity, because for sure sometime, someone, somewhere, will be seeking this information. To whoever you are, I hope this helps.

The problem was solved when I discovered that the second SSD - which was formerly part of an awesome but unnecessary RAID0 - and had been retasked as a data drive, ALSO had a Windows MBR. 

Using the live CD I yanked the data off to an external HD, checksummed both to ensure all was backed up correctly, then blasted everything off the second SSD by deleting the partition and formatting.

Then I reinstalled Ubuntu on SSD 1, specifying SSD2 as a /home partition.

The ubunti awesomness continues :) 

Thanks to those in this thread who contributed wisdom and perspective to a very frustrated user.

---

