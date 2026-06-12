---
title: "Error on boot &quot;Read Error after changing motherboard battery"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by thuleni on 2010-12-02
I changed my motherboard battery last night, and now get "Read Error" on booting to Ubuntu, on dual boot system. This is the most frustrating thing in an otherwise great operating system. It is the second time I have encountered this issue (last time was a change of power supply).

I fixed it last time after three days of re-loading Grub2 and playing around Grub 2 updates, etc. Fixed it eventually, but as usual, no idea of what eventuality fixed it. I think I found a web page buried deep in the 'net, which talked about device.map. Do you think I can find it again - not yet - day 2 searching for the answer...

This is what the grub script tells us:

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 215684663 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=================== sda1: Location of files loaded by Grub: ===================


 110.3GB: boot/grub/core.img
 110.3GB: boot/grub/grub.cfg
 110.3GB: boot/grub/stage2
 110.3GB: boot/initrd.img-2.6.32-24-generic
 110.4GB: boot/initrd.img-2.6.32-25-generic
 110.4GB: boot/initrd.img-2.6.32-26-generic
 110.4GB: boot/vmlinuz-2.6.32-24-generic
 110.4GB: boot/vmlinuz-2.6.32-25-generic
 110.4GB: boot/vmlinuz-2.6.32-26-generic
 110.4GB: initrd.img
 110.4GB: initrd.img.old
 110.4GB: vmlinuz
 110.4GB: vmlinuz.old

---

### Post by oldfred on 2010-12-02
Your boot info script is missing a lot. Plus please post inside code tags which are the # on the right side of the edit panel above as you enter your message.

resetting battery would also reset BIOS to defaults. You may have had some settings.

I have saved these from others, see if any may apply:

BIOS settings need USB mouse & keyboard
BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS

---

### Post by pricetech on 2010-12-02
You may have had some custom settings in the BIOS.  If you didn't document them, can you remember them ??

Make sure you set your system clock in the BIOS, at least the date.

Anything else changed, or just replace BIOS battery ???

---

### Post by thuleni on 2010-12-08
Thanks Oldfred - I changed one thing first - the LBA setting, now grub see the MBR and loads (sort of) Ubuntu.  The other setting were a bit more complicated and I will try to explain.

Your boot info script is missing a lot. Plus please post inside code tags which are the # on the right side of the edit panel above as you enter your message. REST OF THE INFO IN THE SCRIPT WAS OK.

resetting battery would also reset BIOS to defaults. You may have had some settings.

I have saved these from others, see if any may apply:

BIOS settings need USB mouse & keyboard - YES - SET
BIOS should be set for IDE compatibility mode - YES - SET
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility - THERE IS ON "COMPATIBILITY" SETTING, JUST "IDE", "RAID", AND AHCI - CHANGED IT TO "IDE"
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive." - THIS WAS NOT AN OPTION ON THE SATA DRIVE, JUST ON THE IDE DRIVE, WHICH I HAVE WINDOWS INSTALLED ON?
BIOS in not updated to latest revision - WILL SAVE THE BIOS SETTINGS ONCE IT ALL WORKS 100% LIKE IT USED TO, THEN ATTEMPT THE BIOS UPGRADE (FINGERS CROSSED AND PRAYING)
BIOS not set to boot CD or USB first - TOOK CDROM OUT OF FIRST BOOT AS IT NOW BOOTS FROM THE SATA DRIVE.
BIOS shows floppy or firewire and you do not have those - AGREED - REMOVED FROM BIOS
changing newer BIOS SATA from 6 Gbs to a 3Gbs - CAN'T FIND THIS...
Other BIOS settings - Security or locked down Boot sector, Bitlocker - NONE SET
Disable Quickboot in BIOS - DID THIS AND IT DIDN'T MAKE ANY DIFFERENCE - JUST TAKES LONGER TO BOOT AS IT TESTS MEMORY EVERYTIME.

---

### Post by thuleni on 2010-12-08
Forgot to mention two things:
1. Thank pricetech, I will write down working settings, and
2. I now get an error saying something like: "Load kernel first..."

I can get around it by editing the grub setting using the "e" option.

---

### Post by oldfred on 2010-12-08
If you have it working but not quite right then you may need to change setting(s) back, but do it one at a time and see what makes a difference.

If you can boot by editing the grub menu what are you editing? If you have to add a parameter, you can permanently add it in /etc/default/grub, but sometimes updating something may then not need parameter.

If you can boot you should try reinstalling grub from your working system to see if that helps with the booting.

sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by thuleni on 2010-12-10
Thanks for all the advice oldfred.  I changed the setting on the 1st Master drive to LBA as well, although this is my Windows disk.  Switched off SMART Monitoring, also reset Quick boot to enabled (like it used to be - couldn't stand waiting for 4 gigs of memory to test).

Now all is working and boots into grub, where I can select either OS.

So after that success, I decided to upgrade the BIOS (now that I was on a roll).  Updated to 5001 beta, and now have lost the digital display - can only see the screen using a VGA monitor/connection, but that is a ASUS BIOS issue that I will take up with ASUS.

Once again thanks for the help and patience.

---

### Post by oldfred on 2010-12-10
Usually when you upgrade BIOS it resets back to defaults. You may want to check settings that worked again.

---

