---
title: "Completely clean computer for fresh install of Ubuntu"
date: 2020-11-06
forum: Installation &amp; Upgrades
---

### Post by uljanap on 2020-11-06
Greetings!
I purchased an Alpha Linux computer several years ago.  They're out of business now as far as I can tell.  It came loaded with Elementary.  I thought I wiped it clean & loaded Ubuntu but, I didn't.  I have tried every suggestion I've found to wipe this mess clean but every option ends up not working.  I cannot boot from a USB although that's how I loaded Ubuntu 14.04.  I've made a live USB of boot-repair-disk but I can't get past the question of automatically updating the software because my mouse fails to function after Boot Repair loads and typing Y or N doesn't work.  I've removed all the information on the computer as I was hoping to give it to my daughter.  I just want to start from a clean slate.  Thanks in advance :-)

---

### Post by mikewhatever on 2020-11-06
Why 14.04? It's old and unsupported, good though it was. Have you tried the 20.04 release?

---

### Post by QIII on 2020-11-06
Hello.

It might be helpful if you would provide the hardware specifications of your machine.

---

### Post by uljanap on 2020-11-07
3.7 GiB RAM
Intel Celeron CPU N3150 @1.60 GHz x4
64-bit 
468.3 GB SSD

and installed on the machine are elementary 0.4.1 and Ubuntu 16.04 (sorry  made a mistake last night with the Ubuntu release...it was late)

---

### Post by uljanap on 2020-11-07
I apologize, I was mistaken, it has 16.04.  I installed it quite a few years ago :-)

---

### Post by ActionParsnip on 2020-11-07
An option in the installer is to use the entire disk and install Ubuntu. This will delete all partition and data and make appropriate partition ls for you then install the OS. You don't need to clear the old stuff off. The installer does this for you.
I also suggest using Ubuntu Focal (Ubuntu 20.04). It is the latest LTS release and will be supported until April 2025

---

### Post by uljanap on 2020-11-07
Can you provide instructions.  I downloaded Ubuntu 20.04 onto a USB from  my WIndows computer but when I insert it into the computer that needs  fixing, it won't boot from the USB.  Years ago I installed Ubuntu 16.04  in this way (but somehow left elementary) years ago on this computer,  but now it's not working.  I must be doing something wrong, I just can't  figure out what.

---

### Post by CelticWarrior on 2020-11-07
Years ago you must have used some software tool to "burn" the ISO into the USB. It doesn't work by simply copying that file.
The Startup Disk Creator you already have both in Ubuntu and Elementary should do it. In Windows use Balena Etcher (fool-proof) or Rufus (needs settings adjusted for BIOS or UEFI differently).

---

### Post by uljanap on 2020-11-07
Thank you CelticWarrior.  I created my boot USB on a Windows computer.  Must have done something wrong.  Repeated on the not-quite-dead-yet Linux machine and viola!  Loading 20.04 as I type :-)  THANK YOU!!!!!

---

### Post by uljanap on 2020-11-07
Something still went wrong :-(  Despite picking to NOT install alongside Elementary that's what happened.  After installing and restarting I get the double boot screen :-(  AND MY TOUCHPAD stopped working :-(   Any ideas on how to 1) get Elementary off the machine? 2) how to get the touchpad working again.  Complicating factors: R not working on the keyboard & I don't have a USB keyboard or mouse.  Thanks for your continued help :-)

---

### Post by CelticWarrior on 2020-11-07
Choosing "erase and install..." does exactly that.
In newer UEFI system - mostly anything from the last decade -, however, older entries in the the ESP (EFI System Partition) aren't removed along with the old OS(es) system partition(s). Not a problem - it changes nothing, the old entries simply no longer work - but can be cleaned after assuring the new OS is properly installed.

Regarding the touchpad I not sure yet. First suggestion - assuming you have a UEFI system with the default Secure Boot enabled - is to disable Secure Boot. If not enough we troubleshoot from there. Also be sure to install all the updates:
```
sudo apt update && sudo apt full-upgrade
```

---

