---
title: "Trying to install Ubuntu from flash drive"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by Morten_Fjellheim on 2015-01-21
I have downloaded the iso file to my pc, sendt it to the usb stick and set my pc to boot from the spesific flash stick. After reboot i get a message saying "Reboot and select proper Boot device or insert boot media in selected boot device and press a key" 

I have been following this guide on how to install from a flash drive "    [https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Ubuntu)   "

It says something about creating a bootable usb flash drive, is that what i have missed? I simply copied the iso file onto the usb stick. 

Another question, is it not posible to execute the setup file in the iso file on the pc. and start the installation that way?

And finally, is it posible to delete your own threads?

---

### Post by oldfred on 2015-01-21
You have to use an installer that both extracts ISO and creates a bootable DVD or flash drive.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

      
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

---

### Post by sudodus on 2015-01-22
> **Morten_Fjellheim said:**
> I have downloaded the iso file to my pc, sendt it to the usb stick and set my pc to boot from the spesific flash stick. After reboot i get a message saying "Reboot and select proper Boot device or insert boot media in selected boot device and press a key" 

I have been following this guide on how to install from a flash drive "    [https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Ubuntu](https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_a_bootable_Ubuntu_USB_flash_drive_from_Ubuntu)   "

It says something about creating a bootable usb flash drive, is that what i have missed? I simply copied the iso file onto the usb stick. 
You must use one of the ***tools*** described in that link. You cannot simply copy the file to the USB stick.

Unetbootin is one tool, that works in Windows. Win32 Disk Imager is another tool.
> 

Another question, is it not posible to execute the setup file in the iso file on the pc. and start the installation that way?

Are you thinking of wubi.exe?

It might be possible to use for testing, but it is no longer recommended. See this link

                          [Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")                 

> 
And finally, is it posible to delete your own threads?

We only delete threads that violate the Ubuntu Forum's code of conduct. What thread do you want to delete and why?

---

### Post by Morten_Fjellheim on 2015-01-22
I am trying to install Ubuntu but it fails. I get a message saying someting like "No rootfile system is applied, correct this in the partitionmenu" (Translated from norwegian) This confuses me as the partition menu already states it is NTFS. So i set it to fat32 but i get the same message. I try to change the partitionmenu but after pressing new partitionlabel (also translated from norwegian) the machine starts loading but after 6-7 seconds it stops and nothing has happend. I have had a few suggestions like making new partition but it has already failed so i am stuck.

---

### Post by sudodus on 2015-01-22
Merged threads:

Please continue searching for help in your previous threads instead of creating new threads!

As long as you have the same problme or very related problems, it makes it easier for helpers to know the history: what you have already tried, what is the computer specs and the version of Ubuntu etc). With several threads, the effort is diluted and inefficient.

-o-

On the other hand, when your efforts to install have succeeded, and you have problems with some tasks in the installed system, it is time to create new threads about those problems and tasks.

---

### Post by sudodus on 2015-01-22
> **Morten_Fjellheim said:**
> I am trying to install Ubuntu but it fails. I get a message saying someting like "No rootfile system is applied, correct this in the partitionmenu" (Translated from norwegian) This confuses me as the partition menu already states it is NTFS. So i set it to fat32 but i get the same message. I try to change the partitionmenu but after pressing new partitionlabel (also translated from norwegian) the machine starts loading but after 6-7 seconds it stops and nothing has happend. I have had a few suggestions like making new partition but it has already failed so i am stuck.

There are several steps, where things can go wrong. Please describe with as much detail as possible. That will make it easier to help. Otherwise we can only guess.

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Please tell us which version of Ubuntu you try to install, write the name of the iso file (for example: ubuntu-14.04.1-desktop-amd64.iso)

3. Please tell us which tool you used to make the USB boot drive

4. Can you get a live session: Does it work to boot from the USB boot drive and select 'Try Ubuntu'?

5. Are there problems during the installation? In that case, describe what you did and where it stops.

