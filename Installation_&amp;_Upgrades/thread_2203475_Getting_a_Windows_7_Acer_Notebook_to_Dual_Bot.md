---
title: "Getting a Windows 7 Acer Notebook to Dual Bot"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by moses65 on 2014-02-03
I am moving a third machine to Ubuntu.  One was a pure install on an old IBM G40 - perfect.  Next was a dual install on an old HP Notebook running XP.  Again perfect.  Now I have loaded a newish Acer Notebook wich is running Windows 7 and we want want to have both systems available.  I am getting the Dual Boot Menu but when I select Ubuntu it does not work.  
Any ideas ?

---

### Post by oldfred on 2014-02-03
We need to see details:

Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by moses65 on 2014-02-04
Here is the ilnk:  [http://paste.ubuntu.com/6873691/](http://paste.ubuntu.com/6873691/)

---

### Post by oldfred on 2014-02-04
Not sure if you installed wubi or did full installs on old systems, but your new system is UEFI with gpt partitioning.

Most Windows 7 systems were BIOS/MBR but a few were UEFI/gpt. But Windows 7 systems do not have secure boot and all its issues and install of Ubuntu to another partition usually works very well.

Wubi does not work with gpt partitioned drives or any UEFI system. So 12.04 is last supported wubi as all new systems are UEFI with gpt partitioning. Best to just remove wubi and do a full partitioned install.
This has uninstall instructions:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Use Windows tools to shrink the Windows NTFS partition and reboot so it can run chkdsk and make its fixes to its new size.
Make sure Windows 7 is not hibernated, but you do not have the Windows 8 always hibernated issue.

Backup Windows and create a Windows repair flash drive.

Download the 64 bit version of Ubuntu.
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

UEFI is a lot different than the 30+ year old BIOS with MBR(msdos) partitioning. But it has lots of new capabilities. But both vendors & Linux are making lots of fixes as UEFI is relatively new (only 10 years. But Mac since converted to Intel chips and Windows 8 both use versions UEFI.

May be best to update UEFI/BIOS from vendor and use the newest Ubuntu version as it has many updates to UEFI grub booting. Many of those are secure boot related which do not apply to you, but new versions just work better also.

Lots of info (too much), links to UEFI data in link in my signature. Much will not apply as yours is a relatively simple dual boot.

Full walk thru of install, but first part is Windows 8, but you can skip most of that and see the details of installing Ubuntu.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

