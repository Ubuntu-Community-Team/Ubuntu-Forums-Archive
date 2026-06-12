---
title: "How do I make a backup of Ubuntu settings for an XP reinstall"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by tunznath on 2008-07-02
Hi All
I would like to know how I can make a backup of my Ubuntu settings, I heard there is a way to copy the home folder - will this keep all my ubuntu settings and preferences, 

Anything else I can do to keep my settings as Ubuntu is working great 

Then I am going to reinstall XP (a nasty virus has wrecked my XP install, and I can no longer connect to the net with firefox or IE, but can with safari  - WEIRD) I will be following the instructions at 
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Anyone have any hints or anything that will make this painless.

BTW I appreciate Ubuntu way more(if thats possible as I REALLLLY like ubuntu) after a 12 hour Virus and spyware scan of my 3 hard drives with AVG - that is madness - how do organizations cope with that???

Thanks in advance

---

### Post by tsger on 2008-07-02
Maybe this link will help, it explains how to move your home directory to its own partition.  

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by tunznath on 2008-07-02
Thanks for that tsger - A Question how do I know how big I need to make the home partition?

Is there any worry that when i reinstall windows as per the instructions at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) that i could screw up the whole install??

---

### Post by tunznath on 2008-07-02
Just read through the comments on the install xp second and it doesnt look like it will work - it seems to work with a new install without an XP already installed - also as per the instructions I type
 
sudo gedit /boot/grub/menu.lst. 

and get nothing so I cant back up my grub - any thoughts

---

### Post by Partyboi2 on 2008-07-02
When you get to the windows partitioning stage it should show your partitions and list the ubuntu ones as unknown file system, which is fine because all you need to do is delete the windows ntfs partition and then use the unpartitioned space from that to reinstall windows, not touching the ubuntu ones. After you reinstall windows you will need to [[COLOR=Blue]restore grub[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351"), as windows would have written to the mbr.

---

### Post by tunznath on 2008-07-02
Thanks partyboi2 - that helps - i have made a copy of my grub, and saved it  - then after reinstalling XP - can I just replace the "new" grub with the old one I copied and it will work??

---

### Post by Partyboi2 on 2008-07-02
You can back up and restore  by following [[COLOR=Blue]this[/COLOR]]("http://ubuntu.wordpress.com/2005/10/20/backing-up-the-mbr/"). When ever I have reinstalled windows all that was need was to restore grub using the live cd, easy way, but if you are needing your original settings then  follow the mentioned link.

---

### Post by damis648 on 2008-07-02
All you need to do is snstall it as normal, onto the partition when you would like. When you are done, you must reinstall grub to the MBR, as XP will overwrite it. To do this, boot up with the liveCD and start a terminal. In terminal,
```
sudo grub
```
and you will be faced with a new prompt. Now:
```
find /boot/grub/stage1
```
and enter. This will return the partition on which Ubuntu/GRUB is located. Now:
```
root (hd0,0)
```
replacing "hd0,0" with what was returned by the previous command. Finally, run
install /dev/sda
replacing hda with the boot disk (this should be fine).
Good Luck!

---

### Post by tunznath on 2008-07-02
Hi Thanks for everyones help - Hope that it can help someone as well- I used the XP disk that came with my toshiba and there wasnt any option to install to a partition - tried the expert install and it wasnt very clear - it was the OEM disk - so nothing i found on the net helped - so my ubuntu is gone - busy reinstalling all the drivers for XP at the moment - then I will be on to ubuntu - hope I can get it all back the way it was - it was running sweetly - now i am remembering things i should have backed up - nothing too important- hopefully - just a pain to find again. - i am not very happy with virus and trojan writers at the moment - BTW anyone that thinks that Ubuntu is a pain to install try reinstalling XP - finding driver disks etc

---