6. Are there problems after the installation (with the installed system)? In that case, describe what you did and where it stops.

---

### Post by Morten_Fjellheim on 2015-01-22
Ok, sorry for making to many threads i will use only this one in the fututre. I will gather the information you have asked for and come back to it later today i need to ask a question first. Wifi card, are we talking about hardware for wireless internet connection, for the wifi function that alot of smartphones uses, just for computers instead?

---

### Post by sudodus on 2015-01-22
I mean the hardware for wireless LAN (as opposed to ethernet or wired LAN). You probably have it in a laptop but maybe not in a desktop.

---

### Post by Morten_Fjellheim on 2015-01-22
[SIZE=5]Alright, here is the specs asked for:  [/SIZE][COLOR=#444444][FONT=Arial][SIZE=5] Intel Core&#8482; i5 Quad Processor i5-750[/SIZE]
[/FONT][/COLOR]                                                  [COLOR=#444444][FONT=Arial] Kingston DDR3 1333MHz 4GB KIT CL9
[/FONT][/COLOR]                                                  [COLOR=#444444][FONT=Arial] Sapphire Radeon HD5830 1GB GDDR5 PCI-E
And no, i dont have a wifi card.
[/FONT][/COLOR]
The pc is a gamer pc built by "komplett" in Norway. Since its put together by random pieces it doesn not have a brand. 
Here is a link if a closer look is needed   [https://www.komplett.no/product/610227](https://www.komplett.no/product/610227)  . It will take you to a norwegian site, the specs are in english so it should be easy to understand.
I bought the machine without an OS, i am now running windows 7 home premium with servicepack 1.

Ubuntu version is ubuntu-14.10.1-desktop-amd64.iso.
I used linux live usb creator to make the usb boot drive. And yes, it boots from the usb drive and i have already use the try linux option which works perfectly.

I have not been sucessfull in finding a guide for 14.10 so i have used a guide for 14.04 instead, it doesnt matter because up to the point where you get try ubuntu or install ubuntu, the procedure for both are the same.
So now we have booted from the usb drive and are looking at the screen where you can install or try ubuntu, it is the picture under part 1 in this guide    [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop).
I press "install ubuntu" and the picture in part 2 appears, the diference is that i dont get the message saying i have a power core connected. I continue and get the installation type panel. There is four options. One is to erase the hardisk and install ubuntu, it has two more options you can choose but since i am gona use the other option called something else those do not apply. So i press the somethihng else option and gets a list of partitions on the hardisk. The hardisk has two partitions slash dva slash sda 1 and 2. I think number 1 is a small partition where windows is installed, number 2 is the rest of the harddsik.  I wana use the one that says slash dva slash sda 2 but it is only in the list of partitions, and not in the box where you choose the partition to install on. I asume its because the slash dva slash sda is the default and choosing this will install on number two since number one is windows files only.
In the list of partitions i highlighit number 2 and press change, i choose ntfs filesystem and no mount, neither do i tick the format option. In the install option box i choose the slash dva slash sda. With these parameters what hapends when i press install is that a popup with this message appear.....no root file is defined..please correct this form the partitioning menu...
I have tried with fat 32 filesystem and diferent mounts, i also tried to choose the erasing option but everytime the same message pops up. So i am stuck at that point.

I have made this as detailed as posible but if you need more info please ask.

---

### Post by sudodus on 2015-01-22
Thanks for the detailed description! It will make it easier for me and ***also other people*** to understand what might be the problem and to suggest what to do :-)

> **Morten_Fjellheim said:**
> [SIZE=3]Alright, here is the specs asked for:  [/SIZE][COLOR=#444444][FONT=Arial][SIZE=3] Intel Core&#8482; i5 Quad Processor i5-750[/SIZE]
[/FONT][/COLOR]                                                  [COLOR=#444444][FONT=Arial] Kingston DDR3 1333MHz 4GB KIT CL9
[/FONT][/COLOR]                                                  [COLOR=#444444][FONT=Arial] Sapphire Radeon HD5830 1GB GDDR5 PCI-E
And no, i dont have a wifi card.
[/FONT][/COLOR]
The pc is a gamer pc built by "komplett" in Norway. Since its put together by random pieces it doesn not have a brand. 
Here is a link if a closer look is needed   [https://www.komplett.no/product/610227](https://www.komplett.no/product/610227)  . It will take you to a norwegian site, the specs are in english so it should be easy to understand.
I bought the machine without an OS, i am now running windows 7 home premium with servicepack 1.

Ubuntu version is ubuntu-14.10.1-desktop-amd64.iso.

Is the iso file

**ubuntu-14.04.1-desktop-amd64.iso** (the LTS version supported until April 2019)  <--- recommended unless your hardware is too new for it

or
[B]
ubuntu-14.10-desktop-amd64.iso[/B] (a 9-month support version with end of life in July 2015)? <--- recommended for very new hardware because it has a newer kernel and newer drivers.
> 
I used linux live usb creator to make the usb boot drive. And yes, it boots from the usb drive and i have already use the try linux option which works perfectly.

I have not been sucessfull in finding a guide for 14.10 so i have used a guide for 14.04 instead, it doesnt matter because up to the point where you get try ubuntu or install ubuntu, the procedure for both are the same.
So now we have booted from the usb drive and are looking at the screen where you can install or try ubuntu, it is the picture under part 1 in this guide    [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop).
I press "install ubuntu" and the picture in part 2 appears, the diference is that i dont get the message saying i have a power core connected. I continue and get the installation type panel. There is four options. One is to erase the hardisk and install ubuntu, it has two more options you can choose but since i am gona use the other option called something else those do not apply. So i press the somethihng else option and gets a list of partitions on the hardisk. The hardisk has two partitions slash dva slash sda 1 and 2. I think number 1 is a small partition where windows is installed, number 2 is the rest of the harddsik.  I wana use the one that says slash dva slash sda 2 but it is only in the list of partitions, and not in the box where you choose the partition to install on. I asume its because the slash dva slash sda is the default and choosing this will install on number two since number one is windows files only.
In the list of partitions i highlighit number 2 and press change, i choose ntfs filesystem and no mount, neither do i tick the format option. In the install option box i choose the slash dva slash sda. With these parameters what hapends when i press install is that a popup with this message appear.....no root file is defined..please correct this form the partitioning menu...
I have tried with fat 32 filesystem and diferent mounts, i also tried to choose the erasing option but everytime the same message pops up. So i am stuck at that point.

I have made this as detailed as posible but if you need more info please ask.

Do you want to dual boot with Windows? In that case you should boot into Windows and shrink the main Windows partition. Reboot twice.

Then boot into the Ubuntu install drive 'Try Ubuntu' and use ***gparted*** to create one partition with the ***ext4*** file system for the root file system '/' and a small swap partition. If you intend to hibernate you need as much swap as RAM (in Gibibytes), so 4 or slightly more. If you do not intend to hibernate, it is probably enough wiht 2 GB swap (a swap partition).

After that you start the installer and select ***Something else*** at the partitioning screen ...

If you want to replace Windows, you can use almost the whole big Windows partition for Ubuntu, but you must change from NTFS or FAT32 to a linux file system, and I recommend ***ext4***, but reserve some space for that small swap partition described earlier.

---

### Post by sudodus on 2015-01-22
Please run the following command and paste the output to a reply. 'Go advanced' and put it within [noparse]```
some text ...
```[/noparse] tags (mark and use the # icon above the advanced editing window)

```
sudo parted -l
```

... space minus ell

---

### Post by Morten_Fjellheim on 2015-01-22
I will need a more detailed description on how to perform that command thing......how to do it and with windows or linux open_

---

### Post by sudodus on 2015-01-22
Run it when booted live from the Ubuntu pendrive.

Open a terminal window with ***ctrl + alt + t***

type in the text and launch the command with the Enter key.

---

### Post by Morten_Fjellheim on 2015-01-22
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdb: 8017MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      12.3kB  8017MB  8017MB  primary  fat32        lba


Model: Imation Nano Pro (scsi)
Disk /dev/sdd: 3876MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  3876MB  3872MB  primary  fat32        lba


Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sde: 8036MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      2097kB  8030MB  8028MB  primary  fat32


Model: TDK LoR TF10 (scsi)
Disk /dev/sdf: 7744MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  7744MB  7740MB  primary  fat32        lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4282MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  4282MB  4282MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 496GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  496GB  496GB  ext4


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdg: 8017MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      12.3kB  8017MB  8017MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: ATAPI iHAS124 B (scsi)                                             
Disk /dev/sr0: 3119MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                  
Disk /dev/sr1: 101MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

ubuntu@ubuntu:~$ 
```



Not sure if this is correct but here it is anyway.

---

### Post by oldfred on 2015-01-22
Posted twice?
And please use code tags or the # in advanced editor for longer text or terminal output.

You installed with full drive LVM or LVM with encryption. Is that what you really wanted. It is a bit more advanced as LVM is another type of partitioning.

---

### Post by Morten_Fjellheim on 2015-01-22
I am not sure how to use the codes or the # thing, are saying i have to put it infront and behind the command in the terminal or is it something else. And something eelse, since trying ubuntu doesnt include norwegian keyboard setup i can not find the signs you have before and after code. And where is the advanced editing window. I have only that terminal you told me how to open.

---

### Post by sudodus on 2015-01-22
+1 to oldfred's comment and observation.

I also found the LVM partitions in the internal drive /dev/sda

Edit: [I think I misunderstood the output from parted, so I wiped part of this post]

Did you create the LVM partitioning with Ubuntu?

Anyway, there is no Windows in the internal drive.

If you want Ubuntu, the easiest way is to do it the standard way, to let it install using the whole internal drive /dev/sda without encryption, at least for the first attempt. Would that be OK?

---

### Post by Morten_Fjellheim on 2015-01-22
Number  Start   End     Size    Type     File system  Flags
 1      12.3kB  8017MB  8017MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: ATAPI iHAS124 B (scsi)                                             
Disk /dev/sr0: 3119MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                  
Disk /dev/sr1: 101MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ [/CODE]


Is this what you meant

Anyway, i had planned to Dual boot however right now i will try to install the way you proposed. If it works i will leave it with that, if not i will be continuing seeking asitsance.

---

### Post by sudodus on 2015-01-22
No I think I was misunderstanding some of the ***LVM output*** from parted.

/dev/sr0 and /dev/sd1 are optical drives or emulated optical drives (CD/DVD or I think in this case a dedicated part of the U3 pendrive).

Now, please, tell us what you want! Is it OK with an Ubuntu only system, or do you want some kind of dual boot system with Window or some other linux distro?

---

### Post by Morten_Fjellheim on 2015-01-22
Windows has been erased, i was hoping choosing the erase window and install ubuntu option would work better. So from now on i will focus on installing ubuntu as the only OS on the machine. I will try dual booting another time when i have learned more about it os lets focus on installing ubuntu only

I asume after installation when the system asks for restart, i will have to set to boot  from hardisk instead of lash drive?

---

### Post by sudodus on 2015-01-22
That sounds like a good idea. Try it the easy way now, get to know Ubuntu, and next time you can do something more advanced :-)

I will log out for tonight soon, but I'll be back. Maybe you have already succeeded tomorrow, with help from people in other time zones or with other night habits, maybe there is still something where I can help you ...

---

### Post by Morten_Fjellheim on 2015-01-22
It seems like the system is properly installed now, installation went smooth and ubuntu started after reboot.

---

### Post by sudodus on 2015-01-22
Congratulations :KS

Now do some testing, and if things run smoothly, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

Remember to back up your system or at least your personal files: make a routine to take regular backups.

Then go on to explore Ubuntu and when necessary start new threads to get help :-)

---

