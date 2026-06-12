---
title: "Ubuntu 64bit installer doesnt detect windows 8.1 64bit"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by saeed11 on 2015-03-18
Hello friends
I need to install ubuntu 14.04 64bit alongside my windows 8.1 64bit, but the installer doesnt detect my windows and when i choose "something else" it shows my whole hard drive space.

searched alot, havent succeeded. 

I have Asus n46vz and my default OS was win7 64bit.

Thank you in advance.

---

### Post by Bucky Ball on 2015-03-18
Welcome. You need to switch off faststart/fastboot (don't know what it's called, exactly) in Windows. [This]("http://www.pcmag.com/article2/0,2817,2417361,00.asp") might help. You also need to go into the BIOS and check there is no fastboot for Win there. Rarely use Win so sorry I can't be more specific, but suspect this is your issue. 

With it switched on, Windows is basically hibernating so it won't be seen by your installer (it's hiding in the bushes!). Good luck.

* Just had a quick sniff round and 'secure boot' in the BIOS is what you're looking to switch off. If a pre-installed Win8 it will be in UEFI mode. This means you MUST install Ubuntu in UEFI also. Make sure you have the install device set to boot this way in BIOS also.

---

### Post by LostFarmer on 2015-03-18
Open a terminal in the live linux and post the output of
```
sudo parted -l
``` -l is a small L .  It will tell us if it is MBR or GPT partitioning and if it was GPT and now incorrectly change to MBR.

---

