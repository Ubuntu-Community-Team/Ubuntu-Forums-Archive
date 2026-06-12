---
title: "Created Partition and Installed Ubuntu But Now Cannot Access Windows 10"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by wholesomepear on 2016-09-14
I created a partition successfully and installed Ubuntu alongside windows 10. When I boot up the menu lists Ubuntu, and some other options. I click on the option that says windows and it just loads and loads forever at the screen with the windows logo. I wish I could use only Ubuntu but I do require windows for certain programs that can not run on linux OS.

All of my windows data is still in the hard drive, my drive states 786gb available. The trouble I am having is booting windows? Any suggestions?

Its very important that I can get back into my windows OS as I have valuable work within my programs.

---

### Post by oldfred on 2016-09-14
In Windows did you turn off fast startup or its always on hibernation. 
Or did you use the installer to resize the NTFS partition. Windows NTFS always needs chkdsk from Windows repair/recovery console after a resize.
Grub only boots working Windows or Windows that is not hibernated, nor needs chkdsk.

       May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by wholesomepear on 2016-09-15
Thank you for the reply. Yes I did turn off fast start up as I read to do that online. I created the partition in windows it's self by shrinking the main space.
Is there anyway to get windows out of hibernate please?

Thank you I will check the link now.

---

### Post by wholesomepear on 2016-09-15
For some reason I can not reply with the result from the command. I get server access issues.

---

### Post by oldfred on 2016-09-15
If a forum issue, just retry, it is having problems.

Boot-Repair does require Internet access, is that working?

If Windows 10 and UEFI install, you should always be able to directly boot Windows from UEFI boot menu. Direct access to that is often f10 or f12, but check your system's manual.
If you installed Windows 10 yourself in the 35 year old BIOS/MBR configuration, you will have to reinstall a Windows boot loader to MBR.

Either way best to have a Windows repair/recovery flash drive. Then when Windows breaks, you can fix it. Grub only boots working Windows.

       Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

