---
title: "Installing Ubuntu nukes XP install"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by Grul on 2005-04-13
I installed Ubuntu yesterday. I had left some space over on the hard drive from when I installed XP, like 5 gigs, so I installed Ubuntu there. Everything went kind of smooth. Ubuntu suggested a swap and root partition in the free space, I installed it there, everything worked after some tweaking.

However, when I try to boot XP from the GRUB menu option I see the Windows XP logo startup screen -- and then a bluescreen flashes by, and the laptop reboots. I managed to read out the message on top of the screen:

UNMOUNTABLE_BOOT_VOLUME

Does this mean that my  XP install is screwed? I've tried to google around for answers. Microsoft suggests that I should run chkdsk /p in a recovery console, which says that 'there seems to be an unrecoverable problem' with the partition setup. I am inclined to believe that something in the partition table makes windows kill itself and that the majority of the file system actually is OK. Can anyone please point me in the right direction? I don't feel ready to take the plunge into an all-linux environment yet but would prefer to dual-boot for a while.

---

### Post by theChauvinist on 2005-04-13
Sorry, I can't be of huge help, but if all else fails if you use a linux live-disk such as Knoppix you should be able to view and recover any data that does exist.

Got no idea how to solve the actual problem though, sorry...

---

### Post by nuke on 2005-04-13
Yesterday evening I did an install of Ubuntu onto a laptop with XP running.  

Did your install complete?  I did have a problem when I needed to restart the install after it hung part way.  Try and run through the installer again and let the installer put the information into the mbr. My XP install was OK, but since the installer didn't finish, I couldn't get to the XP partition and XP start-up.

If that doesn't work, do a google on reinstalling the mbr using the XP installer CD.  You should at a minimum get back to running XP and start again with the Ubuntu install.

I hope you are successful.

Nuke

---

### Post by Grul on 2005-04-13
I never managed to get my XP install back. All the Microsoft recovery tools reported 'unknown disk structure', rewriting the windows MBR did nothing except removing my ability to access GRUB. So here I am reformatting, wondering exactly *what* the Ubuntu partitioner did to the windows partition. Good thing I had the wits to back up my data I guess.

---

### Post by az on 2005-04-13
Did you look for bug reports about this?

bugzlila.ubuntu.com

---

### Post by Nu-Buntu on 2005-04-14
This is one of the weird things I have encountered with Linux of many flavors in a dual boot environment. Sometimes Lilo or Grub futzes with the MBR to the point that Windows won't boot.

However, last night I took the plunge with Ubuntu on my Dell laptop. I have an XP SP2 installation using FAT32, as well as an ext3 partition and a swap partition. I used to have Mandrake on the ext3, but had some issues. I had previously installed grub on the ext3 partition and used a shareware program called OSLoader to choose which platform to boot. I didn't trust putting Grub on the MBR, as I have had nightmares with that in the past.

Well, after using the Live Hoary CD, I decided to plunge in with a full install, and reformatted the Mandrake partition using the Ubuntu installation routine. I checked the place to put Grub as the ext3, but once the installation took place, I got a screen I have never seen before in any distro. It listed my Windows partition, and said if this was correct, it was safe to put Grub in the MBR. Reluctantly, I agreed, but when all was said and done, I am pleasantly surprised to say that I can now easily boot from Grub to Ubuntu or Windows XP with no problem. Very nice, and no third party boot manager needed. 

Since I am still somewhat of a Linux noob, I need to see how to get my wireless network operational and how to have Ubuntu mount the XP partition. But I think these will be fairly easy. The dual boot is as slick as any I have ever done.  \\:D/

---

### Post by Lovejoy on 2005-05-04
You're doing what I did a month ago. I had XP on my computer, set up some partitions and installed a linux OS which was supposed to let me boot either way. When I tried it I could only get the first screen of Windows for a moment and then it was gone, back to reboot. After lots of trial and error here's what I finally did.

I used Ranish partition manager and xosl boot manager. They're free at [http://www.ranish.com/](http://www.ranish.com/) If you do it the way I did you lose everything you've got installed right now. First you boot with a DOS system floppy, then put in the XOSL floppy and install XOSL. It will also install the partition manager. Then go to the partition manager and set up your partitions. You can set up lots of partitions, but really what worked for me was limiting it to 4 primary partitions. Your swap file is on one of these primary partitions, so you can install up to three OSs. When you're finished setting up each fat  partition it asks if you want to format now, answer yes. When you're done with all the formating save with f2 (I think it's f2, it tells you at the bottom of the screen).

Next step install windows. It will take over and write over your xosl boot manager. So when you're done installing windows, reinstall xosl. Then install ubuntu or whatever. When I installed Ubuntu it gave me the option of installing its boot manager in MBR or the local partition. Install it in the local partition.  

Then when you boot up, your computer goes to xosl first and you can choose which system to boot. You can set xosl to automatically boot your favorite after so many seconds unless you hit escape to choose a different system. 

I hope this helps. I think it took me three or four tries to get everything the way I wanted it, but that's another story . . . :???:

---

