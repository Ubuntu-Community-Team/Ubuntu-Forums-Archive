---
title: "Problems moving Ubuntu 11.10 from laptop to dual-boot with Fedora 16"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by PatrickD-52761 on 2012-02-03
Hi everyone,

I have Ubuntu 11.10 set up on my laptop (Toshiba Satellite A105-S2194) and wanted to move it over to my desktop (homebuilt with an AMD Athalon 1800 XP+ processor). I used Clonezilla to copy the disc over to a hard drive that's the exact same size as the one in my laptop. Then I installed it in the desktop, and ran the grub2 updater in fedora.  Everything seems fine (in that it "found" and created entries for Ubuntu 11.10), but when I try to boot up Ubuntu, I get "Error: File not found. Error: You must load a kernel first." I can boot fedora without problems.

I tried both with copying the bootloader and everything over from the laptop to the hard drive, and stripping out all of the bootloader information (which only removed the grub2 directory, but left the grub directory in the /boot directory).

I'm at a loss as to what to do here. Should I reinstall Ubuntu? Can I repair it (reinstall without losing my data/programs/settings), and if so, how?  Can I do a backup from the laptop and then do a restore on the desktop (pointing to the second hard drive)?

Right now, Fedora is on sda and Ubuntu is on sdb. In the laptop, Ubuntu is on sda, and there's no sdb.  Also on the laptop, the hard drive is a SATA drive, and in the desktop, the hard drive is a PATA drive (not sure if that has an effect or not).

Thanks, and have a great day:)
Patrick.

---

### Post by PatrickD-52761 on 2012-02-04
An update. I tried to use the Ubuntu Live CD to Upgrade Ubuntu 11.10 to Ubuntu 11.10. It seemed to work (except that some of my current programs couldn't be reloaded, so I probably lost something).  When I tried booting, I was taken to a grub_rescue> prompt.

I rebooted the Live CD, and used Boot Repair to try and fix the GRUB installation.  Here's the pastebin from what it shows [http://paste.ubuntu.com/828388/](http://paste.ubuntu.com/828388/)

One thing I noticed is that GRUB is installed on both drives, although it shouldn't be.  Boot Repair failed to fix the problems, so I booted up a SuperGRUB2 disk, and used that to boot into Fedora.  In Fedora, I ran grub2-install --recheck /dev/sda, which repaired GRUB.

Now, I'm back to where I started (Fedora boots up, Ubuntu gives me the "Error: file not found" and "Error: You must load a kernel first" messages.

So, my questions are the same as before, but with some additional (or changed) ones.

1.  Should I reinstall Ubuntu or try the Upgrade option again?
2.  How do I remove GRUB/GRUB2 from /dev/sdb (the Ubuntu drive)?
3. I thought about trying the idea from [http://ubuntuforums.org/showpost.php?p=11631914&postcount=22](http://ubuntuforums.org/showpost.php?p=11631914&postcount=22) and see if that fixes anything. Naturally I would have to choose /dev/sda, instead of his device.  Would this work?

One other option that I'm thinking about doing is this:  Currently I have the Fedora drive as Master, and the Ubuntu Drive as slave. I'm thinking about pulling the Fedora drive out, and changing the Ubuntu drive to Master. Then, I'll run the live CD (with just one drive in) and use update-grub (or grub-install) to get it working.  After that, I'll put the Fedora drive back in (as slave) and re-run update-grub to get it included.

Would that work?

Also, would removing GRUB complety, and then reinstalling it work (as in would it remove GRUB from both drives, or just the /dev/sda drive)?

Thanks for any answers and help.

An update. I tried the advanced options of BootRepair, and it still didn't work. I'm going to try pulling the fedora drive out, and verify that the Ubuntu one boots at all.  Here's the updated pastebin of my Boot(Grub) [http://paste.ubuntu.com/828555](http://paste.ubuntu.com/828555)

Have a great weekend:)
Patrick.

P.S. for clarification, what I want to do ultimately is use the laptop for testing Ubuntu 12.04, and have my stable (11.10/Fedora 16) on my desktop. Or, I may have to do a dual-boot Ubuntu/Windows on the laptop, as I tutor at a local college that uses Microsoft products for their classes.

---

