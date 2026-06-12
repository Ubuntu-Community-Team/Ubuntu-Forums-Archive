---
title: "No bootable device insert boot disc and press any key error"
date: 2014-09-12
forum: Installation &amp; Upgrades
---

### Post by oussama3 on 2014-09-12
Hello Im new here and i have this -hopefully little- problem as the title shows 


i have this one month old laptop it came with windows 7 pro but i wanted to install ubuntu so i got the iso image of ubuntu 14.04.1 downloaded and and booted it into a USB hard drive disk using UNeBoot and then i live booted into ubunto which was the first time i see an OS other than windows . anyway it gave me the option to either test ubuntu or to install it on the hard drive .. i spent some time testing it then ofc i couldnt say no to the install option . i followed the instructions on openclassrooms 
[http://fr.openclassrooms.com/informatique/cours/reprenez-le-controle-a-l-aide-de-linux/](http://fr.openclassrooms.com/informatique/cours/reprenez-le-controle-a-l-aide-de-linux/)

im not sure if there is an english version for that. anyway it basically recommands the partition of the hard disk through the ubuntu installer and gives the exact instructions for that. i followed them and got ubuntu 14.04.1 installed on my hard drive. 
but when i restarted my pc i got this error message No bootable device insert boot disc and press any key.
no idea what to do since im new to all of this and initially wanted Linux because im gonna be studying this in college.
 i read the older thread of the same title but there the poster did not need to keep his windows 8 but i really need my windows 7 and cant afford to lose it. it also contained mysterious terms for me that i couldnt understand.

im sorry for being noob at this so i was hoping if anyone would like to help to use simple language since English is my 3rd learned language and of course idk most of basic things about ubuntu or informatique as i was hoping to learn through using ubuntu. 

but right now im stuck on being able to only live boot to ubuntu through the hard drive disk

also if anyone knows can u please tell me how to set keyboard as azerty and not qwerty because i; having a hard ti;e typing so;e letters as u can see.

also when attempting to install ubuntu again through the live boot it detects both of windows and ubuntu as already installed on the hard drive ... see attachements


. and i can see the partitions i made earlier and they are as follows : ... see attachements

thank you in advance for your help . i really hope i can solve this before dad finds out

---

### Post by oldfred on 2014-09-12
Please post screen shots as attachments not inline. Not everyone has high speed Internet.
You can easily attach screen shots with Advanced editor and the paper clip icon.

Best to see if grub was correctly installed.

Do not run the auto fix, better if we review configuration. Auto fix with simple installs usually works but ocassionly can cause issues. 
Just run the Boot info report and post the link it gives to the pastebin detail report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ubfan1 on 2014-09-12
Take a look at the /etc/grub/grub.cfg file on the hard disk (while running the live media, so you will have to mount it somewhere like /mnt/sda2).  If the hard disk references are hd1... something, edit them to be hd0...  And if there are any references to /dev/sdb...  change those to /dev/sda.
Then try the boot, and if it works, run sudo update-grub to ensure all the disk references are updated.  Sometimes the disks get enumerated differently, (like if the live media gets enumerated first, and gets hd0, then the hard disk will get hd1, which is not present without the live media, so it will not be found.

---

### Post by oussama3 on 2014-09-12
thank you both for your replies 

sorry for the absense of the boot-info report i just came to know what that is. it seems im having trouble getting boot-repair which according to [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) is necessary for the report 
the attachement is a screenshot of the error appeared in the terminal. consequently step 3 in the link above is not possible. pls help me getting boot-repair
also i still need the keyboard configuration it turns out to be very hard to write things like & which appearently is necessary in the terminal. unless there is a copy and paste -from web page to terminal- option which i didnt know of.

and as for ubfan1 im so sorry for being a noob again i really lost you there man i dont know how to take a look at files in the hard drive through ubuntu im just glad firefox is in here and its easy to use.
i will google it right now and i might come back to you when i find out if i ever will. i also dont know how to edit/mount them ...ect 

thank you guys for the help again it is very appreciated.

---

### Post by yancek on 2014-09-12
Boot the Ubuntu on the flash drive, open firefox and go to the site below.  The bootinfoscript on that site provides the same info as boot-repair but doesn't make any attempt to fix anything, just outputs information you can post here.  There are instructions on how to use it in a link in the Description box on that page.  The output file will be named results.txt, post it here. 

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oussama3 on 2014-09-12
ok thank you yancek 
the txt file is attached 
i know it should ve been in the first post xD

i was thinking maybe turning off secure-boot in the bios settings might solve this or maybe uninstalling ubuntu and reinstalling it or cancel the partitions somehow. there are other suggestions in the internet but i m not comfortable trying them unless they r recommanded here.

anyway i hope the boot info report helps define the problem. thx again.

---

### Post by yancek on 2014-09-12
That output does not look good.  First you have windows code installed in the master boot record so your machine will be using the windows bootloader.  A default windows bootloader will not boot Linux.  There is some third party software which can or you could manually edit the windows boot files if you know how to do that.

The second problem is that the first partition on the drive is ntfs (windows) but you have your Ubuntu boot files there and you seem to be missing one or more windows boot files.  I'm not sure about that because I rarely boot windows, someone else should be able to tell you.

It looks like the Ubuntu system files are on sda2 and sda3 is a /home partition, either that or a data partition.  You have a separate BIOS boot partition on sda5 which isn't needed.  Not sure if that presents a problem. 

It also shows you are using GPT partitioning which I know very little about so hopefully, someone else will post.

---

### Post by oldfred on 2014-09-12
You can copy & paste directly from web page or any other source into terminal with the mouse. If using keyboard you have to use control shift v to paste.

You do not show a full install of Windows in the sda1 NTFS partition, but that would not boot from a gpt drive. Windows only boots from a gpt partitioned drive with UEFI. And only boots from MBR(msdos) with BIOS.
You Windows NTFS partition does have two of the three Windows boot files, so Ubuntu may tell you it is bootable, but you are missing /Windows/System32/winload.exewhich normally with Windows 7 is in main install and two boot files you have are just in a small boot partition.

You also show grub installed to the partition boot sector or PBR of sda1 NTFS partition. Grub normally is not installed to a PBR and never to a NTFS partition. Windows has to have its own info in a NTFS partition's boot sector. If just a data partition not sure if Linux NTFS driver still will work with it or not. Best to correct that if you have data in it.
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
# Instructions are here:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Boot-Repair should offer to install grub2's boot loader into the MBR of the drive. Instructions on installing Boot-Repair to your live installer are in link in post #2.

---

### Post by oussama3 on 2014-09-13
> **yancek said:**
> That output does not look good.  First you have windows code installed in the master boot record so your machine will be using the windows bootloader.  A default windows bootloader will not boot Linux.  There is some third party software which can or you could manually edit the windows boot files if you know how to do that.

The second problem is that the first partition on the drive is ntfs (windows) but you have your Ubuntu boot files there and you seem to be missing one or more windows boot files.  I'm not sure about that because I rarely boot windows, someone else should be able to tell you.

It looks like the Ubuntu system files are on sda2 and sda3 is a /home partition, either that or a data partition.  You have a separate BIOS boot partition on sda5 which isn't needed.  Not sure if that presents a problem. 

It also shows you are using GPT partitioning which I know very little about so hopefully, someone else will post.

thank you for your answer. 
I cant edit the boot files manually unfortunately. is the third party software TestDisk ?
the sperate bios boot partition is not originally suggested in the tutorial i was following but when i clicked next in the ubuntu installer it showed an alert saying that i must put one which is at least 1mb but gave me the option to ignore it.i choose to make the partition for it... so if you or anyone thinks that it might be presenting a problem i can remove it if i am instructed on how to do that.


so from what i understand the partitioning went wrong and now files got mixed up and some are missing which makes it not possible to boot from the hard disk. so if anyone has suggestions on how to fix it . that would be greatly appreciated.

i will be trying testdisk from Oldfred reply in a moment.

---

### Post by oussama3 on 2014-09-13
i read this

[http://www.cgsecurity.org/wiki/TestD...ector_recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery")

i followed [http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

but when i open software resources from the software center it didnt have universal repository but had "community-maintained and open source software (universe)" -see attachements- so i checked that and something started in the progress tab in the software center : (updating cashe querying software sources) -see attachements-  appearently it is using my internet which is not very fast. so i dont want to proceed from this until it is over.

in the first link the test disk download link is there [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

i downloaded it and extracted it then i double clicked testdisk_static -see attachements- but nothing happened.

so this updating cashe querying software sources is taking quite a while and im not sure it is necessary , maybe i could try the command in the terminal now ? from [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix) 
or [http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by oldfred on 2014-09-13
I have never downloaded testdisk directly, always from repository. And I rarely use Software Center as it has some idiosyncrasies. I use synaptic, and in that you can turn on added Ubuntu repositories if not already on, see settings tab.
sudo apt-get install synaptic
 
It is a lot easier to use repository. And that is a version that will work with Ubuntu. 
Direct download should work but you may have to use it or do extra configuration steps.

If your sda1 was just a large NTFS data partition and not your main install, you have overwritten your working Windows install. That will not be recoverable as a working system. If you also had vital unbacked up data in that deleted partition, STOP using system as every thing you do overwrites more data. You may be able to recover some of the files with programs like photorec in the repository or Windows tools. Ubuntu actually only overwrote part of existing data, so a drive scan type recovery tool can with lots of effort find files. It will not recover full file name as that is gone, but does find it by type or extension.

---

### Post by oussama3 on 2014-09-13
ok i will try getting synaptic but im not sure what it does. from then i will be able to get testdisk and boot repair because i have been trying to get those but everywhere is asked to put the command
 ```
sudo apt-get update
```
which seems to not work for some reason as it gives errors. so i was wondering if i can get the ubuntu version with pre installed boot repair. maybe running the recommanded repair would solve this.


I do not have any vital data and i only care about windows installation files. but I am surprised to hear that the live boot is eating my hard drive ?? i thought it only uses RAM ? 

and sda1 is not just a large NTFS data partition. at least it wasnt meant to be. it was supposed to be where the main windows install is. because during the partition i left it as "do not use this partition" and in the end it was ntfs with windows loader so it makes sense i guess.

also if windows 7 is overwritten why cant i boot to ubuntu ?

i really need to fix the terminal errors after typing ```
sudo apt-get update
``` because i have been unable to get neither disktest nor boot-repair. if u need the terminal error i will be posting that. I also need to know what is synaptic and what is it supposed to do.
thanks again for the help

---

### Post by oussama3 on 2014-09-13
hey i got the sudo apt-get update fixed and got the testdisk too so im happier but still sad. so should i follow the instructions in the links you provided or get boot-repair and run recommanded repair ?

---

### Post by oussama3 on 2014-09-13
i decided to follow the instructions of [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
in step 3 >> 6.

[LIST]
[*]then select the broken partition with [Boot], it will display something like : 
[/LIST]
 Boot sector
 Status: Bad

 Backup boot sector
 Status: OK

 Sectors are not identical.

 A valid NTFS Boot sector must be present in order to access
 any data; even if the partition is not bootable.

 [  List  ]  [Backup BS]  [Rebuild BS]  [  Dump  ]


this doesnt show up and what i get after clicking advanced is in the attachements, what's next ?

---

### Post by oldfred on 2014-09-13
Did you follow the procedure to restore the backup Boot Sector?

But I still do not know how you converted drive from MBR(msdos) to gpt. Was that somewhere in the original openclassrooms instructions you said you used to install?
Windows will not boot from a gpt drive even if it has all its boot files.
Did you have more NTFS partitions before installing Ubuntu?
Did you make good backups of all your data before installing?

---

### Post by oussama3 on 2014-09-13
the procedure to restore the backup boot sector ? if u mean the instructions on how to use testdisk then yes i did. after step 3 > 5 i didnt get step 3 > 6 but got the screen atached in the previous post

in the openclassrooms instructions there was nothing about MBR or gpt and therefore i have so little knowledge about what those terms mean.
are the boot files present in a gpt drive for sure ? and how to solve this ?
before installing ubuntu i had one and only partition sda1 for windows.

i did not have any personal data that i needed to save elsewhere and this was recommanded in the original instructions and from what i understood it was personal data that i needed to worry about not windows files.

i still dont understand why i got the attached screen in testdisk after selecting advanced. maybe it is a newer version of testdisk ?
and i dont understand why i cant boot to the installed ubuntu ? can i change legacy to UEFI and re install ubuntu . that worked for someone in a post in the internet i read earlier.

---

### Post by oldfred on 2014-09-13
You have to tab & enter on the [Backup BS] to have it copy the backup BS back to the real Boot sector. 

But you cannot boot Windows as long as drive is gpt. 
And Ubuntu would only convert you to gpt automatically is drive was over 2TiB, so I do not know how you converted drive. It is possible to convert back, but again good backups are required. Not sure if Windows is fixable or not. Sometime script does not show all the boot files so they may be there, but we cannot even test until Boot sector is fixed and we have converted back to MBR.

If you convert to MBR from gpt you will also have to reinstall grub. Boot-Repair can do that part for you, but not the conversion. You probably have to reinstall Boot-Repair each time you reboot as it is not saved in the live installer.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by oussama3 on 2014-09-14
> **oldfred said:**
> You have to tab & enter on the [Backup BS] to have it copy the backup BS back to the real Boot sector. 

But you cannot boot Windows as long as drive is gpt. 
And Ubuntu would only convert you to gpt automatically is drive was over 2TiB, so I do not know how you converted drive. It is possible to convert back, but again good backups are required. Not sure if Windows is fixable or not. Sometime script does not show all the boot files so they may be there, but we cannot even test until Boot sector is fixed and we have converted back to MBR.

If you convert to MBR from gpt you will also have to reinstall grub. Boot-Repair can do that part for you, but not the conversion. You probably have to reinstall Boot-Repair each time you reboot as it is not saved in the live installer.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

I dont get any Backup BS tab in testdisk see the attachements . I get only type or create image or quit and for some reason though it is in /dev/sda it shows one partition efi gpt only and i dont even recognize it.

i will be checking those links thank you.

---

### Post by oldfred on 2014-09-14
I do not get that screen on my gpt drives and what does type then show.

Perhaps you are into mixed MBR & gpt.
download and run fixparts, do not do the w for write until you post details. The w will may convert drive.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by oussama3 on 2014-09-15
thank you for your help guys especially you oldfred but i decided to try to reinstall ubuntu after switching legacy bios to uefi 
after i did that it did not detect windows as installed in the live ubuntu installer. so i really didnt care much about windows and i went for the standard installation of ubuntu (no manual partioning) and when i restarted the pc it was able to boot to the installed ubuntu from the hdd. after starting to getting used to ubuntu maybe its time to not look back at windows at all. perhaps i ll be trying to get windows later but right now i am happy with ubuntu.

maybe i should ve tried boot repair first or testdisk or gdisk and used them correctly before reinstalling but I was a bit impatient. 

anyway thanks again. I ll be sure to come back here in case of any questions or problems with ubuntu.

---

