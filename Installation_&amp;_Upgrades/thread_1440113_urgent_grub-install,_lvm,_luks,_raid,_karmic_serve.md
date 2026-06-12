---
title: "urgent grub-install, lvm, luks, raid, karmic server"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by craig0927 on 2010-03-27
Please help...I'm really desperate.  If I can't get this fixed by tomorrow, my only option will be a complete reinstall as I have to have everything operational for a new job I'm staring on Monday.

I'm running Karmic Server with GRUB2 on a Dell XPS 420.  Everything was running fine until I changed 2 BIOS settings in an attempt to make my Virtual Box guests run faster.

I turned on SpeedStep and Virtualization, rebooted, and I was slapped in the face with a grub error 15.  I can't, in my wildest dreams, imagine how these two settings could cause a problem for GRUB, but they have.

To make matters worse, I've set my server up to use Luks encrypted LVMs on soft-RAID.

From what I can gather, it seems my only hope is to reinstall GRUB.  So, I've tried to follow the Live CD instructions outlined in the following article (adding the necessary steps to mount my RAID volumes and LVMs).  

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

If I try mounting the root lvm as 'dev/vg-root' on /mnt and the boot partition as 'dev/md0' on /mnt/boot, when I try to run the command $sudo grub-install --root-directory=/mnt/ /dev/md0, I get an errors:

grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: error: Embedding is not possible, but this is required when the root device is on a RAID array or LVM volume.

Somewhere in my troubleshooting, I also tried mounting the root lvm as 'dev/mapper/vg-root'.  This results in the grub-install error:

$sudo grub-install --root-directory=/mnt/ /dev/md0
Invalid device 'dev/md0'

Obviously, neither case fixes the problem. 

I've been searching and troubleshooting for several hours this evening, and I must have my system operational by Monday morning. That means if I don't have a solution by pretty early tomorrow morning...I'm screwed. A full rebuild will by my only option. Please...if anyone has any ideas, please help.  I really, really don't want to have to rebuild my entire server just because of a GRUB problem.

---

### Post by stlsaint on 2010-03-27
I doubt that grub is the problem considering that it was fine until you changed those two bios settings. 
Question 1: Have you changed those two bios settings back to what they were originally.

Also you may be able to retrieve that data as long as you know the passphrase to the lvm with a livecd. 
Change those two settings back and try re-installing grub again.

---

### Post by Herman on 2010-03-27
Firstly, remember that there is paid technical support available for Ubuntu, look for the link in the following URL, [http://www.ubuntulinux.org/support](http://www.ubuntulinux.org/support).

Not so many of us regular desktop users around here would have much experience with an advanced professional type of an installation like yours with LUKS encrypted  LVM and RAID.

In the meantime one thing that strikes me as odd right away is that you say you're booting Karmic with GRUB2 but you're saying you are seeing a [GRUB Error 15]("http://members.iinet.net.au/%7Eherman546/p15.html#15"), which I thought was an error from Legacy GRUB. Maybe I'm wrong?
What files do you have in your /boot partition?

What does the boot stanza in your grub.cfg or menu.lst file look like?

Presuming you are using GRUB2, have you tried booting from a GRUB2 Live CD and performing a direct boot from GRUB2's Command Line Interface? [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  Rescue your System?

Have you checked to make sure your hard disk order hasn't been accidentally changed somehow in your BIOS? 

Just a few ideas, I hope I'm being helpful, I have an encrypted LUKS LVM installation, but no experience with RAID.

EDIT: I am inclined to agree with stlsaint, (above), and I would first be trying to reverse any changes in the BIOS settings if that's where the problems came from.
Also, I think if you install lvm2 and cryptsetup in the Live CD and do 'sudo modprobe dm-crypt' you should be able to mount your LUKS encrypted root file system and chroot if you need to, I presume that's what you were going to do anyway.

---

### Post by craig0927 on 2010-03-27
Well...I finally figured it out.  After about 7 hours of reading through articles in the forums, searching google, and trying slight variations in my attempts to reinstall GRUB, I removed a USB thumb drive.  One that used to be a liveUSB...with GRUB 1...

Yes...I am an idiot. :-)

I had wondered the same thing Herman wondered about the error 15 when researching the problem...but I could have swore my machine was set to boot from the hard disk first...and it never even occurred to me that it might be booting to my USB drive...that I had recently formatted....apparently gparted doesn't erase the MBR when you delete the partition and format...

The BIOS settings had nothing to do with the problem after all...and I'm using them now without any problems...although I can't say I notice any performance gain.  

I guess it's good that I figured it now instead of next week when I start work...I would have surely panicked and tried to reinstall.  

Everyone repeat after me...GRUB Error 15 = check for bootable USB, then proceed with the stuff mentioned in these forums and google. :-)

---

### Post by Herman on 2010-03-27
:D LOL - well we're all human! I'm glad you were easily able to solve your problem and thanks for letting us know. 

Regards, Herman :)

---

