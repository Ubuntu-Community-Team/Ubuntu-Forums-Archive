---
title: "Clean install without GRUB messing with win7"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by loseby on 2013-05-25
I have Ubuntu as a dual boot that uses GRUB on a different machine. Now I want to put the latest version on this PC but I dont want to use GRUB or anything else , would rather use the F12 key and let Gigabyte bring  up boot options. When I install Ubuntu I dont want it to put its boot manager on any other drives or even list windows etc etc. I want it a pure and simple solo drive which I will encrypt and use for all my financial transactions. It will be an OCZ 120GB SSD by itself

I guess one way would be to remove all other drives and just leave the OCZ attached but with my layout it is hard...... the crossfire GPUs ( long ones ) cover the sata connectors on the motherboard and the computer is high and heavy and I would have to move it and detach all cables to get to the back ( for the sata connectors on the HDD's ) but thats a last resort. 


edit: a different question. What version of 13.04 should I get? I use 64 bit win7 version as I have 16GB memory but I want stability from Ubuntu 13.04

---

### Post by fantab on 2013-05-26
> **losbey said:**
> ...I want to put the latest version on this PC but I dont want to use GRUB or anything else , would rather use the F12 key and let Gigabyte bring  up boot options. When I install Ubuntu I dont want it to put its boot manager on any other drives or even list windows etc etc. I want it a pure and simple solo drive which I will encrypt and use for all my financial transactions. It will be an OCZ 120GB SSD by itself ...

edit: a different question. What version of 13.04 should I get? I use 64 bit win7 version as I have 16GB memory but I want stability from Ubuntu 13.04

I dont think it is possible to NOT have a boot-loader and boot any OS. What makes you believe that with GRUB you will not have a "pure and simple solo drive"? What is your REAL worry?

If you want 'stability from Ubuntu', 12.04 is your best bet. If your machince supports 64bit then 64bit it is.

---

### Post by loseby on 2013-05-26
> **fantab said:**
> I dont think it is possible to NOT have a boot-loader and boot any OS. What makes you believe that with GRUB you will not have a "pure and simple solo drive"? What is your REAL worry?.


well I dont want Ubuntu putting anything on the Windows hard drive or other drives  I guess its ok if it just goes on the OCZ SSD but I want to be sure it doesnt go on my main Windows hard drive. Basically this is a gaming machine and I like a fast boot into Windows and not having to go through GRUB 

its a uefi firmware interface ( and I hate it with a passion but thats another story ) and just reading this [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI") gives me palpations


> Case when Ubuntu must be installed in EFI mode
Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: 

if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.

I would assume I installed win7 in EFI mode but how do you know ? 


> **fantab said:**
> 

If you want 'stability from Ubuntu', 12.04 is your best bet. If your machince supports 64bit then 64bit it is.

have 12.04 but I want to play with 13.04 , over time the other PC will be going to the dump but thats end of the year



I guess what I want to know is what happens when you install Ubuntu on a seperate drive in a dual boot system. Where does it write GRUB ? Does it put anything on the Windows drive or to be precise its MBR ?

---

### Post by fantab on 2013-05-26
You can look at your partitions for a 100-300MB First partition, most probably FAT32 with a boot flag, that is your 'efi' partition. Or post the output of:
```
sudo parted -l
``` 

from the Ubuntu Live DVD/USB... that should tell us if its UEFI.

It is recommended that you install GRUB on the same HDD/SSD, on which you have your Ubuntu installed. If you want to install grub to SSD then it should make sense to have your Ubuntu install on SSD. To control your Ubuntu install you have go manual way rather than doing an automatic installs. Its that simple.

Now, what exactly you mean by, "fast boot into Windows and not having to go through GRUB"? If you are assuming that with GRUB you will be delayed in booting Windows then you are wrong. Grub only does what Windows Boot-loader would do. There is no time lost. Since you want to dual boot you will have MENU to choose which one you want to boot. Even if you try to dual boot two windows with Windows boot loader it too will give you that choice.  

If you want us to help you install Ubuntu without disturbing your Windows install in anyway then you must start by giving us the complete details of your current set up. Is it a laptop or desktop? Model? specifications? Did you install the ssd or did it come pre-installed?
Post the screenshot of your Partitions from Windows. 

Then we can take it from there. 
EDIT: It is also possible to disable UEFI boot (but you may have to reinstall Widnows) if you really want to disable it.
If you Install Ubuntu on a separate Disk and install Grub there too then, NO Windows will not be affected.

---

### Post by loseby on 2013-05-26
My specs are :  GA-Z77X-UD5H , i7 2700k , 2x7970 in xfire, 2 Corsair SSDs ( one has the Win7 O/s and games, the other is pics/music/downloads etc ) , a Samsung 500GH HD for more files & a 120GB OCZ which I want Ubuntu 13.04 on.

What I would like to do is use the F12 key to select what drive I want to boot into ie. either windows Corsair SSD or Linux SSD . I want to boot straight into Windows 99% of the time as soon as I hit the power button except when I want to use Ubuntu, then I would like to use the F12 key and select the OCZ drive as my bootable drive.

Maybe some physical effort would solve my problem.....remove all the drives except the OCZ & DVD and then install 13.04.  Would that give me the option of then selecting bootable drive via F12 key ( boot menu )

btw: the Corsair in Computer management shows a healthy 100mb efi system partition so thats one question solved  :-)


An explaination why is " on another dualboot   PC I removed the Linux hard drive and when I booted all I got was a grub error and no windows...ended up putting the linux drive back in. Dont want this here

---

### Post by fantab on 2013-05-26
Before you start, following are some links you may find very useful. Go through them.
[Back Up Windows and its partitions]("http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710"): see post #3 by MarkPhelps
Installing on Different HDD than Windows:
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Read all the posts by 'oldfred'.

Boot with Ubuntu Install Disk and "Try Ubuntu". From Desktop open Gparted. Using Gparted select your OCZ SSD (Make sure you choose correct Device), from Gparted menubar choose 'Device' -> 'create new partition table'-> 'advanced' -> GPT (GUID partition Table). We are using GPT partition table as your Windows install is UEFI and uses GPT. We have to have Ubuntu also in UEFI mode. If your OCZ is already in GPT then ignore the step.

From the 'Unallocated Space" create partitions: as 
300MB FAT32 and put boot flag on it. Gparted rightclick menu should give you that option to put boot flag after the partiton is created. 
30GB EXT4 for Ubuntu /
4GB SWAP
All the remaining GB EXT4 for /home
CLOSE GPARTED after you have applied all the changes. Restart computer.

Boot with Ubuntu, make sure you boot in UEFI mode, your Ubuntu install media should give you an option to boot in either mode. "Try Ubuntu", and establish internet connectivity.

From desktop 'Install Ubuntu" at the 'Installation Type" dialog where the installer asks you how you want to install Ubuntu, Select "**SOMETHING ELSE**". This should take you to another diaolog (GParted). **Select the correct OCZ device** and select 30GB Partition, click 'Change' at the dialog that opens select USE AS= Ext4, Mountpoint=/, select FORMAT. Then Select the 'All the remaining GB" partition, USE AS= Ext4, Mountpoint=/home, select Format. 
****** At bottom of the first dialog, where you select the device and partitions, you will have an option to select which disk you want to **install GRUB to, choose the correct OCZ drive**, not partition. Thats it. continue with installation.

Reboot. Enter F12 and boot ubuntu.

******* There is a good chance that you may have to run Boot-Repair later (if Ubuntu doesn't boot), and I am not sure how Boot-Repair will fix the boot without interfereing with the Windows boot loader. If you have doubts about the process then don't install Ubuntu at all on the said machine. Or wait for someone more experienced with UEFI and GRUB to guide you.

Good Luck.

---

### Post by Mark Phelps on 2013-05-26
> **fantab said:**
> ... Now, what exactly you mean by, "fast boot into Windows and not having to go through GRUB"? If you are assuming that with GRUB you will be delayed in booting Windows then you are wrong. Grub only does what Windows Boot-loader would do. There is no time lost. ...

Not to start an argument, but that it not true.  IF you boot through GRUB, even if you have Windows as the default selection, there is still time that GRUB will take booting and then handing off control to the Windows boot loader.  It is not instantaneous -- I know, because I have my PC set up exactly like this.

But that said, it's only a few seconds --NOT a long delay, by any measure.

---

### Post by loseby on 2013-05-26
thanks Mark, that is what I meant

to fantab, your patience is a virtue , thankyou for you help

I now have a massive headache after reading those links   :-)   

I have decided that I don't want to risk messing up my Windows installation and files.  UEFI is something I have not kept up to date with and basically know nothing about, it was just a very annoying form of BIOS but now I know a bit more.



So basically I will move the PC and remove all but the OCZ and DVD player and install Ubuntu on that following your 

 > From the 'Unallocated Space" create partitions: as
300MB FAT32 and put boot flag on it. Gparted rightclick menu should give you that option to put boot flag after the partiton is created.
30GB EXT4 for Ubuntu /
4GB SWAP
All the remaining GB EXT4 for /home
CLOSE GPARTED after you have applied all the changes. Restart computer.


Now unlike Kathlyn in one of those other threads I have the option of removing the Hard drive. The case is an Obsedian and had a slot at the top so you can slide standard hard drives or SSD in so if any problems occur after plugging everything back in I can just power down and slide the SSD out.

---

### Post by fantab on 2013-05-26
> **Mark Phelps said:**
> Not to start an argument, but that it not true.  IF you boot through GRUB, even if you have Windows as the default selection, there is still time that GRUB will take booting and then handing off control to the Windows boot loader.  It is not instantaneous -- I know, because I have my PC set up exactly like this.

But that said, it's only a few seconds --NOT a long delay, by any measure.

Thanks Mark. I stand corrected. (To be honest, I never noticed that delay on my computer that also boots windows7, however what you say, is very probable).

@losbey: A good BACK UP is a MUST. 
Have a look at [EasyBCD]("http://neosmart.net/EasyBCD/") (Read the 'Documentation' which is a bit old at the moment but should give an idea what it is) it is to be installed in Windows and it enables Windows Boot Loader to boot Linux OS. EasyBCD from version 2.2 supports UEFI dual-booting, however their documentation is bit old and says it does not. The newer version supports Windows8 so... However, if you intend to use EasyBCD then I strongly suggest you join [EasyBCD Forum]("https://neosmart.net/forums/") and clarify your concerns first. 

Good Luck...

---

### Post by loseby on 2013-05-26
I have all my data backed up on another internal dive as well as on an external drive.  Have being reading the mobo manual and looking there and to say its confusing is the understatement but I have found a solution if I want to use it ..ie. disable all drives except the OCz

Just made a bootable USB and took a shortcut and went straight to install but it failed to detect my current windows installation so I basically aborted

edit:  had a melt down or forums did

was going to say will try it your way now and see how it goes

edit : failed

In the bootmenu ( F12 ) it shows as uefi ocz but it still boots into windows,  the USB stick showed as uefi when I installed  the 13.04

may go and try just an installation without splitting the OCZ up

---

### Post by loseby on 2013-05-26
I have all my data backed up on another internal dive as well as on an external drive.  Have being reading the mobo manual and looking there and to say its confusing is the understatement but I have found a solution if I want to use it ..ie. disable all drives except the OCz

Just made a bootable USB and took a shortcut and went straight to install but it failed to detect my current windows installation so I basically aborted


edit: will not boot into linux

---

### Post by loseby on 2013-05-27
update : no luck in booting Ubuntu 13.04

tried the method suggested and it didnt work, so I booted once again into the USB drive and it saw the previous installation but I wiped that out and let Ubuntu manage the install ..... but when I rebooted it went to Windows so using the F12 key I selected uefi ocz ( the drive I installed windows on ) and go the error - grub rescue - no such device

rebooted again and this time i just selected the ocz drive ( not the uefi ocz drive ) but it booted into windows


Now I am positive its there and the grub rescue prompt is the answer..... just a pit I dont know what question to ask:)

