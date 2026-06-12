---
title: "boot stops at initramfs prompt after update"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by mobilediesel on 2008-05-27
I installed Ubuntu using WUBI so I can dual-boot Windows XP Pro and Ubuntu. It has been working fine with Ubuntu getting more use every day while my wife and I get used to Ubuntu. Today it reported that updates were available so I installed them since I've had no trouble with updates. Now when I try to boot into Ubuntu it stops at a prompt that says initramfs. I'm very new to Linux of any version. I have no idea what to even think about trying next. I can boot into Windows just fine still. My other computer has Ubuntu on it and hasn't had trouble with updating or anything but now I wont be putting any updates on when they come available until I find out why this happened.

what the hell do I type when "initramfs" shows up? :mad:

---

### Post by overdrank on 2008-05-27
> **mobilediesel said:**
> I installed Ubuntu using WUBI so I can dual-boot Windows XP Pro and Ubuntu. It has been working fine with Ubuntu getting more use every day while my wife and I get used to Ubuntu. Today it reported that updates were available so I installed them since I've had no trouble with updates. Now when I try to boot into Ubuntu it stops at a prompt that says initramfs. I'm very new to Linux of any version. I have no idea what to even think about trying next. I can boot into Windows just fine still. My other computer has Ubuntu on it and hasn't had trouble with updating or anything but now I wont be putting any updates on when they come available until I find out why this happened.

what the hell do I type when "initramfs" shows up? :mad:

HI and you may look here
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by mobilediesel on 2008-05-27
> **overdrank said:**
> HI and you may look here
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

I've been through that page before I posted. Nothing on there helps me at all. Is there some command I type at the initramfs prompt? Do I need to reinstall Ubuntu? Should I get a new hard drive and install it on it's own drive?

---

### Post by inportb on 2008-05-27
Hm... what did you update, exactly? A new kernel revision was released yesterday; did you install the new kernel?

---

### Post by Aearenda on 2008-05-27
What to do depends on why this occurred - try booting using the 'recovery' option in the Grub menu (press 'ESC' when prompted to enter the menu at boot time) and see if it tells you more.

Often this means the system can't find the root filesystem during the boot process. This can happen if the UUID of the filesystem has changed (unlikely), if the order of the drives has changed (more likely, but shouldn't matter if UUIDs are used in /boot/grub/menu.lst and in /etc/fstab), if the drives cannot be found using the more advanced methods used later in the boot process (most likely), or for other reasons.

There are many threads on what to do in this situation with Hardy, which has been prone to difficulty particularly in mixed SATA/IDE systems.

Fortunately there is also a variety of workarounds, mostly by using kernel parameters at boot time. These are set permanently in /boot/grub/menu.lst, or temporarily by editing the boot menu at boot time. [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15) has instructions for both. I would try adding all_generic_ide first, and then irqpoll, assuming the recovery mode startup offers no clue as to the real cause in your case. That post is about the Dell Inspiron 530, but it applies generally apart from the BIOS settings part at the end.

Another option is to see if the system will boot off an older kernel in the Grub menu, assuming there is one offered.

---

### Post by Belikov on 2008-05-28
My computer has the same problem. I try recovery option of the new kernel but something like that it couldn't mount "root" disk. Then I reboot, use old kernel and everything is ok. What can I do now to use the new kernel?

---

### Post by Aearenda on 2008-05-28
Belikov: Well, you can try searching the forums for people with the same hardware as you who have the busybox problem. Or you can just try all the suggestions people have come up with in the forums, by just searching for 'hardy busybox'. 

For starters, I would try the all_generic_ide kernel parameter that is referred to in my last post, along with a pointer to instructions on how to test it and set it permanently if it works.

---

### Post by retatkcid on 2008-05-31
OK, so my problem wasn't the boot process stoping at initramfs prompt.  However, my boot process was corrupted after the most recent updates.

System is a NON-WINDOZE mixed SATA (2 drives)-IDE (1 drive), with IDE primary master as the boot drive.

During the update process, I was presented with a rather cryptic dialog box regarding a change to GRUB's menu.lst file.  I tried to determine what the change might be to no avail.  So, I accepted the default response to allow replacing menu.lst with the package developer's version.  Stupidly, I assumed that a backup of my munu.lst would automatically be created and did not make one myself.  Never again.

The updates required a reboot, and booting failed on restart with a GRUB Error 21: "Device not found" or ""Can not find disk".  So, I pulled out my trusty SuperGRUB CD and went straight to Fix GRUB.  It failed, returning the same error.  I tried to use a GRUB shell as root, letting it find its files,  my boot partition, and rewrite the MBR with the same result.  here's where it gets weird.

Booted with Hardy Live CD and launched GRUB shell from a console window.  Using "find", GRUB claimed that its stage1 files were on (hd2,0).  Having three drives, I thought nothing of this at first and accepted its findings.  Boot failure again.

After poking around for a while, I realized that the drive and partition (hd2,0) that GRUB claimed held the stage1 files was probably wrong.  I changed the call in menu.lst to (hd0,0) and booted successfully.

Who's dumber, me or GRUB?  Go figure.

It appears that there may be more issues related to these recent updates though.  I started getting error messages regarding the DCOP server when trying to run KDE apps.  My .kde folder ownership was correct and after renaming (to feign deletion) all of the hidden .DCOP* files and .ICEauthority, new copies were recreated after starting the first KDE application.  All is well for now, it seems.  That also cured a noticible sluggishness, as well.

---

