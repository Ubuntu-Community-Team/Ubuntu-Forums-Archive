---
title: "Installation on UEFI"
date: 2013-08-17
forum: Installation &amp; Upgrades
---

### Post by grimm2 on 2013-08-17
I have been trying for 2 days to install ubuntu 13.04 next to windows 7 on this computer . Im not that tech-savy , and a totaal linux noob . Ive had a huge amount of help on the IRC but there also we seem to got stuck so i thought to ask it here . 
[U]
This pc is fairly new , specs are:[/U]
MOBO: Asrock 880gmh/u3s3
AMD FX8120 -8core 3,1ghz
8gig Ram DDR3 
Amd Radeon HD 6800 series graphics card 

**Important : my dvd drive is broken** , so i do everything with bootable USB drives , i used unetbootin to 'burn' the iso. images to USB .

I got one 120gig SSD drive , and a secondary 1TB (sata 2 i think) drive .

So first i clean formatted everything , installed windows (NTFS) on the SSD as i will still be using windows mainly for games , and sometimes for other more heavy applications if i cant find a way to get it working under Ubuntu. 

_The 1TB drive is partitioned as following :_
60gig for Ubuntu (ext4 , mount point / ) 
675gig for all data (NTFS so i could access it with both OS?) 
195gig for what i call 'input' , NTFS , so internet downloads , torrents , everything that comes into the pc (in the idea to reduce infection risk if something goes wrong)

First i had some issues with the graphics card (flashing purple white screens)  ,and after some IRC rescue help , i figured out where to put the nomodeset to get that working already. 

Went into the install menu of Ubuntu , choose 'something else' . 

**There i made / it was following setup : **
/dev/sda
     /dev/sda1 = NTFS 104mb windows 7 (loader) 
     /dev/sda2 = didn't say anything but i assume here is Windows installed 

/dev/sdb
      /dev/sdb5 = swap (4gig , i didn't do this at first , but i got the warning when clicking continue . I dont know if its necessary , but i dont mind sacrificing 4gig to be sure)
      /dev/sdb6 = ext4 Ubuntu 13.04 
      /dev/sdb3 = the data disk NTFS
      /dev/sdb4 = the input disk , also NTFS 

Boot loader was saying /dev/sda , nothing more. 

So continued the installation , also entered my wifi password (got a wireless network card in this desktop) , let it run and download some extra packages. Ok. 
When it was ready , it asked me to reboot - yes - and then i got these really trip blue vertical lines on a black background , with 4 small redish squares on it . 
It seemed to be stuck there so ive done a hard shutdown . 

Changed the boot priorities back to my hard drive , and there i noticed the first strange thing , the bios (or UEFI) didn't seem to list my secondary HD in the boot priority menu , but i was visible in another boot priority sub menu (dont know anymore what it was called , can check it after i write this) . There i could switch it with the SSD drive , and then the secondary hard drive would show up in the boot priority menu , but then the SSD wouldn't.. still very confused about this , as in the past it showed up all devices it could boot from.. I can make a photo / video from it with my phone if needed. 

Anyway , no matter how i put these settings unless it was the USB drive as first boot option , it would go straight to windows , no asking wich OS i want to start. 
On recommendations in the IRC , ive re-done the install process (same way) , again got those strange blue lines at the end , but now they disappeard in 1 second and the pc rebooted . Again changed boot priority to hard drive , nope straight to windows . Also tried putting the 2th hard-drive where ubuntu is installed as first boot option (like i explained in the previous paragraph) , but no choice , straight into windows.  

Only at this point i thought about mentioning the UEFI setup bios thingie in the IRC :rolleyes:, and they told me that probably the issue is in there , and they didnt know how to deal with this. 

So thats where i end up here . :lol:

What options do i still got ? 
I finally , after years of doubting it , decided that i want to give ubuntu a shot , and its probably worth it i believe that , but i have to get it running first ofcourse ](*,)

---

### Post by oldfred on 2013-08-17
You do not mention efi partitions, so you probably have installed both systems with CSM/BIOS/Legacy mode that new UEFI motherboards have to be like the old BIOS.

Download the full ISO or install into your Ubuntu installer and post the link to the BootInfo report. It may offer to install grub autoamatically to all drives, but I prefer to manually install Windows to Windows drive and grub to Ubuntu drive. You can uncheck the auto fix but then check fix MBR and then in the advanced options choose.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by garryhughes on 2013-08-17
I do have an efi partition on the SSD, 99mb. Does this change how I must install Ubuntu?

I've created a 50GB partition on my 3TB drive (GPT disc) to house Ubuntu, but I want to be sure of the install procedure for my set up before I go for the install.

Thanks.

---

### Post by oldfred on 2013-08-17
If Windows is in UEFI mode, then you need to have Ubuntu in UEFI mode to easily dual boot. I would create an efi partition on the 3TB drive even if the installer puts the boot files in the SSD's efi partition. Then  you could copy files to efi on 3TB drive and boot from it if you every have issues with SSD.

More info on dual boot two drives in link in my Signature.

You will know if you boot Ubuntu in UEFI mode if you get grub. If you get purple screen with tiny icons at bottom, you are booting in BIOS mode. How you boot installer is how it installs.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by grimm2 on 2013-08-18
Thanks for the tutorial(s) , i will read myself into it and see if i think i can handle such procedures . 

Is this an issue as these computers are 'too new' ?
Its kinda 'putting me off' to install Linux seeing how complicated it is on this machine , not saying thats anyones fault or something. 

If you aren't super tech savy  ,or enthusiastic to spend entire nights learning , trying , failing , trying again , more learning and trying , you tend to go for the easy solution , especially if other people also depend on your computer for work/school and you don't want to screw them over by rendering the machine (temporary) unusable.

Next to that i am slightly concerned such procedures could damage my hardware , but i guess thats more paranoia as something else (somehow , the DVD drive did break between the clean format install of windows and ubuntu, could been the windows disc aswell that messed it up , but thats the last i have done with it , doesn't help with the hardware paranoia lol..)

Do you think that in the near future there would be come a more ''dumb user friendly UEFI method'' to install ubuntu ? 
Are the procedures you posted to get it running achievable for someone who's tech skills extend to fixing fomats , following internet guided registry fixes, writing some basic codes with internet tutorials to for example create own shutdown timer buttons etc ? Or do you need little higher pro skills for that ? 

In computer tech world , i feel somewhere between a general practitioner and a dentist , but not nearly as close as a surgeon ..

---

### Post by oldfred on 2013-08-18
Some users have posted that with their version of Windows 8 and UEFI that just installing worked. Some with secure boot on and others with it off.

But many vendors modify system or UEFI and seem to make it more difficult. And Ultrabooks use additional features that make it more difficult (RAID & dual video). And many vendors do not release internal workings of there chips or board and make it very difficult to reverse engineer drivers. Some like nVidia and AMD then release proprietary drivers that work but maybe not as good as the Windows version.

---

