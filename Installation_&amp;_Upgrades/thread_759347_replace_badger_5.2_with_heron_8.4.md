---
title: "replace badger 5.2 with heron 8.4"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by tellmehow on 2008-04-19
Using book 'beginning  ubuntu linux' CD  I installed badger 5.10. as a dual boot for my Dell 505 laptop. Its not upgradable. I downloaded  ISO for Heron 8.4. I wish to replace 5.2 with 8.4. I have no data to save. Docs do not recommend reinstall which I will do if thats my only choice. Is their a better way ?

tellmehow

---

### Post by PmDematagoda on 2008-04-19
I don't see why you can't do a clean install of Ubuntu 8.04, from where did you hear the contrary?

Could you also post the specifications of your PC.

---

### Post by tellmehow on 2008-04-20
PmD thank you for your reply.
I'm confused about ubuntu installations. The one below is 'clean install upgrade'. How does this differ from 'fresh install' , 'reinstall' ? Is this my only choice to go from badger 5.10 to heron 8.04?
Since there is no data or configurations to save is there a better choice? How is unbunto removed from the HD?  Celetron 1.38 processor , 60GB HD    with half 8GB of free space allocated to ubuntu.

The info below is from  ... community/installation/  forumn

Clean Install Upgrade (not recommended)
If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory.

Back-up any important data before following this procedure as data loss is possible, and very well may be likely.

Obtain an installation CD for the release of Ubuntu 7.04 you wish to install, and boot from it.
Start the installation process. When you reach the Prepare disk space stage of installation, choose the Manual option and press Forward.
Identify your current '/' (root) partition. Select '/' as the mount point and ensure that Format is ticked. You will lose all data on this partition and the new version of Ubuntu will be installed there instead.
Identify your swap partition and set its mount point as 'swap'.
Identify your /home partition. Set its mount point as '/home' and make sure that Format is not ticked.
Continue installation as normal until you reach the Who are you? stage, enter a username and password which exactly match your current username and password.
Complete the installation as normal.
Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

tellmehow

---

### Post by PmDematagoda on 2008-04-20
In your case since you have no data to be backed up you can either do the install using the instructions you have provided or you can just do a full clean install by formatting all the partitions or by asking Ubuntu to do it automatically.

---

### Post by tellmehow on 2008-04-24
Thank you PmD. I down loaded 8.04 ISO file to the desktop; dragged it to CD Creator and did selected write to disk, set speed to 2x. Clicked Write to Disk. Got this dialogue: Since this a single ISO image gave choice of write as image or as file. I tried as image nothing happened. Then I did as file  and got CD with my ISO image. I made sure I could boot from CD. I turned computer back on and received my standard 5.2 boot screen with safe mode,other os and Xp options. Have I done some thing wrong? I tried this sequence two more times with same result. I tried to boot from this CD in my Win Xp computer. Windows xp booted normally. How do I get 9.04 to boot?

Tellmehow

---

### Post by PmDematagoda on 2008-04-25
You burnt the ISO as a file, not an image which is incorrect and would not allow you to boot the CD, what burner software were you using anyhow?

---

### Post by tellmehow on 2008-04-25
PmD. Right. I am using CD/DVD Creator-File Browser under Nautilus (Badger 5.10). When I chose the image option, I got the dialog: No such file or directory. The file 'ubuntu-8.04-rc-desktop-i386.iso' is not a valid disk image.    What should be  my next step and how do I execute it ?  Iappreciateyour help.

Tellmemore

---

### Post by PmDematagoda on 2008-04-25
> **tellmehow said:**
> PmD. Right. I am using CD/DVD Creator-File Browser under Nautilus (Badger 5.10). When I chose the image option, I got the dialog: No such file or directory. The file 'ubuntu-8.04-rc-desktop-i386.iso' is not a valid disk image.    What should be  my next step and how do I execute it ?  Iappreciateyour help.

Tellmemore

It may be that your ISO image is corrupted, please refer to this [Ubuntu Wiki]("https://help.ubuntu.com/community/BurningIsoHowto"), especially the MD5Sums section.

---

### Post by tellmehow on 2008-04-25
PmD: I down loaded the current 8.04 ISO image from Argonne Labs. When I attempted to write it to disk as an iso image, again using CD/DVD Creator I again got this dialogue: No such file or directory. The file 'ubuntu-8.04-desktop-i386.iso' is not a  valid image file. What do I now do?

Tellmehow

---

### Post by PmDematagoda on 2008-04-25
Try using a different burning software like Brasero, install Brasero by executing:-
```
sudo apt-get install brasero
```
After installation Brasero can be found in Applications>Sound & Video>Brasero Disc Burning.

---

### Post by tellmehow on 2008-04-26
PdM: Thank you for your valuable help. I clicked on the link: [http://help.ubuntu.com/community/BurningIsosHowTo](http://help.ubuntu.com/community/BurningIsosHowTo). I scrolled down to my computer and followed the instructions.    I inserted my 'invalid' 8.04 iso image CD. When CD/DVD Creator was automatically opened , I closed it;  right clicked on the iso image on the desktop; selected burn to a CD. In less then 30 minutes I had a bootable  8.04 iso image CD. I reinserted the CD, powered down the computer, and booted successfully from the image CD. I chose a form of partitioning that retained some of Badgers 5.10 data. I am writing this in OpenOffice.org Writer and will paste to the thread reply form. 

 Tellmehow     :guitar:[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

