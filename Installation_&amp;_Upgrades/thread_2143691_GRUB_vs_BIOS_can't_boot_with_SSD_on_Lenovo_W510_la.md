---
title: "GRUB vs BIOS: can't boot with SSD on Lenovo W510 laptop"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by icycle on 2013-05-09
Hi all,     

First I'll give some background in this paragraph, then describe  the current problem in the next paragraph.  I recently started using Ubuntu 12.10 with a Crucial 256GB SSD disk (model M4-CT256M4SSD2) in my Lenovo  W510 laptop.  Things were good for a while and then one day  the system completely hung.  I'd awoken it from suspend in a meeting and  used it a bit then it wedged up: no mouse pointer, cursor, response to  keys, etc.  I hard powered it down and from that point it would not  boot.  The BIOS showed an error "2100: HDD0 (Hard disk drive)  initialization error (3)".  I tried several soft and hard reboots to no  avail.  Later I tried one more time and it did successfully boot.  I  decided to check disk FW levels.  I was running 040H FW and noticed the  latest FW (070H) fixed an issue whereby the disk might not be detected  by the host on power up.  Great!  So I booted into my old Windows 7 HDD  and upgraded the FW in the SSD.  Things were good for a bit and then I  started having trouble booting again.  Hmm, perhaps the BIOS is having  issues, so I upgraded the BIOS to the latest (1.45) version.  Not much  difference.     

That brings us to today: I had the BIOS SATA mode set to AHCI and  was basically seeing constant SSD activity after the BIOS splash screen  followed after a long while (~1 min) by "Read Error" which is output by  the first stage of the GRUB bootloader.  This repeated through soft and  hard reboots, never able to boot.  I booted into the Ubuntu 12.10 live DVD and  verified that the disk was healthy (smartctl health report clean, SMART  short and offline self tests pass, able to read all of the MBR and boot  partition, grub CLI could see the files, etc).  I installed and ran  Ubuntu's Boot-Repair program ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)).  All of this still presented the same problem on boot.     

            I then tried switching the BIOS SATA mode to "Compatibility" so  it'd emulate the old school PATA style disk emulation.  The next boot  attempt successfully reached GRUB menu!  However, any attempts to boot  OS menu entries failed (running memtest86 did work, however).  The  symptom there was constant SSD activity with no change to the console.   Oddly, a subsequent boot (still in BIOS SATA compat mode) would not  reach the GRUB menu.  Re-entering BIOS menu and re-saving the compat  mode seemed to help get back to GRUB menu, but it seems flaky.     

            So I have a full report from the Boot-Repair program ([http://paste.ubuntu.com/5646096/](http://paste.ubuntu.com/5646096/) -- tried to include below but despite wrapping in CODE tags still ends up malformatted)  and am seeking help from the greater Ubuntu community for help.  What I think is that GRUB is relying on the  BIOS disk access facilities and that is having trouble with this disk.   I have tried the Boot-Repair option to have GRUB use "ATA disk support"  option, no difference.  I'm thinking of some way to force GRUB to use  it's own disk access instead of BIOS, but I've not figured this out yet.     

Any tips?     

            Thanks,     
            Brett

---

### Post by oldfred on 2013-05-09
All operating systems read the system info reported by BIOS (or UEFI) to boot with. 

You need AHCI on to enable trim, but it does not look like you are using trim. 
Are you then using a cron task to run fstrim.

Some suggest fstrim is better. I use trim in fstab, but did not enable it right away.
 fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
sudo hdparm -I /dev/sdX
Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
test if trim working using hdparm
[http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2](http://techgage.com/article/enabling_and_testing_ssd_trim_support_under_linux/2)

      
 With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler
But per this noop may not now be best.
[http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)
noop may not be best scheduler for SSD, deadline may be better
[http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance](http://www.velobit.com/storage-performance-blog/bid/126135/Effects-Of-Linux-IO-Scheduler-On-SSD-Performance)

   fred@fred-Precise:~$ cat /sys/block/sda/queue/scheduler
noop deadline [cfq] 

   [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by icycle on 2013-05-09
Fred, thanks for the info, but the problem here is that the system won't boot, so the trim cmd and the scheduler are irrelevant, right?

---

### Post by oldfred on 2013-05-10
I do not see anything wrong. Not sure why Boot-Repair wanted to run fsck. May be better to ru e2fsck from liveCD.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

And why is grub2 in MBR using an embedded config file? It does that is there is not enough room for grub2's core.img (formats other than ext4 like btrfs?) or booting from one drive to another. Do you have something unusual that I am not seeing in BootInfo report?

---

### Post by icycle on 2013-05-10
Thanks for the tips Fred, I should have mentioned that as part of the SSD health assessment I did fsck all the filesystems successfully, manually, from the Live CD.

Folks,    


             Looks like I resolved this by re-flashing BIOS.  I chose a version  one less than the one I was running (which was the latest), but it could also be that this  flash was from a Lenovo BIOS update bootable DVD whereas the previous flash (that led to the problems) was  using a Windows 7 program from Lenovo, which did the whole flash from  within Windows.  I saw nothing of interest in the latest BIOS that would  entice me to retry a bootable DVD flash of the latest, so I'll live  happily on version 1.44.    

            
So, things are stable using the SSD and Ubuntu now boots right up.    

      
      Thanks for the looks,
       Brett

---

