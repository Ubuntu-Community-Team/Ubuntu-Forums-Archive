---
title: "I/O error on device sdd"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by Eladon on 2007-03-14
Ok, a week ago I reloaded my computer from scratch with Edgy.  Everything was working fine, I had it just the way I wanted it.  Then today I boot up my computer, and it hangs "Checking root file system..." at which time it looks like it's trying to kick fsck 1.39 into gear but it just hangs there forever.  So I Ctrl-Alt-Del to see if I can get a command prompt, and after messages about how it couldn't start X, etc., I get a command prompt.  

So I check around, and it looks like the root file system is there, all the files seem to be there... But then I noticed that every once in a while a message appears saying
"I/O error on device sdd"...

I have one IDE drive on the system that has one Windows partition and one ext2 partition with grub running in /boot on it.  Then I have 3 SCSI hard drives that I have set up with software Raid 0, and LVM on top of that, that mounts the whole file system.

Now I'm not all that familiar with what devices are called what yet, I've only had this system up and running for a week... So I don't really know what "sdd" is in the context of things.  But it seems awefully strange to me that I could get a command prompt, view files on the drive, and yet there is some problem...

I even went into the Bios of the Adaptec SCSI card and used it to verify the integrity of the 3 SCSI hard drives, they passed with flying colors.  So how do I explain this?  All of my drives seem good, I haven't had any system crashes or unreliability up to this point, so I'm not even sure how to go about trouble shooting this?

Thanks for any help you can give!

---

### Post by Eladon on 2007-03-14
Oh my goodness, it was because I had a USB Drive plugged into my computer.   :-k  Don't know why that would be the case, but I sure am relieved I don't have to start from scratch again...

Note to self:  Don't leave USB drives plugged into computer during boot.
:biggrin:

---