### Post by uljanap on 2020-11-07
Not all peaches & cream :-(  During the install my mouse stopped  working.  The R key hasn't been working for a bit, been using the  onscreen keyboard when necessary.  But after reboot I can't skip the  online accounts and the fixes I found all require an R in the Comand  line.  Is there something else I can do or do I have to go out and buy a  USB mouse?

---

### Post by dragonfly41 on 2020-11-07
Can you use a tool like xdotool or autokey to simulate pressing faulty R key .. as a temporary workaround?
There are other similar tools for UI automation. Actiona is another one.

---

### Post by helen314 on 2020-11-07
Just to verify - and DO NOT want to start a discussion about bios and UEFI! 
Is your start -up firmware bios or UEFI friendly? Or both ?

I assume your initial grub has given you choice 
install
try before installing

I am not familiar with "touch  pad" , but I think you need minimal PS2 connected keyboard. 
My wireless (USB ) keyboard refuses  to let me select options in UEFI setup - it is just "off". 

Good luck

---

### Post by uljanap on 2020-11-08
Dragonfly41...I tried, thanks to your suggestion, but way too complicated for me...went out an bought a USB keyboard & mouse :-) I think life is good again. I, at least am ready & prepared to fight the good fight :-)

CelticWarrior...I tried to disable Secure Boot but could not find instructions specific to Ubuntu 20.04...the instructions I found online did not work.  Can you provide instructions on how to disable Secure Boot if it is still necesssary at this time?  The USB keyboard & mouse seem to be functioning fine.  I installed all updates per your instructions above.  Computer is currently restarting....taking quite a long time.  In my double boot menu it mentions UEFI....so...doesn't that mean it should've deleted Elementary automatically when installing 20.04?  It's taking a long time to re-start so I think I'll hit the hay while it finishes and give you all an update tomorrow.  Thanks, everyone...I'm feeling very hopefull :-)

---

### Post by uljanap on 2020-11-08
@Helen314 

I don't know.

How can I tell if the start-up firmware is BIOS or UEFI friendly? or both?

---

### Post by tea for one on 2020-11-08
> **uljanap said:**
> I tried to disable Secure Boot but could not find instructions specific to Ubuntu 20.04.

Secure Boot is an option in your UEFI (or BIOS) set up pages, often found under the Security section. It is not specific to Ubuntu.

---

### Post by uljanap on 2020-11-09
Today's update is not so good :-(

After loading 20.04 I restarted the machine and it's been spinning ever since (over 24 hours[IMG]https://lh3.googleusercontent.com/bBOtvz_RXmUBCV3mL6xNchzb4B9tQtx7KW6lDkaR1lcLqo4ylt78P12ZGI8JdRc88P9vZXhmX_WGs3q0aSEIUO2eSmwSG4sCCNnabp40laVk03rhzUyCLMFxZdQ1Z5piEC-tEKjSxH4ObtzjCot2wsED6FDTk5uf7PvxCW5nC5nkNm1Z66u3_CoexfuOttXjm8odb1ecl8pTQAuxces3rz9DCLlETY9ywMiNkeeaUCz9ixo8EayWv80O3kYPWVbKfhryXf29_bW3dflZfeUfA9x1YozR0x-xOelQ4cJ9qkYGlWkb_MG6QQq7nO-bNCCv7O_5FY2Y9Vm-2pw8GNt7qeVYPKc3_mNeQJfTiAU6DpD1Xz--ir-MO-F8_FBGtpYZRb9VtM6GZGsX3jKVOQli4PRoXVxejfOBxYF-6OAKaDXrx7mPCXdSm5EZCcVaIXKwETZaNyS4JMMOXQYox2rICYvzuhlu_eLFVJTcP5GhuXr_cJWzurHGLsLBcuSc733o-qQSQ8nMX953YYNkiYEQRQHQzBzLcrixGGrEvAzFH3ip5sTlpflNivxCBxm-yEsankjGvB-NKIgl_7BrwlO-D8BgPZkhfxjk_GjoZLBHM64VOgaXmK8U9BqJemTsx5YShwxC-Ugis--N6LLUvT9luq0wODGEjhy89e87vYVyRWlUHWyKQZ2_CAI1GeKPHRQ=w1545-h869-no?authuser=0[/IMG]             now).  I have tried powering it off.  When I power it back on it is still spinning.  This morning I unplugged the power cord hoping the battery would die...no such luck. I've tried hitting various function keys; Ctr+Alt+Del.  Nothing has an effect on this...the little 3 part circle just keeps spinning....

