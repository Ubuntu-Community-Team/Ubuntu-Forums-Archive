---
title: "Any Official instructions for upgrading to Trusty while using a dual-boot?"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2014-05-12
I am using a dual-boot with Ubuntu 13.10 & Windows 8. I have noticed people in my situation have already experienced issues messing the GRUB file as a result of just clicking on that inviting button when Ubuntu 13.10 prompts you to upgrade. 
If not official, are there at least a list of steps to follow that would guarantee at least 98% of the upgrade process?

Thanks in advance guys,

JDL

---

### Post by LastDino on 2014-05-12
Delete all the third part drivers if any (e.g:Nvidia) and remove PPA's. Take back up and possibly image of 13.10 installation before removing those drivers and PPA's.

Then click on that inviting icon  and cross your fingers :3

---

### Post by Frogs Hair on 2014-05-12
[https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)

---

### Post by oldfred on 2014-05-12
Is this a UEFI system?
Did you run Boot-Repair's 'buggy' fix as that also will cause issues.

There is this bug.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)

And it may be related to using grub-efi and that must not correctly update the re-install entry.
Is this entry in list empty? With grub-efi not sure this command even works. 

 #To see what drive grub2 uses see this line   - [COLOR=#ff0000]grub-pc/install_devices[/COLOR]:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

And similarly this should update entry, but with grub-efi??

 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by javierdl on 2014-05-12
LastDino, thanks for replying. Talking about "imaging", is there any tool you could recommend that is NOT Clonezilla?

Frogs Hair, thanks for the link. But it seems it is for the simpler situation when all you have installed in your desktop pc is Ubuntu. But in my case I have a dual-boot. Thanks anyway.

oldfred, fortunately I don't have a UEFI system yet, so this should simplify things for me.

JDL

---

### Post by oldfred on 2014-05-12
Others suggest these as Windows backup options:
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

I prefer to plan just to reinstall Ubuntu so I do not back it up. But do backup /home, all my data, some settings in /etc, grub settings that I have changed, and a few other things in system. I export a list of installed apps so I can easily reinstall.
      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)


 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

---

### Post by LastDino on 2014-05-12
I've used Fsarchiver to clone my initial Xubu installation with all my softwares, which is command line tool. I haven't actually ran into situation where I might need to restore them so I can't tell you exactly if it is good or not. 

I would suggest checking how image is mounted on some other HD if available before relying on them. I don't have any particular data that I would consider important enough to do so, but you should as a good practice.

---

### Post by javierdl on 2014-05-12
Olfred, this list of links is excellent! I'll take my time studying it before I get my hands dirty ;)

LastDino, thanks for sharing! 

JDL

---

### Post by javierdl on 2014-09-04
A quick visit to advise that after backing up files and creating clone-image files of both OSs, I went ahead to click on the OK button when Ubuntu 13 asked me to upgrade, and ... it all went unbelievably smooth! The Ubuntu 14 installer took care of literally everything! And yes, the Grub file was modified as a result of it, BUT now is simpler too :)

Thanks all again for helping :)

JDL

---

