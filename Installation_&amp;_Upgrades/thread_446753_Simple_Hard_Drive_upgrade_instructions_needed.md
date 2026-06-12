---
title: "Simple Hard Drive upgrade instructions needed"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by conal on 2007-05-17


Hi!

Simple task but I can't find instructuions. How do I copy the entire contents of one Hard Drive to another? - OS, the lot. I need to know how  to format the new one for Linux, and what commands to use to copy everything.

Here are the details:

I currently use  2 Hard Drives. The Master one with Windoze (for work). The Slave with Linux (for joy).  I just want to replace my 12GB IDE Iinux slave drive with a faster new 160GB IDE drive.

Sounds simple eh? 

I assume I do this:

- Remove the Windows one and plug the new HD  in it's palce. 

- Format the new HD and copy everything over from the Linux one. 

- then put the new one back where the old one was (as slave)

- plug the windows one back in (as Master). 

I have been using BIOS to chose my Hard drive and thus my OS. I don't have Grub, and this system has been working fine so I want to stick with it. 

I would appreciate any  help!

Many thanks

Conal

---

### Post by IgnorantGuru on 2007-05-17
You might look at this Howto on how to backup and restore a partition...
[http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)

That would accomplish it in a somewhat round-about way.

Also, the command to copy files in linux while retaining their permissions is "cp -a".  If you wanted to try that method you could boot the sysrescd mentioned above, then format the target partition (mkfs -t reiserfs /dev/hdax), then mount it and copy.  However, I don't have experience with copying a whole OS this way, so I'm not sure if that would copy everything involved, such as sockets and such.  ???

Also, you'll need to copy the MBR boot code (just the boot code, not the whole MBR).  Those instructions are in that howto as well.

---

### Post by conal on 2007-05-18
Thanks.

I'll have a go at that then!

---

### Post by allwin on 2007-05-18
> **conal said:**
> Thanks.

I'll have a go at that then!

You might want to investigate the GPARTED Live CD.  This is another ISO you download and run off it directly.  It is Linux, but not UBUNTU.  Anyhow, I did the same thing you wanted to do, copy a working UBUNTU disk to a brand new drive, and it worked like a champ.  The benefit is the GPARTED LIVE CD doesn't access your hard drives at all while it is running, unless you are copying or altering partitions.  Google around for it.  I also think I may have had to reinstall GRUB (from the Ubuntu Live CD) to get everything bootable again.  Search around for how to do that.  You may want to increase the size of your partitions when going from the old disk to the new one, and this helps you out with that, expanding SWAP, too.

---

