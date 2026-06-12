---
title: "Grub error 17"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by jasper_m on 2006-08-12
I installed Dapper, and everything was ok. Until I rebooted the comp. It leaves me with a screen "Grub Loading stage1.5. Grub loading please wait... Error 17".

I did some searching and found out that error 17 means that partition exists, but GRUB doesn't understand it. I also think I've located the problem: my comp has 3 HDDs, one SCSI drive, two IDE drives. Ubuntu is installed on one of those and so is GRUB (on hd1,1). On grub on LiveCD hd0&hd1 are IDE drives and hd2 is 
the SCSI drive. On a GRUB boot floppy, hd0 is the SCSI drive.

And some potentially useless info: The GRUB boot floppy also doesn't show my Linux HDD's partitions when i write root(hd2,1), it says 1 exceeds cylinder count reported by BIOS. However, unhide (hd2, 1) gives no output, but if the number exceeds the real limit, it will complain.

I've looked at other forum posts about this error, and they all seem to be problems with BIOS settings or RAID or something. My computer doesn't have RAID. And I've not changed my BIOS settings after install.

Maybe someone could give me instructions how to make GRUB use the correct HDD? 

Thank you in advance.

---

### Post by Herman on 2006-08-12
> I installed Dapper, and everything was ok. Until I rebooted the comp. It leaves me with a screen "Grub Loading stage1.5. Grub loading please wait... Error 17". I did some searching and found out that error 17 means that partition exists, but GRUB doesn't understand it. I also think I've located the problem: my comp has 3 HDDs, one SCSI drive, two IDE drives. Ubuntu is installed on one of those and so is GRUB (on hd1,1). On grub on LiveCD hd0&hd1 are IDE drives and hd2 is the SCSI drive. 
On a GRUB boot floppy, hd0 is the SCSI drive. Okay, there, jasper_m, so I think that Grub was installed on the right MBR okay, at least you are getting an error message.
You can use any of two or three ideas here, whichever one suits you.
1) You could boot the Ubuntu Dapper 'Desktop' Live/Install CD and open a terminal in that. Then mount your Ubuntu partition and 'sudo gedit' the /boot.grub/menu.lst file and edit the Ubuntu entries in that to make sure  they have the correct information regarding disk and partition designation.
For an illustrated example of how to do that, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").
2) You could boot Ubuntu from the Command Line and then edit your menu.lst file in Ubuntu, for an illustrated example of how to do that, [*Click Here. *]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
3) You could download the latest Super Grub Disk in another computer and extract it and burn it to a CD and use that to boot your computer with and then fix your menu.lst file. For more on S.G.D., [*Click Here.*]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Once you are able to access your /boot/grub/menu.lts file in one of those ways, (whichever you thing will be the easiest for you), if you need any help with it, you can copy it and post it here, mainly just the bottom part of it, with the operating systems entries. ```
sudo gedit /boot/grub/menu.lst
```
For anyone to be able to help you with it, you would also need to include a copy of the output from the following code, ```
sudo fdisk -lu
``` If you already know how to do those things by yourself, then just ignore the second half of this post.
There is no guarantee that the menu.lst entry is your problem, it could be some other problem, but the menu.lst is an easy thing to start with.

I hope this helps you, Regards, Herman :D

---

