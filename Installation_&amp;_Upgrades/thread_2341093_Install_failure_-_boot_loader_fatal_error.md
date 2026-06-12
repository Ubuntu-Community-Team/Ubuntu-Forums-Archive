---
title: "Install failure - boot loader fatal error"
date: 2016-10-24
forum: Installation &amp; Upgrades
---

### Post by levinin on 2016-10-24
Hi,

Any help appreciated!

Trying to install Ubuntu on what was a windows 10 machine from a USB stick.
It gets so far then fails to install grub - fatal error.
It offers 3 options but won't let me actually choose any of them. As in the options are viewable and selectable but when I click "OK" it does nothing.

Got the link: [http://paste2.org/PH7gOYaO](http://paste2.org/PH7gOYaO)

Tried doing something simple I saw on another post:
Choose the "Try Ubuntu" option
$ sudo grub-install /dev/sda

But I get this:
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.

And:
$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

Any help appreciated. Right now I seem to have bricked my PC!


Small update - realised I didn't have /dev/sda mounted so tried to do that:
sudo mount /dev/sda /mnt/sda
mount: unknown filesystem type 'isw_raid_member'

Clearly I am missing something about having a raid hd setup.

---

### Post by ubfan1 on 2016-10-24
Something seems badly wrong with your partitioning.  The disk total is 488M sectors, but the first partition ends at 960M+.  Do you really want a 32bit system?  If you repartition, you should consider a smaller root, like 50G, 8G swap (guessing from your extended partition size, which has no logical partitions added to it), and the rest a data partition you can mount from your home, so you may keep it for  reinstalls of the OS .

---

### Post by levinin on 2016-10-24
Interesting. I just went with the defaults, no real thought in it. Definitely don't want a 32 bit system :). 
What you say about a 50G root for future installs makes a lot of sense, I'll give it a go.

---

### Post by oldfred on 2016-10-24
Is or was drive(s) ever RAID, or Intel SRT which is seen as RAID.
Make sure UEFI/BIOS is set for AHCI, not IDE nor RAID.

And if drive was RAID, then you may need to remove meta-data. But if you want RAID better to use server install version & then choose to install your desktop of choice.

This was from someone with Intel SRT, but same commands for removing any RAID meta-data from drive.
       > Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by levinin on 2016-10-24
Yes my disc is set up as raid striped. It manages the partitions ok during setup (I think so anyway having just been playing with it again following ubfan's post). 

But you're saying although it doesn't manage the boot loader in desktop it would manage it in server mode? Any idea why that is?

---

### Post by oldfred on 2016-10-25
Back with 12.04 there was the Alternative installer for RAID & LVM. They did away with it and said they would add those features to the gui installer.
And with both 12.10 & 13.04 they said to either install 12.04 and update, or use server installer.
And is was only a couple of versions ago that Desktop gui added LVM installs.
And some RAID version seem to then be seen, but grub never seemed to correctly install.

If you have gotten Ubuntu to correctly install, you can manually reinstall or add grub. 
Boot-Repair may work but where grub is installed depends on type of RAID. 
I do not know RAID, but I believe hardware RAID & Linux software RAID install grub to MBR if BIOS.
But if "FakeRAID" or BIOS based RAID then you install grub to root of /mapper/... as if it is MBR.
If UEFI you still have a separate ESP - efi system partition with all installs (I think).

---

### Post by levinin on 2016-10-26
Oldfred you are a star. You called it. Turns out you do know a little raid.

At first I could not complete install because it errors on grub and would not let me complete installation. 

Then I ran commands in above post to try and manually install grub. This failed because I was trying to install to sda which is the wrong location on a raid system.

But it did then pass grub during install and therefore I now had a complete install with no bootloader.

So back to live USB boot. Install grub to both mapper drives (raid0 striped setup) and it works!

---

### Post by oldfred on 2016-10-26
Glad you got it working.

With RAID 0 you must have good backups.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

