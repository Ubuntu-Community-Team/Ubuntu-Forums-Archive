---
title: "Help install 7.10 to external USB HDD"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by vonchiz on 2007-12-11
I am an experienced computer user and have recently made the jump to Ubuntu, I still have my main windows install for some of the programs I need (once I get Ubuntu running I want to do some testing with wine).  I was running a dual-boot from my main hard drive, but for some reason 7.10 32-bit version would pooch my MBR anytime I installed Grub.  x64 version worked like a dream.  There were some packages I needed from the x32 version for my testing to transition from windows to Ubuntu, so I resorted to a 3rd party bootloader, which worked, but I still had problems.  I took Ubuntu off my internal drive because of the problems and I needed the space, so now I am trying to do my testing from an external USB drive.  This hasn't worked because the USB drivers aren't loading up early enough in the boot sequence.  I have a couple of questions that would solve my issues.

I have been looking for answers on the forum and general internet, and I think I have all the answers I need, but I am unable to implement them.  When I install from the live DVD, it won't give me permissions to change any of the files on the HDD install from the live DVD boot.  I can't figure out how to boot in rescue mode from the live DVD with 7.10.  Old versions it was obvious, but the only thing close on my live DVD is a graphics-safe UI - it still won't let me change any config files on my HDD install.  I have made the changes in VIM with a sudo command and for some reason, it refuses to save any changes I've made ('colon x' does nothing).  I have tried just typing in rescue to the boot options - nothing lets me change anything on my HDD install.  Any suggestions?  Here is the main reference I've been using, from an older version of Ubuntu:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

Some people have suggested just doing a clone of the DVD install on the hard drive.  This sounds great, but I have more ??'s.  First of all, how to I set up a swap partition after I do this?  Is there a way of copying it to an EXT3 partition from windows, or do I have to copy the files to a FAT32 partition?  Can I boot from that into Linux then copy to an EXT3 partition or is it stuck there forever.  I would prefer an EXT3 partition for Linux, but I do have a secondary FAT32 partition on the drive in question to transfer some working files between Linux/Windows.  
Here's the main reference I plan on using if I go with this:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thanx in advance for any help.

Chad

---

