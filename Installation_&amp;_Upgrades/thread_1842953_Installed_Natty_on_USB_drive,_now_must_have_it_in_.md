---
title: "Installed Natty on USB drive, now must have it in to start windows"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by wdavro on 2011-09-12
I have a Lenovo T420s laptop with 64bit Windows 7 installed on it (my business issued laptop).  I plugged in a USB drive and installed 64bit Natty on the USB drive.

Now, when I try to boot up the laptop to Win7 without the USB drive, it tells me the device (some long hex number) doesn't exist and I get a grub rescue prompt.

If I plug in the USB drive, I can get the grub menu and then boot Windows 7 (or Natty).

To further complicate things, the Lenovo has three partitions (as reported by Win7 Disk Manager and DiskPart):
Part 0: labeled SYSTEM_DRV; 1.2GB; no drive letter; not active; System
Part 1: labeled WINDOWS_7_OS; 102GB; drive letter C; marked active; Boot
Part 2: labeled Lenovo_Reco; 15GB; drive letter Q: not active

I've run fixmbr on the Windows 7 drive from Repair on the install DVD but it tells me all is well and there's nothing to do (it also says Windows is on the D: drive), and of course it doesn't fix the problem.

My goal, when the USB drive is NOT plugged in, the laptop boots straight into Windows 7.  But when the USB drive IS plugged in: 1st choice:  the grub menu pops up and I can go either way.  2nd choice: use the bios boot menu when I plug the USB drive in to boot straight into Natty.

I have very little experience with grub and am hesitant to play around (although, I do have a couple month old clone of the Win 7 drive, if all else fails, but I would prefer that to be a very, very last resort).

I could use some advise on how to unravel this/accomplish my goal?
Thanks,

---

### Post by oldfred on 2011-09-12
FixMBR should have fixed the boot from your internal drive, if grub2's boot loader was installed to the internal. But you still need grub2's bootloader in the external to boot your external drive.

Try this first as it usually works.
Boot Problems:Computer does not boot without external drive
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

If you can still boot into your install on the external you can install grub to the external from your install.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc



If that does not work post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by wdavro on 2011-09-13
Thanks for the help OldFred.  

I'm on the road this week and I don't want to take any chances with the laptop as it's critical for my travels.  I'll try the sourceforge link when I get home this weekend after I backup.  I read through it and it looks like it will solve the problem.

Again Thanks,

---

### Post by wdavro on 2011-11-19
The instructions at the link were perfect!

Even the note at the bottom on how to prevent it from happening again during install.  I just reinstalled (to change the partition structure) and those instructions worked exactly!!

Thanks so much.

---

### Post by oldfred on 2011-11-19
Glad I could help. :)

---

