---
title: "Broken grub ('Boot Repair' doesn't!)"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by timswait on 2016-10-16
The hard drive in my parents computer (Xenial Kubuntu) recently started to break down. Unfortunately they carried on using it until it failed to boot, going into grub rescue mode. I have now fitted a new hard drive and used Clonezilla in rescue mode and copying sector by sector. It did the cloning (took about 10 hours) and when I booted the system to a live disc I could mount the new hard drive and see my parents files in it. However, it still doesn't boot to the new hard drive, going to the grub rescue screen. So I booted back to the live disc and installed and ran the 'Boot-repair' utility (using beginner mode). It ran and said it had completed successfully, but it still doesn't boot (just get the grub rescue screen still). The link to the Boot-Repair file is here: [http://paste2.org/7OBG4s8L](http://paste2.org/7OBG4s8L)
At least I can access my parents documents, so should be able to save those, but I would really like to save the existing Kubuntu installation rather than doing a fresh install. It took ages to get it all set up just the way they like it, I really don't want to go through all that again!
So also to add, when I try to boot from the hard drive, the error I get is:
```
 Error: file '/boot/grub/i386-pc/normal.mod' not found
Entering rescue mode.....
grub rescue> 
```

---

### Post by oldfred on 2016-10-16
Often normal not found is related to wrong version of grub, BIOS or UEFI.

You show your install is the 35 year old BIOS/MBR configuration.
But you booted Boot-Repair in UEFI mode and it said this:

 BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled. 

If Secure Boot is on, system will not boot in CSM/BIOS boot mode, so go into UEFI/BIOS and turn secure boot off. You may have to turn UEFI off, and/or turn on CSM boot mode.
      
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

But if old drive was really corrupted/defective cloning it will not work. You just cloned the problems.

For both old and new drive, I might first try fsck.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

But fsck will not fix defective drive. You can check drive status in Disks and icon in upper right corner use Smart Status. That will tell if drive is good or not. It also can run many test, but I do not know how to read the many details, just good or bad total status.

---

### Post by timswait on 2016-10-16
Cheers, I had run fsck on the old drive and on the new cloned one. But on more inspection of what was actually recovered on the new hard drive it seemed to be missing a whole lot (e.g. the entire home folder and everything in it!), so I decided it wasn't worth the effort to try to save the old system and have wiped the new drive and done a completely fresh install on it. Am now trying to set it back up nicely for my parents so it's like it was! At least they were good at backing up to external drives so they didn't loose anything too important.

---

