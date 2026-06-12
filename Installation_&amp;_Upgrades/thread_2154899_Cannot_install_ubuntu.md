---
title: "Cannot install ubuntu"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by manngaurav on 2013-06-16
I have acer aspire 4752, bought on 15th august 2012, it didn't ship with ANY windows , and the win 7 that the dealer installed was pirated so one day it crashed, and i installed WINDOWS 8 PRO.
the reason for stating that win 7 thing is because after searching the htreads i found there is an issue with secure boot so i think that thats not my issue. I made a live usb of UBUNTU 13.04 64-bit.
I have CHECKED the md5hash and its correctand i have used unetbootin to create the usb  I have no problems in booting with USB and the live usb works well, i am typing through the booted live usb now infact the even BCMwifi works out of box but i when i PROCEED TO INSTALL NOTHING HAPPENS JUST BLACK SCREEN AND THEN IT REBOOTS. i have done it 10 times just the same thing no error or message just black screen and the system restarts , please someone help me i really want to install ubuntu :)




thank you very much evryone who took the time to reply to a complete dumb like me :)

---

### Post by fantab on 2013-06-16
Perhaps the .iso did not burn correctly. Try burning it again.

Also tell us how did you install Windows8? Did you install it in UEFI mode or the BIOS mode?

---

### Post by cincinnatus13 on 2013-06-16
Honestly, I think the iso burn is bad. Reason I say that is, I tried a few times to get unetbootin to make the USB drive bootable. It kind of does but apparently 13.04 does NOT play well with unetbootin. What I ended up doing was using one of two methods:
1) Use PowerISO on Windows. It'll burn it right (though it is a pain to get it to format the drive entirely again after you're done with the liveUSB.)
2) Use the Startup Disk Creator in Ubuntu (if you have access.) Absolutely no issues with this method.

---

### Post by manngaurav on 2013-06-16
ok i burned the iso again using the startup disk creator but now i dont have any dual boot option..?[ATTACH=CONFIG]243877[/ATTACH][ATTACH=CONFIG]243877[/ATTACH]   ,  