Any ideas?

Once I get if functioning, I will work on disabling the Secure boot

---

### Post by CelticWarrior on 2020-11-09
Press and hold the power button. After a few seconds it shuts down.
Next boot edit the "Ubuntu" entry and replace "quiet splash" by "nosplash".

---

### Post by uljanap on 2020-11-14
CelticWarrior.  I'm sorry, I don't understand.  It finally came out of the spin & appeared to work normally.  We did not shut it down, just hibernated.  Today it was working VERY SLOWLY so I figured a re-start was in order.  When I restarted it I didn't see what you were talking about and it went into it's eternal spin again.  I have tried holding down the power button but it only restarts the machine & the spin picks right up where it left off.  I'm going to try to quickly insert the Ubuntu install USB in the split second that it's off.  Maybe your instructions will make more sense then.  Thanks :-)  I'll let you know.

---

### Post by uljanap on 2020-11-14
I held the power key down until the "on" light went off.  I stuck the USB drive with Ubuntu on it into the USB port then I turned the computer back on.  The only screen that came on, and it came on right away, was the spinning :-(

I've unplugged the computer maybe the battery will die, but it's holding now again since I loaded 20.04...peculiar but I'm not complaining.

---

### Post by ajgreeny on 2020-11-14
If you want to completely clear the hard disk before installing Ubuntu, boot to the USB install medium (I assume you still can) and choose "Try Ubuntu without installing".

From that running system open gparted which is on all the live systems and using that, delete all the partitions on the hard disk, including the current EFI/ESP partition which will probably be /dev/sda1, and will be about 200 - 500MB in size.

Now go to the "Install Ubuntu" icon on the desktop and use the "Erase disk and install" option.  This will create the partitions needed, ie, a new EFI partition and a new ext4 / (root) partition for Ubuntu.  I never update while I'm installing but leave that until the new OS is running after a reboot; that is your choice.

---

### Post by uljanap on 2020-11-15
ajgreeny, I will try this as soon as it stops spinning and allows me to do something/anything :-)  Considering the machine has NOTHING on it I'm ok, deleting all partitions..it's actually what I wanted to do from the start.  Thanks!

---

### Post by uljanap on 2020-11-15
ajgreeny
I was able to delete all partitions that I found EXCEPT /dev/sdb  iso9660 Ubuntu 20.04.1 LTS amd64.  I hope I'm right in assuming that's the thumb drive with the OS that I want to load

---

### Post by ajgreeny on 2020-11-15
Yes, it is your USB.

If your computer has only one single physical hard drive then it definitely is the USB.
Presumably all the other partitions were /dev/sda#?

The  ***iso9660*** name means it is the standard filesystem type of a USB install disk.  You couldn't delete it because that is the OS that was running.

---

### Post by uljanap on 2020-11-15
VICTORY!!!! I think ;-) 
Ubuntu 20.04 is loaded.  I've re-started several times (that's when it went into the eternal spin after the last install).  The previously loaded Elementary is gone.  Life, I think is good.  

BUT

As I'm loading my daughter's music and videos, it tells me I'm out of space! :-O

The computer originally had a 32GB mSATA solid state disk and a 512GB hard drive.  I swapped the 512GB hard drive for a 500 SSD.

I loaded the OS on the 500 SSD because when I was running 16.04 (on the 32GB mSATA) I kept getting error messages that there was no room to upload updates.  By loading it on the 500SSD I was hoping to avoid that problem.  But alas, it again haunts me :-(   Maybe I did something when deleting all those partitions?  With only 10 Disney movies and 7 albums loaded how can I be out of space?  

It's still early....If it's better to load the OS on the 32GB drive I can re-delete and re-install, no problem.  I just want to sort out all these little issues before I hand it over to an 8 year old.  Thanks :-)

---

### Post by ajgreeny on 2020-11-15
Strange!  

It is difficult to know why you are now running out of space on a larger disk without more info so show us the output of terminal commands ```
sudo fdisk -l
df -hT
``` and we'll move on from there.

