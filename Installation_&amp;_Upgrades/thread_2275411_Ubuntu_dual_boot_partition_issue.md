---
title: "Ubuntu dual boot partition issue"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Digital_Pirate on 2015-04-25
[FONT=arial]Hello, I have windows 8.1 installed on my laptop and i want to dual boot ubuntu. Everything goes fine until i want to make partition for ubuntu where it show the HDD. There is now ntfs drives which show the windows system drives that i made on windows 8.1 instead it shows the whole HDD as free space. I have 750gb HDD on my laptop and it shows whole 750gb as free space not the remaining. I have watched many videos and read many articles and blogs but no avail. The question is what is the solution of this and if i make partition on this 750gb free space will it format the windows 8.1 or dual boot along with it without harming the windows OS???????? I am doubtful about the result so help is required ASAP.[/FONT]

---

### Post by oldfred on 2015-04-26
Back up Windows.
Make a Windows repair/recovery flash drive.
Use Windows to shrink the main Windows NTFS partition and reboot immediately so it can run chkdsk and make repairs to its new size.
Make sure fast startup is off in Windows. And if UEFI has fast boot turn it off.
Use gparted on Ubutnu live installer to create partition(s) for Ubuntu.
Use Something Else to choose partitions you created. Click on change button to chose which is / or /home.
If unsure of details of any of above see link in my signature.

Several of most important links, which are first in link in my signature.
       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