before this step this appears  [ATTACH=CONFIG]243878[/ATTACH]     i have tried doing both YES  and NO , i even tried YES once it gave no dual boot , then i rebooted and tried NO still didnt give th edual boot option :(

---

### Post by cincinnatus13 on 2013-06-16
Looks like it's saying that your primary hard drive is already mounted (ie, you probably clicked on it in Files or something.)
Go ahead and unmount it. Then you should be able to see the option to install alongside Windows. It just can't "see" that Windows is on it while it's mounted.
You can either unmount it in the installer or in Gparted, which is available on the liveUSB.

Edit- and since I'm not too familiar with Ubiquity, you might have to restart the installer once it's unmounted so it can see it.

---

### Post by fantab on 2013-06-16
Windows 8 has this '**fast startup**' feature, which is actually 'Hibernates' your Computer when you shutdown. You may have to disable it because in effect Windows is still running with 'fast startup' enabled and that its partition is in use.

To **disable** 'fast startup' in Windows8: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Also post the output of the following command; run it from Ubuntu DVD/USB->Try Ubuntu without installing-> Terminal [Ctrl+Alt+T]:

```
sudo parted -l
```

---

### Post by manngaurav on 2013-06-16
the 'fast startup' thing shouldn't apply because on the first usb it showed the dual boot option, meanwhile i am mounting again :(  , so will post back

---

### Post by manngaurav on 2013-06-17
I  am going to install ubuntu with DUAL BOOT OPTION  i want to install it on the highlighted drive here
[ATTACH=CONFIG]243908[/ATTACH]       and i dont want to mess with anything else other than this drive it has 124 gb space and is completely empty but when i click next this shows up [ATTACH=CONFIG]243909[/ATTACH]          please tell me how to DUAL BOOT , again i want my ubuntu installed on the hihglighted drive only .

---

### Post by manngaurav on 2013-06-17
without doing anything else i just re-mounted and now the dual boot option (but using dual boot does the same thing black screen and reeboot so i have chosen the something else option here ) shows but i got stuck here:

i want to DUAL BOOT with my UBUNUT 13.04 installed on the HIGHLIGHTED DRIVE ONLY      [ATTACH=CONFIG]243911[/ATTACH][ATTACH=CONFIG]243910[/ATTACH]             

but when i click install that error shows up . what to do please once again i need DUAL BOOT and the ubuntu should be INSTALLED ON /DEV/SDA4/ ntfs   ONLY.    I dont want to mess with anything else

---

### Post by manngaurav on 2013-06-17
here is the output of parted -l 
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      106MB  107GB  107GB  primary  ntfs         boot
 2      107GB  215GB  107GB  primary  ntfs
 3      215GB  366GB  151GB  primary  ntfs
 4      366GB  500GB  134GB  primary  ntfs


Model: Sony Storage Media (scsi)
Disk /dev/sdb: 8100MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8100MB  8100MB  primary  fat32        boot, lba

---

### Post by 3rdalbum on 2013-06-17
You need to set the partition's mount point to / on that screen. The / partition is the "root file system".

---

### Post by manngaurav on 2013-06-17
My system crashes too

---

### Post by manngaurav on 2013-06-17
i think everyone here is a little bit busy and ](*,) but still waiting if someone helps else i would have to give up on ubuntu :(

---

### Post by manngaurav on 2013-06-17
COULD YOU PLEASE PLEASE be more clear i did not understand anything  i just have been using ubuntu for past 30min

---

### Post by ikt on 2013-06-17
You need to create at least 2 specific partitions.

For example on Windows you have the "C:\" drive, and swap space is automatically part of that.

On ubuntu/linux you want to create a "root" or "/" partition and a 2-4GB swap space on the drive you want to install it to. Make sure to put the MBR on the drive that the computer boots up onto first.

Are you installing Ubuntu on the same drive as windows?

---

### Post by manngaurav on 2013-06-17
no my windows is in drive C or dev/sda1  and i am trying to install ubuntu in drive e or dev/sda4 can you please give a step by step method to create that root and swap thing

---

### Post by ajgreeny on 2013-06-17
I spite of what windows is telling you with drive C: and drive E:, you only appear to have one physical drive, so great care is needed when you install to make sure you don't overwrite any of your windows OS or data that you must keep.  It also means that ikt's comment about the MBR of the device you boot to is superfluous; you only seem to have the one.

It looks as if you have already chosen the "Something Else" option judging by the screenshots you show, which is a good start, however, it would be good to know more about the machine you have and whether or not it is using old style BIOS or the newer UEFI, as that will make a difference in the way you need to go from here.  Can you therefore show us the output of ```
sudo fdisk -l
sudo parted -l
``` which will show more detail of your system's partitions at present.  Use those command one by one; the first may just show an error mentioning GPT partitions, but if so the second will show what is needed.

---

### Post by CharlesA on 2013-06-17
Uh.. there is another thread here: [http://ubuntuforums.org/showthread.php?t=2154899](http://ubuntuforums.org/showthread.php?t=2154899)

I do not know if it is about the same issue or not, though.

---

### Post by matt_symes on 2013-06-17
Threads merged.

Please don't create multi threads for the same problem.

---

### Post by fantab on 2013-06-17
> **manngaurav said:**
> here is the output of parted -l 
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      106MB  107GB  107GB  primary  ntfs         boot
 2      107GB  215GB  107GB  primary  ntfs
 3      215GB  366GB  151GB  primary  ntfs
 4      366GB  500GB  134GB  primary  ntfs


Model: Sony Storage Media (scsi)
Disk /dev/sdb: 8100MB
Sector size (logical/physical): 512B/512B
Partition Table:** msdos**

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8100MB  8100MB  primary  fat32        boot, lba

With 'msdos' partition table you can only have 4 Primary partitions, which you already have. For Ubuntu you will need atleast 2 paritions, one for '/' and other SWAP. You can also have /home which is recommended but not a MuSt.
Ubuntu will NOT install to a NTFS formatted disk or Partition.

Here's what you can do:
From Windows, DELETE the last or fourth partition of 134GB. Leave the space 'unallocated' and shut down. 
Restart with Ubuntu LiveDVD/USB and 'Try Ubuntu without installing'. Let the desktop load.
Using GPARTED make the entire 'unallocated space' as an EXTENDED Partition. [Extended Partition is a Primary Partition but is also a container for Logical Partitions. Within an Extended Partition we can have more than 100 Logical Partitions].
After creating the Extended Partition you will see that you still have 'unallocated space'. From that space create:
30GB Logical ext4 [to install Ubuntu]
2-4GB Logical Linux SWAP
All the remaining GB Logical ext4 /home [here you will be storing your DATA]

Apply changes in Gparted and exit.

From desktop ' Install Ubuntu'. From the dialog which says 'Installation Type' choose 'SOMETHING ELSE'.
From subsequent dialog select the 30GB partition and click 'Change'. Adjust the settings as: USE AS=ext4, MOUNTPOINT=/ and format. Similarly, choose the last partition/DATA partition and USE AS=ext4, MOUNTPOINT=/home and format. No need to do anything with SWAP partition.

That should install Ubuntu as we want it.

Good Luck...

---

### Post by manngaurav on 2013-06-17
heres the output to sudo -fdisk and parted -l

[ATTACH=CONFIG]243916[/ATTACH][ATTACH=CONFIG]243917[/ATTACH]

---

### Post by manngaurav on 2013-06-17
@fantab thank you for such detailed help ,here is the gparted pic[ATTACH=CONFIG]243915[/ATTACH] after i did everything just as you said but i have one doubt will i be able to dual boot...? because that is what i want as i am completely newbie to ubuntu i dont want to delete my windows yet and the tragedy is i dont even have the wndows installation CD in case i brick my system so i need to be extremely careful

---

### Post by cincinnatus13 on 2013-06-17
^^ Looks like you need to highlight sda5, hit change, mark it as root and format for ext4 or whatever you want.
Just saying that because its label is "s" which seems strange to me.

Also, how much RAM do you have on your machine? 4GB for swap is a bit excessive IMO, even for a low specced machine. This is Linux after all, not Windows with its huge pagefile. You could possibly shrink that down to 2GB and be just fine. If you do, move the slider away from whatever partition you want to have more space (ie. leave the unallocated space towards the partition to want to make bigger.)

Lastly, as long as you are marking root, swap, and /home, Ubuntu won't mess with your Windows. It will detect Windows and give you a GRUB menu option for booting into Windows. Worse comes to worse and you uninstall Ubuntu, there are plenty of boot repairers and things you can do to fix your MBR for Windows. So don't worry about that.

---

### Post by manngaurav on 2013-06-17
Hey thanks i am able to proceed with the installation now thank you very very much @fantab :)  and @cincinnatus13 i already have proceeded with the installation and that label 's' i gave it myself through gparted and sorry you were bit late i have already proceeded with the 4gb swap  , i have 2gb ram and i think that's more than enough because the min requirements for ubuntu shown here was 512mb ram :P

---

### Post by ajgreeny on 2013-06-17
The first thing to do if you can boot to Windows is make sure you have made the recovery disks, or whatever they're called, that MS tells you to do.  That will allow you to restore the bootloader if for whatever reason grub fails.

I am not sure you can simply mark partitions as / using gparted at this stage, after installation; I think you may need to start again from scratch, but this time, after choosing "Something Else" delete the partitions sda5, sda6 and sda7 to leave unallocated space.

Now make a new logical partition sda5 of 20GB (30GB is too large for root in my opinion), format as ext4 and set the mountpoint as / (or root)
Make a second logical partition sda6 of 4GB and format as swap, no mountpoint needed for swap.
Use all the remaining space as a new logical partition sda7, format as ext4 and set /home as mountpoint.

That should get you to where you need to be with grub installed to the MBR of /dev/sda, not to a partition but just to/dev/sda

EDIT:
I was a bit slow with my response!

Can you now boot both OSs?  If so, ignore my comments, particularly about partition sizes; just enjoy ubuntu.  If you have any more problems come back again and I'm sure we'll do what we can for you.

---

### Post by ubfan1 on 2013-06-17
You have no unallocated space on the disk, and no partition of a type (like ext4) that Ubuntu can install to.  You can either just delete the sda4 partion, and let the Ubuntu installer recreate it, or use a partition editor like gparted to change the type.   Since your partition type is msdos, you are limited to 4 primary partitions, so I'd recommend:
  1) Use a partition editor to delete the last primary partition.
   2)Create an EXTENDED partition using that freed space.
   3)Now you can create logical partitions in the extended partition -- a root "/" type ext4 (probably default) and swap minimum.
   4)run the Ubuntu installer