---

### Post by sudodus on 2013-05-27
We are not sure what will work, but there are still a few things to try.

- Disable and/or disconnect the other drives. Keep only the Ubuntu drive connected.

- Run YannBuntu's Boot Repair script and let it help you (first try the default action)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

- and reboot.

---

### Post by fantab on 2013-05-27
Before you run "Boot-Repair" post the output of [**BootInfo Script**]("http://bootinfoscript.sourceforge.net/"), which is part of Boot-Repair. But I suggest you run the script independently from Live Ubuntu Disc. Lets see if all set and ready for Boot-repair. And do tell us the dirve number for OCZ, like /dev/sdc or /dev/sda etc.

---

### Post by loseby on 2013-05-27
Have being checking on efi and in Windows Computer Disk Management it shows this :

Disk 1 100 MB Healthy  EFI System Partition  #   now this is my Windows 7 O/S disk Corsair SSD


Disk 3 shows this 190MB Healthy EFI system Partition / 244 mb Raw ( Healthy Primary Partition ) / 118GB Raw Healthy Primary Partition which is the OCZ SSD


Now I am sure that both O/S are installed in efi mode if you can trust windows


and if I recall correctly the drive is dev/sdd

Now I will go into BIOS and disable all the other drives  except the OCZ  then I will start following the rest of the advice

