---
title: "Dual boot - want to upgrade to Win 10 without destroying everything"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by subcook on 2016-02-19
Ubuntu14.04 LTS
Toshiba Laptop L855-S5383
500GB HDD

First partition is Win7, Second Partition is Ubuntu.  If/When I upgrade Win7 to 10, I'll have to re-install grub (correct me if I'm wrong) so that I get a bootsplash to boot into linux.  (Been a long while but I remember it being easy to re-install grub - reminders)?

Ideally I would like to go back and re-install Win7 as I like it better, but when 6/2019 comes around and architecture and security support for Win7 goes bunk and I have no choice, would still like to get Win10 for free as it would recognize the devise.

I'm not greedy though, if it's really easier to accept defeat (again) from Window$, than I'll just stick w/ Win10.


Thanks in advance,

Cheers !

P.S.  I did look for a thread/guide on the matter before posting this.  My search was fruitless

---

### Post by oldfred on 2016-02-19
If you have BIOS/MBR, Windows has a major bug for years, where it updates partition table but forgets to write the Linux logical partition.
So you both need to restore Linux partition to partition table (partition is normally still there) and reinstall grub to MBR.
You also need to turn off fast start up in Windows 10 which is always on hibernation.

       Fast Startup off
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html
      [/URL]
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Post this just to document partition table.
sudo parted /dev/sda unit s print

Best to backup partition table, but only restore if you do not change partition table structure.
      First backup partition table, use your drive for sda, sdb etc.
sudo sfdisk -d /dev/sda >parts_ sda.txt
Restore:
sudo sfdisk -d /dev/sda > parts_sda.txt

    Many updating to Windows 10 have had to use testdisk or parted rescue
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)

Use parted rescue to restore missing partition details in post #22
[URL="http://ubuntuforums.org/showthread.php?t=1775331"]http://ubuntuforums.org/showthread.php?t=1775331
[/URL]Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---

### Post by subcook on 2016-02-19
So from the sounds of it, I'd be better off wiping the linux partition (after backing up - I think I use deja dup, but whichever has the black file cabinet icon), installing win 10, reverting back to win7, than installing the ubuntu as if it were all new, than restoring the backup.

If it weren't for those damn video games, I would write winblows off altogether at this point

---

### Post by Mark Phelps on 2016-02-20
Personally, I would advise against upgrading the PC to Win10.  That continues to have lots of problems (NONE of which MS is telling folks about because they're too busy bragging about the supposed 200 million folks who have upgraded!).

But, if you are determined to do it, then BEFORE you do that, at least make an image backup of Win7 -- so you have something to go back to when one or more of your components does not work due to the lack of Win10 drivers. And, do NOT rely on the Win10 GoBack function to revert to Win7, it is unreliable and can leave your machine in a corrupted state.

Macrium Reflect (MR) provides a FREE version that can be used to image and restore partitions or entire drives.

What I recommend is the following:
1) Download and install Macrium Reflect (MR)
2) Run MR and choose the option: "Create an image of the partition(s) required to backup and restore Windows" to write a full backup to an external drive or USB stick
3) Use the option to create a boot USB stick or CD

I use this all the time and it typically takes less than 10 minutes to do the image backup and about the same time or less to do a restore.  Plus, MR has the option to Add a Recovery Boot Menu entry.  This allows you then to boot into WinRE, and you can then use that to do a restore -- when you can't boot into Windows!

NOW, you have the means to restore a full working system from the external drive or USB stick in only a few minutes.

Good Luck

---