---

### Post by uljanap on 2020-11-15
Here's the output you requested

```
dzvinka@dzvinka:~$ sudo fdisk -l

[sudo] password for dzvinka:

Disk /dev/sda: 447,13 GiB, 480103981056 bytes, 937703088 sectors

Disk model: SanDisk SDSSDA48

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: gpt

Disk identifier: C8B8AD69-290E-4FC1-9DE1-51C4CE3DC75A

Disk /dev/mmcblk0: 29,12 GiB, 31268536320 bytes, 61071360 sectors

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: gpt

Disk identifier: 3F1EFAF9-EEA4-43AF-B538-654168C97045



Device           Start      End  Sectors  Size Type

/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System

/dev/mmcblk0p2 1050624 61069311 60018688 28,6G Linux filesystem


Disk /dev/sdb: 59,64 GiB, 64019759104 bytes, 125038592 sectors

Disk model: USB Flash Drive

Units: sectors of 1 * 512 = 512 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disklabel type: dos

Disk identifier: 0x00000000

Device     Boot Start       End   Sectors  Size Id Type

/dev/sdb1          64 125038591 125038528 59,6G  c W95 FAT32 (LBA)


dzvinka@dzvinka:~$ df -hT

Filesystem     Type      Size  Used Avail Use% Mounted on

udev           devtmpfs  1,9G     0  1,9G   0% /dev

tmpfs          tmpfs     378M  1,9M  376M   1% /run

/dev/mmcblk0p2 ext4       29G   28G     0 100% /

tmpfs          tmpfs     1,9G   41M  1,9G   3% /dev/shm

tmpfs          tmpfs     5,0M  4,0K  5,0M   1% /run/lock

tmpfs          tmpfs     1,9G     0  1,9G   0% /sys/fs/cgroup

/dev/sdb1      vfat       60G   56G  4,3G  93% /media/dzvinka/AV FILES

```

dzvinka@dzvinka:~$ ^C

dzvinka@dzvinka:~$

Thanks for your time :-)

---

### Post by oldfred on 2020-11-15
Please use code tags for long terminal output. Easy to add with Forum's Advanced editor and # icon.
Also exclude loop devices as they are just snap programs, not devices.

Rerun this which excluded snaps.
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"

But you show / on MMC device and used 28 of 29GB. 
I have lots of apps installed and am using 8.5 GB, but have all data in separate data partition.

You also show you are using FAT32 on 60GB partition which is full
You movies may not fit. FAT32 has a hard file size limit of 4GB. 
I used to do a image backup to FAT32 and wondered why it always was 4GB even as system grew. Do not use FAT32 except small partitions and do not use image backups.


My partitions:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop" [/COLOR]
NAME        FSTYPE LABEL     MOUNTPOINT   SIZE FSUSED MODEL 
sda                                     931.5G        HGST_HTS721010A9E630 
&#9500;&#9472;sda1      vfat   ESP_B                510.2M         
&#9500;&#9472;sda2      ext4   bionic_b              30.3G         
&#9500;&#9472;sda3      ext4   ISO_b                 49.8G         
&#9500;&#9472;sda4      ext4   backup_b             147.6G         
&#9500;&#9472;sda5      ext4   focal_a               30.3G         
&#9500;&#9472;sda6      ext4   data                 302.8G         
&#9500;&#9472;sda7      swap                          2.1G         
&#9500;&#9472;sda8      ext4   groovy                24.4G         
&#9492;&#9472;sda9      ext4   groovy_k                24G         
nvme0n1                                 465.8G        Samsung SSD 970 EVO Plus 500GB 
&#9500;&#9472;nvme0n1p1 vfat   ESP_NVME  /boot/efi    512M  11.9M  
&#9500;&#9472;nvme0n1p2 ext4   focal_0               29.3G         
&#9500;&#9472;nvme0n1p3 ext4   focal_k   /           29.3G   [COLOR=#ff0000]8.5G[/COLOR]  
&#9500;&#9472;nvme0n1p4 ext4                         29.3G         
&#9492;&#9472;nvme0n1p5 ext4   nvme_data /mnt/data  195.3G 122.4G 