You might want to uncheck the [Solved] button if you are still haveing problems.

---

### Post by manngaurav on 2013-06-17
hey i have installed ubuntu but GRUB DOESN'T SHOW UP , my pc boots up straight into windows 8 and i am sure that my pc doesn't have secure boot option , i have tried the boot repair here's the url that it gave me [http://paste.ubuntu.com/5774692/](http://paste.ubuntu.com/5774692/)   , haven't rebooted yet,  will post back

---

### Post by manngaurav on 2013-06-17
YES! the boot-repair did it i am succesfully able to dual boot now thank you very much guys this is one dedicated community contrary to windows 8 where i never figured out how to post questions. feeling like the happiewst/proudest person , infact i wasn't so happy when i successfully ran mac os x on my windows laptop :P  , i really love linux please can anyone give some useful how to's

---

### Post by ubfan1 on 2013-06-17
Sorry about the last post, I missed the last two pages of discussion.  Start looking at
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
for all sorts of help and documentation, or google for ubuntu howto
Good to hear things are working for you.

---

### Post by ajgreeny on 2013-06-18
There's also a very good range of ubuntuguides available from [http://ubuntuguide.org/wiki/Ubuntu:Precise](http://ubuntuguide.org/wiki/Ubuntu:Precise) or for your version of Ubuntu, [http://ubuntuguide.org/wiki/Ubuntu:Raring](http://ubuntuguide.org/wiki/Ubuntu:Raring)

---

