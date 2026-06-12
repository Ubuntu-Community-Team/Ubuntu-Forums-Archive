---
title: "boot-repair didn't write MBR"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by bproffit on 2014-06-10
I've been using 14.04 LTS successfully.  I removed a multi-card drive from that machine and when I booted again, I was told there was no boot drive!  I have an SSD for Ubuntu, and 5 1-TB drives in a RAID array.  I booted from the 14.04 CD, downloaded and ran boot repair.  (Details are at paste.ubuntu.com/7623003). It detected my 14.04 installation just fine, but when it's time to boot again I'm told there's no bootable media.  I checked the BIOS and it shows all 6 drives as installed, but won't let me select the SSD as a boot drive--which I assume means there's no MBR.  Two unusual things during the repair: I got a message that the drraid might interfere with the mdraid and did I want to install it anyway?  I said no, and the RAID was accessible normally in the live season. The last step was entering a command (sudo chroot "mnt/boot-sav/sda1" apt-get install -y --force-yes grub-PC Linux)that ended with linux.  I used copy/parse, so I know I didn't enter a typo.  I got a error (in terminal) that the package linux couldn't be found.  Leaving that off the end of the command, I tried again and it appeared to work.  I did not get the prompt I was told to expect where it asked where I wanted to install grub.

Any ideas in what I should try??

FYI, in the boot-from-CD live session, I can mount and access the SSD just fine so it's connected and working, and boot-repair identifies it as a 14.04 installation.

---

### Post by oldfred on 2014-06-10
You kept the dmraid packages:

      >  No DMRAID disk.
[dmraid] packages may interfere with MDraid. Do you want to remove them? no
User chose to keep dmraid. It may interfere with mdadm.


 Set sda as corresponding disk of md0  ??? not sure what this mean?

    

You need to fix this, but it is inside your RAID and I do not know RAID.
 Error: The primary GPT table is corrupt, but the backup appears OK, so that will
be used.
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)


Boot-Repair for whatever reason wants you to boot from md0 not sda?
Grub does not use boot flag, so this does not really matter, but sda1 would be more correct.

 parted /dev/sda set 1 boot off


 Reinstall the GRUB of sda1 into the MBR of sdc # and every other drive you have.
That does not work as you have to have a bios_grub partition to install to gpt partitioned drives.

It does say it installed to sda with error 0 or it installed correctly.
Best not to use auto repair if you have more than one drive as Boot-Repair wants to install to every drive. You only want it installed to sda. Using advanced mode you can choose an install and choose which drive to install into.

In BIOS are you booting from sda in AHCI mode, not any other drive in RAID mode as that would be the wrong RAID.

Since I really do not know RAID, not sure if anything is out of place.

---

