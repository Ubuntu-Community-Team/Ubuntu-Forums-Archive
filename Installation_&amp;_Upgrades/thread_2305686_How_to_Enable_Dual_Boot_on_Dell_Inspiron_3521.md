---
title: "How to Enable Dual Boot on Dell Inspiron 3521 ?"
date: 2015-12-08
forum: Installation &amp; Upgrades
---

### Post by Mubeen_Asghar on 2015-12-08
I tried to install Ubuntu 14.04 on my dell inspiron 3521 Windows 7, how would I enable a dual boot option on startup ? I used my USB as a bootable disk, but it doesn't work, whenever I unplug the USB, it starts with windows as usual and doesn't show a dual boot option. Further I also have a installation problem, when my system boot with Ubuntu USB then it doesn't install the Ubuntu completely, with every restart it shows the same options again and again.

---

### Post by oldfred on 2015-12-08
Did you reinstall a Windows 8 system with Windows 7 or was it originally Windows 7?

Post this from terminal in live installer:
       sudo parted /dev/sda unit s print

---

### Post by Mubeen_Asghar on 2015-12-08
Windows 7 Originally

---

### Post by grahammechanical on 2015-12-08
> when my system boot with Ubuntu USB then it doesn't install the Ubuntu  completely, with every restart it shows the same options again and  again.

What options are these? Try Ubuntu & Install Ubuntu? Have you actually installed Ubuntu to the hard disk or only created a Ubuntu lives session USB memory stick?

Did you do this? 

[URL="http://www.ubuntu.com/download/desktop/install-ubuntu-desktop"]http://www.ubuntu.com/download/desktop/install-ubuntu-desktop
[/URL]

Or only this?

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Regards.

---

### Post by Mubeen_Asghar on 2015-12-08
Yes, those were Try Ubuntu & Install Ubuntu.....I tried to install it but when I restart my system then it doesn't show a dual boot option when I unplug my USB, and when I plug it again then it again starts from the very beginning and shows the same options Try Ubuntu and Install Ubuntu......

---

### Post by oldfred on 2015-12-08
Best to see details:

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mubeen_Asghar on 2015-12-08
Ok, Here is the Link :
[http://paste.ubuntu.com/13840089/](http://paste.ubuntu.com/13840089/)

---

### Post by oldfred on 2015-12-08
It looks like you are trying to install wubi, which is not supported anymore.
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

    
And you have SFS partitions or Windows dynamic.
       Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

    
Then you need to convert one of your 4 primary partitions to an extended. You will have to backup and delete that one partition.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

    
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Then after you have full backups of everything.       
 [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

           
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

