---
title: "Is it better to do complete reformat of hard drive"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by mal3 on 2014-04-22
I have just installed Ubunto to a older laptop after having Windows 7 on it, and that was ok - but I have read that it may be better really to completely reformat the hard disc - for the ext format of Linux as this gives maximum long term benefit in terms of reliability ??.

Is that a good idea - - and how can i do  it - i assume it will need doing after booting from the DVD/ disc .

Many thanks
Mal

   HP G61-415SA Notebook
 2.1 GHz Intel Pentium Processor T4300
 4 GB DDR2 memory
 Intel Graphics Media Accelerator 4500M

320 GB SATA Hard Disk Drive 5400 rpm

 802.11 b/g Wireless

---

### Post by oldfred on 2014-04-22
That is not a real old laptop. My 2006 Toshiba only has 1.5GB of RAM and runs the 64 bit version of Ubuntu, but I do have to change from Unity which needs a better video processor to fallback/flashback which is less intensive and the old menu system. 
Best to try with live installer. 

Most users install in dual boot. Ubuntu does need its own file formats, but will read NTFS or FAT32 without issue.
Most users dual boot as there often is one application or game that they cannot live without that just does not work in Linux or the equivalent type application is just not good enough. But some Linux apps are just as good or even better, but you have a learning curve because of differences.

Most Windows 7 systems use all 4 primary partitions. 
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

Even if you decide to erase Windows, best to make a full image backup. Then you could restore Windows in case you need it, or want to sell it later.
      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by grahammechanical on 2014-04-22
When you install Ubuntu what options did you chose? Did you choose, Use the Entire disk? When we install Ubuntu to use the entire disk it will format the hard disk to the Ext4 file system by default. It will in effect remove any operating system and data on the drive. 

If you format that drive now, even if you format it as Ext4 you will destroy whatever operating system, even Ubuntu, is on it and any data as well. Get ready to re-install.

Regards.

---

### Post by mal3 on 2014-04-22
Thanks,
Originally I did a dual instal - keeping Win7 - but after I decided that I liked to continue playing with Linux - I did a completely new instal replacing windows - so it would seem it has Ext4 . 
So far I havent transfered all my user files onto it ( I still have a newer Tosh laptop with Windows 8.1 on it !!!, and need to keep that for compatibility purposes ) but plan to use Linux as my principle Internet machine due to its much more secure system. 

thanks for the advise
Mal

---