### Post by fantab on 2015-03-19
> the installer doesnt detect my windows and when i choose "something else" it shows my whole hard drive space.
There are a few reasons why the above happens:
1. Switch off Hibernation (if you use it) and shutdown Windows properly. In Windows 8+ this is called [FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")... disable it.
2. There could be filesystem errors on the HDD - Run [Chkdsk]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") to correct the errors.
3. If there is NO Linux compatible filesystem on the HDD... you should at least have 10Gb 'Unallocated space' on the HDD.

If third, then it will be a good idea to see the output of :
```
sudo parted -l
```

Moreover, it is strongly suggested that you go through the following URLs before you install Ubuntu:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[URL="http://ubuntuforums.org/showthread.php?t=2147295"]http://ubuntuforums.org/showthread.php?t=2147295
[/URL]

---

### Post by saeed11 on 2015-03-19
Dear Bucky Ball

I switched off fast start-up, yes it was necessary to switch it off but still didn't help.

about the UEFI: I didn't have UEFI, think that's because I had win 7 pre-installed on my laptop.

Thank you

---

### Post by saeed11 on 2015-03-19
[SIZE=4][FONT=arial]Dear LostFarmer and Fantab[/FONT][/SIZE]

[SIZE=3][FONT=arial]I typed "[/FONT][COLOR=#000000][FONT=arial]sudo parted -l", the result is in the attachments,[/FONT][/COLOR][COLOR=#000000][FONT=arial]ubuntu_1.jpg.

[/FONT][/COLOR][COLOR=#000000][FONT=arial]it asks a question so one time i typed "y" and the result is [/FONT][/COLOR][COLOR=#000000][FONT=arial]ubuntu_2.jpg[/FONT][/COLOR][COLOR=#000000]

[FONT=arial]and the other time I typed "n" and the result is [/FONT][/COLOR][COLOR=#000000][FONT=arial]ubuntu_3.jpg[/FONT]

[FONT=arial]PS: I'm installing Ubuntu from my flash memory.[/FONT]

[FONT=arial]------------------------------------------------------------------[/FONT]
[FONT=arial]I ran check disk from properties of drive.[/FONT]
[FONT=arial]checked all my drives including windows 8.1 drive (C), the drive I want Ubuntu (D) installed in, my other two drives and eventually my flash memory which contains the Ubuntu installation. There are no errors.[/FONT][/COLOR][/SIZE]

---

### Post by LostFarmer on 2015-03-19
"parted -l" does not indicate any partitions.  Can you still boot into Windows ?  I suspect not. But if you can, go to disk management and post a screen shot.

---

### Post by saeed11 on 2015-03-19
Dear LostFarmer

I can log in to windows, I created 200GB of unallocated space, but the installer didn't detect my windows.
here is the screen shot

---

### Post by fantab on 2015-03-19
If you don't have Uefi and Windows 8 is installed in MBR/Legacy mode then you probably also don't have GPT... I think your HDD partition table is corrupt...
In your 'parted -l' output you see the warning.
This can be easily fixed with '[fixparts]("http://www.rodsbooks.com/fixparts/")'... its a simple utility should be present by default on Ubuntu Live. If it is not then it can be installed with package 'gdisk'.
```
sudo apt-get install gdisk
```

Another important thing:
You already have 4 Primary partitions on the HDD... and you've left 200gb unallocated space, however MBR or 'msdos' partition scheme only allows 4 Primary Partitions.
To install Ubuntu you will need to delete one of your existing partitions then Using Gparted from Ubuntu you must make an Extended Parittion to overcome the only 4 Primary Parittions limit...

---

### Post by LostFarmer on 2015-03-19
I agree with running 'fixparts', that will correctly remove left over GPT header data.  My understanding the program will automaticly remove the GPT left over GPT header, just run the program and quit.

'fantab' did make a error when looking at your hdd partitions, 2 of your NTFS partitions are logical.

I did learn something, I figured when running 'parted -l' and said No to GPT it would display the MBR partitions.

---

### Post by saeed11 on 2015-03-20
Dear LostFarmer and fantab
when I said no to "parted -l" it showed my flash memory containing the Ubuntu installation.

I am reading through the pages you suggested, and Im not much of a professional on these topics :p
right now im gonna run the fixparts on the live linux and then deal with the thing fantab said:

"[COLOR=#000000]Another important thing:[/COLOR]
[COLOR=#000000]You already have 4 Primary partitions on the HDD... and you've left 200gb unallocated space, however MBR or 'msdos' partition scheme only allows 4 Primary Partitions.[/COLOR]
[COLOR=#000000]To install Ubuntu you will need to delete one of your existing partitions then Using Gparted from Ubuntu you must make an Extended Parittion to overcome the only 4 Primary Parittions limit...[/COLOR]"

---

### Post by saeed11 on 2015-03-20
I executed "fixparts" in live Ubuntu. The result is attached (new doc 4_3).It says the directory doesn't exist, however when I was checking if it exists, I saw my other partitions ,except the unallocated 200GB one, in the explorer(new doc 4_1). I dont know if they were there before I executed "fixparts":(

hmm but the installer still doesnt detect my windows and in "something else" shows my whole hard disk space.

---

### Post by Mark Phelps on 2015-03-20
Your Disk Management screenshot shows "I:", presumably a partition your created for Ubuntu.  Get rid of that!  Ubuntu will not install in a Windows filesystem partition and Disk Management can NOT create Linux filesystem partitions.

Instead, what you need is Unallocated space on the drive, which you then format using the Ubuntu installer.

---

### Post by saeed11 on 2015-03-20
Dear Mark Phelps
That "I:" is my flash memory that contains Ubuntu installation. I made it bootable using "rufus". An application for installing OSs with flash memories.

---

### Post by LostFarmer on 2015-03-20
Your internal hdd is sda as per parted -l, so the correct command is 'fixparts /dev/sda' not /dev/sdc.

---

### Post by saeed11 on 2015-03-21
Dear LostFarmer

I will run the command but before that lets check on this attachment I put here.
I made my live Ubuntu using "rufus". in the "partition scheme and target system type" there are 3 alternatives:
"MBR partition scheme for BIOS or UEFI computers
MBR partition scheme for UEFI computers
GPT partition scheme for UEFI computers
"
 which one should I choose?Have they caused these problems??

I will run the right command as you said, after making my live Ubuntu again.

---

### Post by Ko_Char on 2015-03-21
You need *sudo* when you run fixparts. 

```
sudo fixparts /dev/sda
```

---

### Post by LostFarmer on 2015-03-21
Your current Win8 is in MBR mode.  The diskmanagment you posted does not have the needed fat32-EFI partition for GPT.  So linux needs to be booted and install also in MBR mode. Have never used RUFUS to make a linux boot usb , but would say select "MBR partition scheme for BIOS or UEFI computers".  Just to be sure linux usb is booted in MBR mode run  
```
ls /sys/firmware
```  You do NOT want to see "efi" as one of the items listed.  If you see 'EFI' , you have booted into GPT/EFI mode not MBR mode.

On my EFI boot, you do NOT want:```
[dad:/home/dad] $ ls /sys/firmware
acpi  [COLOR=#ff0000]efi[/COLOR]  memmap
```

---

### Post by fantab on 2015-03-22
> **saeed11 said:**
> I executed "fixparts" in live Ubuntu. The result is attached (new doc 4_3).It says the directory doesn't exist, however when I was checking if it exists, I saw my other partitions ,except the unallocated 200GB one, in the explorer(new doc 4_1). I dont know if they were there before I executed "fixparts":(
You have entered a wrong disk id with fixparts, your drive or disk is /dev/sda and NOT /dev/sdc... 
> **LostFarmer said:**
> Your internal hdd is sda as per parted -l, so the correct command is '**fixparts /dev/sda**' not /dev/sdc.

Also use a simple write tool in Windows like [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager") or [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Unless your partition is fixed, you will have problems installing, no matter where and how you burn the iso to usb.
Read the fixparts tutorial I have linked in my earlier post and run it safely.

---

### Post by saeed11 on 2015-03-22
[FONT=Arial][COLOR=#222222]Helodear LostFarmer, fantab and every one who helped me

Finally I succeeded! 
Here is a brief of what I did from the first moment till now, Just to be a tutorial for myself:

1. my diskwas dynamic, deleted my whole partitions and changed it to Basic.

2.Switched off fast start up in my windows 8 (type "po bu" instart and go to "power buttons" section)

3.[/COLOR]Ityped "[COLOR=#000000]sudoparted -l", the result is in the attachments,ubuntu_1.jpg.
[/COLOR][COLOR=#222222]wefound that my partition table is GPT table but is somehow corrupted as mentioned in the terminal window.
[/COLOR][COLOR=#000000]itasks a question so one time i typed "y" and the resultis ubuntu_2.jpg

and the other time I typed "n"and the result is ubuntu_3.jpg (when I said no to "parted-l" it showed my flash memory containing the Ubuntuinstallation.)

[/COLOR][COLOR=#222222]4.Soto correct my partitio table I ran the command "[/COLOR][COLOR=#000000]sudofixparts /dev/sda[/COLOR][COLOR=#222222]".Unfortunately I dont have the image but thinks I typed "y"ond it corrected my partition table and the i typed "?" tosee the commands available and then typed "w" to write thechanges to my disk and save the changes.

5.i booted my flashusing rufus and restarted my pc and entered the non uefi installationand it recognized my other partiotions.(Booting in UEFI mode resultedin the installation to not detect my windows, but it still detectedmy partitions)

6.I installed ubuntu and partitioned it usingthis help

I wrote these in a hury, might have missed things,will correct it again!!

Thank you![/COLOR][/FONT]

---

### Post by saeed11 on 2015-03-22
I would like to thank you for your helps.
I really didnt think I would succeed but I did. Been dealing with it couple of weeks and couldnt overcome it without your helps ;)

I learned alot from you about partiotioning, partition table ...

Thanks alot my friends :)

---

