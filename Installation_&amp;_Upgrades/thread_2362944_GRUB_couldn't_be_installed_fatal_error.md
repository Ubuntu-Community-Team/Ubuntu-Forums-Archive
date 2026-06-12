---
title: "GRUB couldn't be installed fatal error"
date: 2017-06-04
forum: Installation &amp; Upgrades
---

### Post by snova2 on 2017-06-04
Hello everyone,

i am not new to using Linux and have some knowledge about it  but i never Installed it by myself.

so i tried to do so now . i downloaded Ubentu 14.04.2-destop-amd64.iso and used Rufus to create a usb stick to boot from .

after setting up my partitions as follows:

sda 80 Gb ( an HDD for windows 10 recovery)
sdb 100 Gb ( C:\ of win10)
sdb 600 Gb ( D:\ of win 10)
sdb 260 Gb ( G:\ of win 10)
sdb swap 8Gb 
sdb /  20 Gb 

so the installation kept going BUT right before the end this shows " GRUB couldn't be installed on this partition fatal error ." 


before posting i have read other threads but none matched my problem.

PC : 
-Tour Type (a desktop one)
-Win 10 only 
-2 HDD sata (80 GB + 1 TB)

please be as explicit as a human can be .

thank you for the time you are given , have a nice day.

---

### Post by LastDino on 2017-06-04
Is it MBR/EFI install? 

During installation, you will have to select partition for installing the grub, usually that is usually your "/" by default, you can also make separate boot partition and maintain grub from there. Which way to go will depend on whether it is MBR/EFI install. 

Meanwhile, for in detail readings, search for Oldfreds posts on here.

---

### Post by snova2 on 2017-06-04
so  this is the RUFUS configuration :
[ATTACH=CONFIG]275461[/ATTACH]

i only made one partition is a" / " 

is it better to make 2 ? one / and one /home ?

---

### Post by yancek on 2017-06-04
You failed to answer the question posted above by member LastDino.  That is necessary.  Take a look at the link below which is the official Ubuntu documentation on the subject.  If you scroll down the page, it will explain how you can tell if you are booting EFI or MBR.  With windows 10 pre-installed, it is almost surely EFI so using those instructions will be necessary.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

How did you create the partition for Ubuntu?  If you did it from windows, you will have to format it during the install of Ubuntu as windows default is not capable of formatting with a Linux filesystem.

I don't know what you did to get the error "GRUB couldn't be installed on this partition fatal error" but with the older MBR, you would install to the MBR not a partition.  With EFI, you install it to the EFI partition where it will create a separate directory for the Ubuntu EFI files.

It is not necessary to create multiple partitions.  The "/" root filesystem partition is all that is necessary as you can easily create additional partitions later if you want.

---

### Post by snova2 on 2017-06-04
partition have been created with the ubuntu installer .
also this is a win 7 to win 10 upgrade .
some people suggested me to turn off fast startup in win10 and fast boot.
also it's important to say that i have a limited knowledge about MBR and EFI , what are these? 

thank you.

partition have been created with the ubuntu installer .
also this is a win 7 to win 10 upgrade .
some people suggested me to turn off fast startup in win10 and fast boot.
also it's important to say that i have a limited knowledge about MBR and EFI , what are these? 

this is how the HDDs are with "réservé au système" meaning " reserved for the system.

thank you.

---

### Post by oldfred on 2017-06-04
Your drives must be MBR, as you do not have the ESP - efi system partition.
And your partitions look like a typical Windows BIOS/MBR configuration.

But your F: drive may be an issue. Somehow with only one partition it shows dynamic partitions. Dynamic is a proprietary Microsoft partitioning and does not work with Linux. But if not wanting to use F: for data in Linux it may be ok, but generally better not to use Dynamic. 
 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.  But some third party tools may work, but you still need good backups.
      
 [http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

Does not matter whether Windows is UEFI or BIOS, the fast start up setting in Windows must be off.
       
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by snova2 on 2017-06-04
okay, i tried to install again , here the thing:
when booting (pressed f12 ) entered teh boot menu i had :

to choose between UEFI USB DEVICE  or USB DEVICE.
i chose the no UEFI option so i got this screen
[IMG]http://pix.toile-libre.org/upload/original/1347445119.png[/IMG]
it loaded then started  to install  until at some point i got the same message " GRUB couldn't be installed in sda " but this time i got to choose between 
-cancelling the installation 
-choose another partition
-try again 

i chose another partition the sda 7 ( meaning the swap zone i believe) 

installation ended  was a success need to reboot . rebooted straight into win 10 with no way to choose Linux.

---

### Post by ubfan1 on 2017-06-04
I'm not that familiar with the Widnows disk display, but I don't see an extended partition on your picture, so maybe that disk is actually GPT partitioned.  In that case, you will need a separate, small (1-2M) partition (no format), flagged grub-bios in order to install legacy grub.  It looks like you have free space, at the end, try making the partition there, but usually, the partition is towards the beginning of the disk.

---

### Post by snova2 on 2017-06-04
update , i read the thread about " boot-repair" followed teh instructions  and here we are ubuntu is working !! 
i got to select it form the selection menu (grub) at booting 

NOW the deal is WHERE is my Win 10 , ubuntu shows me that the files are still there but i only  got to choose if i wanted ubuntu or advanced option .

i got a Url from boot-repair

paste.ubuntu.com/24773634

please i really need acces to win10 it's as important for me as ubuntuis for you :D

---

### Post by ubfan1 on 2017-06-04
Can you select the sda disk to boot from?  Maybe that will boot Windows.  That is the disk with the dynamic partition, which Grub cannot read, so of course it cannot see Windows.  If that works, change your boot order to the OS you use most frequently, and use the boot selection at power-up (some function key at power-up, varies by machine, but try F12) to select the other OS.

---

### Post by snova2 on 2017-06-04
FINALLY  it's has WORKED , i gave birth !

recap : ubuntu & win 10 are working 

after the update of ubuntu i got to restart my Pc boot from the Main HDD ( where all of them  are parted) i noted 2 new components : win 10 dev1 win 10 dev2 
lunched dev 1 and now i got both .


THIS thread is SOLVED. Thanks to your my friends !

i am tempted to write a guide on what could be the main difficulties a newbie will face during the installation if this could help .

---