---

### Post by loseby on 2013-05-27
> **fantab said:**
> You can look at your partitions for a 100-300MB First partition, most probably FAT32 with a boot flag, that is your 'efi' partition. Or post the output of:
```
sudo parted -l
``` 

.

ubuntu@ubuntu:~$ sudo parted -1
                                     
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ VERTEX-TURBO (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  200MB  199MB  fat32              boot
 2      200MB   456MB  256MB  ext2
 3      456MB   128GB  128GB


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs


Model: SanDisk Cruzer Colors+ (scsi)
Disk /dev/sdc: 2001MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      66.0kB  2000MB  2000MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$

---

### Post by loseby on 2013-05-27
> **fantab said:**
> Before you run "Boot-Repair" post the output of [**BootInfo Script**]("http://bootinfoscript.sourceforge.net/"), which is part of Boot-Repair. But I suggest you run the script independently from Live Ubuntu Disc. Lets see if all set and ready for Boot-repair. And do tell us the dirve number for OCZ, like /dev/sdc or /dev/sda etc.Please write on a paper the following URL:
[http://paste.ubuntu.com/5706118/](http://paste.ubuntu.com/5706118/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

No change has been performed on your computer.

---

### Post by loseby on 2013-05-27
it didnt work .... ended up with bootmanager is missing when I booted from the OCZ drive



I am not sure this is the problem but the OCZ is on the Marvel ATA controller and is Gsata ( gigabyte )  ... have a sneaking suspicion it may be causing the problem so I am going to put it on one of the normal sata ports.... on the West Digital Raptor Drive

[SIZE=4]**well have it working **[/SIZE]  but getting the error message "system program problem detected"

When I hit the F12 key I see an entry their Ubuntu and thats what I use  ... now to enable all the other drives and see what happens

---

### Post by loseby on 2013-05-27
have ended up with Ubuntu 13.04 on my rapor and it boots into that automatically but the f12 key gives me the option to select windows boot manager so for now its ok

Now there appears to be a problem with the Marvel 88SE9172 SATA controllers or the SSD drive attached to them , when I used the Intel Z77 sata controller it worked but it was a non SSD drive so cant definitely say thats the problem. 


Some positives :

1/ learnt a hell of a lot more about efi 
2/ usb installation worked perfectly 


One final annoyance :

 Windows shows that I have dives G, H & I which is the Raptor drive that has linux on it. Anyway to hide this drive from Windows ?  

edit: drive G was the OCZ which I now have made Windows but its H & I that still show


Thanks for the help

---

### Post by Mark Phelps on 2013-05-28
> **loseby said:**
> ... Anyway to hide this drive from Windows ?  ...
If your concern is messing with the Linux filesystem while inside Windows -- no worries, as Windows can't read or understand Linux filesystems.

---

### Post by loseby on 2013-05-28
> **Mark Phelps said:**
> If your concern is messing with the Linux filesystem while inside Windows -- no worries, as Windows can't read or understand Linux filesystems.

but if you went to disk management could you or someone not delete the partions and format ...... on the other PC I cannot see the Ubuntu drives at all 


anyway I just tidied up the last thing and it now boots into windows except if I hit the f12 key where I can select Ubuntu which is basically what I wanted from the beginning. A long journey but I learnt a hell of a lot about Gigabytes uefi firmware ( still hard not to call it a bios ) that controls your PC once you hit hit the power button

---

