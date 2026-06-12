---
title: "Need help to installing Ubuntu without losing Windows 10 Data"
date: 2020-06-18
forum: Installation &amp; Upgrades
---

### Post by chinmayrajyaguru on 2020-06-18
Here's my Window 10 Setup:


C Drive (SSD 250GB) [Wherein installed Windows 10]
D Drive (2TB Data)

**I can fully format the C drive.** _Once I install Ubuntu's latest OS, can I get D drive access?_ Or *I'll lose all data of drive D?*


**In D drive, I have important Softwares, photos, games, and data (.EXE and windows format files). Will I lose it?**


Is there any option or way to install Ubuntu without losing it? :confused:


I'm already using LibreOffice, 7Zip, GIMP, etc. I'm not using any Windows software anymore. Hence, I would like to move on permanently in the Linux world. :KS

---

### Post by mIk3_08 on 2020-06-18
Yes, you can fully change the O.S of that C: drive. just be careful when you reach this stage:

[IMG]https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/optimized/2X/4/46e9947d7b4ad3e96487d81cf61c327485d56b5a_2_690x424.png[/IMG]

you should choose "something else" 

 then here; 

[IMG]https://i.imgur.com/a2Oe9mM.png[/IMG]


after successfully installed the Ubuntu. You can then access the D: drive. Its Unattached.
Be-aware that it is in your hands. Take the Risk. Good Luck!
Welcome to the Linux World.

---

### Post by chinmayrajyaguru on 2020-06-18
First, thank you so much for the reply and description.

But, I can't take the risk with the data I have. This data is very important for my business. :cry:

_I have heard a rumor:_ when you connect a Pendrive or HDD with Linux wherein Windows data or files, it will crash/corrupt.

**Is there any risk-free option? **:confused:


> **mIk3_08 said:**
> Yes, you can fully change the O.S of that C: drive. just be careful when you reach this stage:

[IMG]https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/optimized/2X/4/46e9947d7b4ad3e96487d81cf61c327485d56b5a_2_690x424.png[/IMG]

you should choose "something else" 

 then here; 

[IMG]https://i.imgur.com/a2Oe9mM.png[/IMG]


after successfully installed the Ubuntu. You can then access the D: drive. Its Unattached.
Be-aware that it is in your hands. Take the Risk. Good Luck!
Welcome to the Linux World.

---

### Post by yancek on 2020-06-18
If you have important data on a partition you need to back it up to ANOTHER drive.  I'm not sure what you mean by:

> **I have important Softwares, photos, games, and data (.EXE and windows format files).**  

If you have .EXE files on that partition you will need a windows OS to run them.  No Linux system will run windows executable files.  

As pointed out above, if you do not want to erase the entire drive, you need the Something Else option which is a manual install of Ubuntu during which you can select the partition on which to install Ubuntu.  If you do that correctly, it will have no effect on your data partition.  You need to familiarize yourself with Linux drive/partition naming conventions as Linux does not use the drive letter method used by windows.  Is your windows an EFI install?  Almost any windows 10 pre-install will be.  Take a look at the link below which is the Ubuntu documentation on dual booting with windows 10.  Some of it will not apply if you want to remove windows or install over it but most will if you want to keep a windows partition.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by SeijiSensei on 2020-06-18
If you're that worried, disconnect the drive cable before installing.

---

### Post by ActionParsnip on 2020-06-18
[https://answers.launchpad.net/ubuntu/+question/691385](https://answers.launchpad.net/ubuntu/+question/691385)

---

### Post by mIk3_08 on 2020-06-18
> **SeijiSensei said:**
> If you're that worried, disconnect the drive cable before installing. I agree with SeijiSensei. disconnect the drive.

---

### Post by ubfan1 on 2020-06-18
If you have encrypted your data with a Windows tool like bitlocker, decrypt first!!! If you don't you will probably lose that data if you delete Windows.  (May be inaccurate/old info) Windows encryption seems to include the 30-40 digit system ID as part of the encryption key, so even just moving the disk to another Windows system may not work for decryption.

---

### Post by oldfred on 2020-06-18
If data has any value at all, you need multiple backups. Hard drives fail, lightning or power failure can cause damage even to new drive, and users often make mistakes.

Also make sure Windows hibernation is off, that includes fast start up which also sets hibernation flag on all NTFS partitions.
Linux NTFS driver will not normally mount NTFS read/write as it sees hibernation flag and does not want to write into it and damage it. You can force mount read/only.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by Impavidus on 2020-06-18
> **chinmayrajyaguru said:**
> 
**I can fully format the C drive.** _Once I install Ubuntu's latest OS, can I get D drive access?_ Or *I'll lose all data of drive D?*

If done carefully, you'll still have access to your files on your D partition (which will not be known as a D partition in Ubuntu). However, although Linux can read and write Windows partitions, it cannot fix them if damaged. So if you suffer a power failure and a dirty shutdown of your system, the filesystem will be damaged, the files will be inaccessable and you won't be able to fix it without Windows. So, never rely on Windows (NTFS) partitions for data storage on a Linux-only system. And you can't convert it to a Linux filesystem without wiping all files.

> 
**In D drive, I have important Softwares, photos, games, and data (.EXE and windows format files). Will I lose it?**


Is there any option or way to install Ubuntu without losing it? :confused:


I'm already using LibreOffice, 7Zip, GIMP, etc. I'm not using any Windows software anymore. Hence, I would like to move on permanently in the Linux world. :KSAny Windows-only stuff will be worthless after you wipe Windows. Software like Libreoffice works on both Windows and Linux, so you can still use it. Not the same executable file though, you have to install the Linux version of each of those programs. Which is fairly easy. In fact, you'll find many of those installed by default.

If this is important for your business, don't take any chances. Make sure you've got multiple, versioned backups of all important files on external media. Maybe you want to experiment with Ubuntu on a completely separate computer.

---

### Post by chinmayrajyaguru on 2020-06-23
Thank you so much for the information. I have done this on Sunday. Successfully installed Ubuntu!


Ubuntu - Disks - Mounted successfully.
But while I connect the 2TB drive, it's taking too much load. 
There's no solution/clue to connect Windows Microsoft Basic Data Partition.


Hence, I have installed Windows 10 again for temporary. I will need an extra 2TB drive to backup it.



> **mIk3_08 said:**
> Yes, you can fully change the O.S of that C: drive. just be careful when you reach this stage:

[IMG]https://ubuntucommunity.s3.dualstack.us-east-2.amazonaws.com/optimized/2X/4/46e9947d7b4ad3e96487d81cf61c327485d56b5a_2_690x424.png[/IMG]

you should choose "something else" 

 then here; 

[IMG]https://i.imgur.com/a2Oe9mM.png[/IMG]


after successfully installed the Ubuntu. You can then access the D: drive. Its Unattached.
Be-aware that it is in your hands. Take the Risk. Good Luck!
Welcome to the Linux World.

---