[/FONT]
```

---

### Post by uljanap on 2020-11-16
I didn't consciously do any of it.  It all seemed "off" to me, that's  why I wanted to completely clean the thing before a fresh install of  Ubuntu 20.  I thought it would be the easiest way to resolve the issue  that I really didn't know anything about...being a non-computer person.   I hit erase and re-install from the boot disk after deleting all  partitions....It didn't give me options on how to format the memory, as  far as I recall.  This is jibberish to me, unfortunately.  Can you help   me fix it...I still have no real data on it...the movies are all on a  flash drive so I am fine completely wiping the thing clean again &  re-installing if that's easiest

---

### Post by oldfred on 2020-11-16
If movies are on FAT32 formatted partition on flash drive, they may be damaged, if over 4GB.

With new systems, how you boot install media, UEFI or BIOS is then how it installs. You choose that from one time boot key you use to select to boot installer. 
Microsoft has required Windows to be installed in UEFI boot mode to gpt partitioned drives since 2012 and release of Windows 8, so most systems now are UEFI.
Some tools to create flash drive installer, only create UEFI or only BIOS although the ISO is configured for both.

To have additional partitions to use for data, you have to create partition (s), format partition, give yourself ownership & permission to use it and if internal drive mount with fstab, so always availabe. If external then you just can click on it to mount it and use it.

---

### Post by uljanap on 2020-11-16
That explains why some of them ARE damaged :-)

My understanding is that I need to make a new boot install media AFTER reformatting my thumb drive to UEFI?  if so please give instructions...I have been unable to reformat that thumb drive myself, I assume I'm doing something wrong.  Alternatively, please provide detailed instructions as to what I should do or where to find instructions.  Thanks

---

### Post by uljanap on 2020-11-16
Here's the requested output oldfred:

dzvinka@dzvinka:~$ lsblk -oNAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,fsused,MODEL | egrep -v "^loop"
NAME         FSTYPE   LABEL MOUNTPOINT                     SIZE FSUSED MODEL
sda                                                      447,1G        SanDisk_SDSSDA480G
mmcblk0                                                   29,1G        
&#9500;&#9472;mmcblk0p1  vfat           /boot/efi                      512M   7,8M 
&#9492;&#9472;mmcblk0p2  ext4           /                             28,6G   8,7G 
mmcblk0boot0                                                 4M        
mmcblk0boot1                                                 4M        [COLOR=#888888]
dzvinka@dzvinka:~$ [/COLOR]

---

### Post by oldfred on 2020-11-16
Not sure where you are at now?
If installing in UEFI mode, see link below.
It has install instructions, links to downloads & more info and perhaps then too much data as it tries to cover many different systems.

---

### Post by uljanap on 2020-11-16
> **oldfred said:**
> Not sure where you are at now?
If installing in UEFI mode, see link below.
It has install instructions, links to downloads & more info and perhaps then too much data as it tries to cover many different systems.

How do I know if I'm installing gin UEFI mode?  

I've deleted all the files I transferred to the computer.  I will read  the link Wednesday as tomorrow I've got too much going on to focus on  it.  Then I'll post an update.  Thanks!

It seems this was a lot easier when I first started with Ubuntu in 2008....maybe it's this no frills machine I bought :-(

---

### Post by oldfred on 2020-11-16
Since it has MMC as main drive, it definitely is a lower end system. 
Now some low end systems have a small SSD.

How you boot install media UEFI or BIOS is how it installs. 
Only with 20.10 now is grub shown for both BIOS & UEFI boot.
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If using Rufus, it only creates UEFI or BIOS(CSM) version of install, so no choice once you try to install.
CSM is the official name of to old BIOS boot with UEFI.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
Soon new hardware systems will be UEFI class 3 which does not have CSM.

---

### Post by uljanap on 2021-04-18
thank you all for your help!  I just recently got the machine back from a computer repair shop and there was a bit of something that had broken off inside the machine causing random problems, the last of which was a black screen that I couldn't do anything with.  Working pretty well now except the web cam but I'll post on that if I can't find suggestions on how to fix it.  Thanks again!!!!  Stay well :-)

---

