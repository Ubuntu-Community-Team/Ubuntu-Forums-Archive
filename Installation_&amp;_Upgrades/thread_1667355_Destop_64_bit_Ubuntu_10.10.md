---
title: "Destop 64 bit Ubuntu 10.10"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by DCarrollUSMC on 2011-01-14
I had Windows vista originally on my desktop PC.  I have installed Ubuntu 10.10 and configured everything the way that I like it, and now I'm interested in removing windows vista from my computer completely.  Can someone help me by informing me of some of the risks of doing this, as well as the benefits in addition to steps describing how to complete such a task if desired.  Thank you in advance for the help. Please let me know what information you need.  I have attached what GParted said when I ran it the first time.

---

### Post by Quackers on 2011-01-14
Welcome to UF :-)
The main downside is that you won't be able to go back to Windows without buying it again. I would recommend that you boot into Windows and create the recovery dvd's, if you haven't done that already. In fact, I would make 2 sets, and check that they both work first. You should also make the repair disk (which Windows calles a recovery cd) by going in to Control Panel > Backup & Restore Centre, then choose from the left pane "create recovery cd". Then you can just delete the Windows partitions from gparted.
Then run ```
sudo update-grub
``` from within the Ubuntu desktop.

---

### Post by DCarrollUSMC on 2011-01-14
Quackers,
Thanks for the quick reply and great information.  I've been considering switching to Windows 7 anyway and as a student I have access to discounted rates.  I'm not too worried about losing my windows (as I have already made copies of everything I want from windows)  If you could tell me, is there a chance that while removing the windows partition that I could damage ubuntu?  If that's the case then I will make the recovery disks so that I can reinstall ubuntu if i have to as a last resort.  Also, once I'm in GParted, how can I tell which is the windows partition and can you give me step by step directions to removing the partition?  Please excuse my ignorance, I am not very experienced.

---

### Post by Ad1217 on 2011-01-14
If you are running wubi, the linux partitions will not show up to anything other than that Ubuntu installation; they are virtual, and the actual files are inside the Windows ntfs partition. Thus, the above post will delete your Ubuntu installation as well as Windows. You would have to back up, your files, wipe the drive (the Ubuntu installer does this for you), reinstall Ubuntu without wubi, and then put your files back in.

---

### Post by DCarrollUSMC on 2011-01-14
> **Ad1217 said:**
> If you are running wubi, the linux partitions will not show up to anything other than that Ubuntu installation; they are virtual, and the actual files are inside the Windows ntfs partition. Thus, the above post will delete your Ubuntu installation as well as Windows. You would have to back up, your files, wipe the drive (the Ubuntu installer does this for you), reinstall Ubuntu without wubi, and then put your files back in.
If this is the case then should I switch to my windows operating system and create the Ubuntu install disks then run them to wipe windows?  I would like to avoid this if possible because I want to save my settings that I have so far for Ubuntu and I'm not sure what I'd have to do to save and install my settings if I did this full install.

---

### Post by Quackers on 2011-01-14
If you are running a wubi installation then disregard my earlier post! That will definitely not be good! Did you use wubi?

---

### Post by DCarrollUSMC on 2011-01-14
Yeah I sure did.  I thought I mentioned that but I may not have.

---

### Post by DCarrollUSMC on 2011-01-14
What about downloading the Ubuntu 64 bit  desktop version from the website making the CD and then running it.  Will this wipe everything?  Any chance I'll get the opportunity to keep my Ubuntu settings without creating a disk?

---

### Post by Quackers on 2011-01-14
No :-)
That changes things for sure.
I don't have a link, but I believe it is possible to migrate a wubi installation to a dual boot installation. Once that is up and running you can delete Windows. Do a search for that phrase.
Alternatively, if you can backup everything you need, you can just install Ubuntu from the live cd/usb and use the whole disc for Ubuntu, which will over write the Windows partitions. Then you can replace your data from the backups.
I'll leave you to think about that :-)

---

### Post by DCarrollUSMC on 2011-01-14
I just got done making backups.  It really wasn't much, only what I had time to customize over the past 24 hours.  if it doesn't work or something happens it won't be hard to get back to where I was.  Thanks a lot for your help.  As I am right now, on Ubuntu through Wubi, I'm downloading the 64 bit 10.10 again and will put it on a CD, then can I run that in Ubuntu or should I switch to Vista to run the disk?  Does it matter?

---

### Post by Quackers on 2011-01-14
No, if you burn the image (after checking the MD5SUM of the downloaded iso file) you can change your bios to boot from cd first and then just boot from the cd and select "try ubuntu" or go ahead and install it. Be aware though, that if you select the whole disc you WILL over-write everything on the disc!

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Ad1217 on 2011-01-14
Neither: reboot, and access your bios boot option screen (be quick!) Hit the cd option, and install away!

---

### Post by bcbc on 2011-01-15
If you have fully customised your wubi install then you can just migrate it. Split your /dev/sda1 partition from within windows, migrate to the new one, then do what you want to windows afterwards. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

