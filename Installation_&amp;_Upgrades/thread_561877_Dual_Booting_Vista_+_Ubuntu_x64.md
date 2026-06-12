---
title: "Dual Booting Vista + Ubuntu x64"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by kyleabaker on 2007-09-28
I know this seems to be a very common topic, however, I've been searching for ways to fix my booting issues for like 5-6 hours now and have given up on finding a solution on my own. So here I am..

I have Windows Vista Ultimate x64 installed already on a 300gb drive and I've installed Ubuntu x64 using a 10gb allocation on the same drive. The problem I'm having is that once the installation completes my pc just boots up into Vista using the Vista boot loader and grub is never used. I've tried restarting, but grub is never installed correctly. I'd really like to get it working and use the Vista boot loader instead of grub, however, at this point I'd really just like to get it working period so grub would be satisfactory for me. I'm just gonna walk through all of my steps and try to provide all the information needed to get this straight (since I've read several posts and seem what is asked).

My current setup:
Sata 750GB
Sata 300GB

The 750GB drive is just a storage/junk drive. The 300GB drive has ~290GB for Windows Vista Ultimate x64 and I've allocated 10GB of space for Ubuntu which is at the end of the drive. I rebooted and started up the live install disc and ran the setup. I selected Manual in the "How do you want to partition the disk?" step (4 of 7). After this I right clicked the free space (10GB I allocated in vista with the computer management app) and set it with the follow:

Type for the new partition: Primary
New partition size in megabytes (1000000 bytes): 10730
Location for the new partition: Beginning
Use As: ext3
..then clicked ok, right click again and set mount point to "/" since no option was available in the previous window.
Mount point: /

Click forward and continued without a swap drive. Setup the "Who are you?" step and continued and clicked install.

Here is what step 7 printed:
```

Language: English
 Keyboard layout: U.S. English
 Name: Kyle Baker
 Login name: kyleabaker
 Location: America/New_York
 Migration Assistant:
 Windows Vista/Longhorn (loader) (/dev/sdb1):


If you continue, the changes listed below will be written to the disks. 
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed: 
 SCSI3 (0,0,0) (sdb)

The following partitions are going to be formatted:
 partition #2 of SCSI3 (0,0,0) (sdb) as ext3

```

I installed 2-3 times testing and kept removing the volume in Vista and reinstalling Ubuntu, but on the last option it has an option to select the Device for boot loader installation (which is "(hd0)" by default) and I tried hd0 and hd1 for this since my 300gb drive is listed second in the fdisk -l print out (I'll paste it below). The results were different. With hd0 my pc would reboot into Vista and never acknowledge Ubuntu or Grub, however, hd1 seemed to install Grub, however I got error 22 saying that the partition was not found.

I also tried using EasyBCD 1.7 to add a Linux boot option and selected the correct linux partition, but it didn't work. So I tried it with the option saying grub was not installed (so it used NeoGrub or something like that) and once I got to the grub menu none of the options worked except other os Windows Vista.

So now I've installed Ubuntu using all the same steps as listed above and left the default Device for boot loader installation option (hd0) and it still won't boot or show grub.

Here is "fdisk -l", my drive setup/structure.
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       91202   732571648    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       35179   282570470    7  HPFS/NTFS
/dev/sdb2           35180       36483    10474380   83  Linux

```

What can I do to get this straight? I've searched and searched and tried several methods that have been posted in the past, but none of them worked. I've had to run fixmbr several times to get back into windows after messing up the vista loader and grub at times, but at the moment Vista loader is working fine for Vista with no option for Ubuntu. So please shed some light on this issue for me and help me get it sorted out.

Thanks in advanced.

---

### Post by BigDaddy-CF- on 2007-09-28
It seems like your problem is that you installed Vista after Ubuntu and it's boot manager has taken over but you didn't make a backup of your GRUB boot manager so that you could make an entry in Vista's boot manager to point it to Ubuntu. I'm no Linux expert by far but if it were me I'd just follow the ubuntu installation portion of the triple boot guide below using the new Gutsy Beta CD it's been very stable for me anyway and has the latest support in it([x86]("http://releases.ubuntu.com/releases/7.10/ubuntu-7.10-beta-desktop-i386.iso")) or ([64-bit]("http://releases.ubuntu.com/releases/7.10/ubuntu-7.10-beta-desktop-amd64.iso")) If you do that properly then you should just have Ubuntu's boot manager GRUB managing your boot process and you won't have to mess with Vista's pain in the rear boot manger at all. Maybe some Ubuntu guru's can chime in here on just how you might be able to get back into your ubuntu insall without having to reinstall ubuntu as I have no clue on that note, but just in case you want do want to use Vista's boot loader when you manage to get access back to your linux install here's how I got my Ubuntu installation to show up in Vista's New Boot Loader(why make it so much harder MS?)
first things first from within Ubuntu type the following into a console to see the available partitions, pay special attention to whether or not your boot device is listed as /dev/hda or /dev/sda's mine are SDA's
```
sudo fdisk -l
```
Ok now type the following to see your mount points```

sudo df
```
Type the following within Ubuntu console to back up your GRUB boot manager, you need to take note of which drive has your linux installation on it, it's usually going to be either HDA or SDA though so if yours is /dev/hda/ or /dev/sda you need to put what is appropriate for you in the code below and also substitute the path of a writable partition which is also accessible for Vista for /media/SHARE/ if you need to
```
sudo dd if=/dev/sda of=/media/SHARE/ubuntu.bin bs=512 count=1
```
check the backup  by typing the following in the console
```
hexdump -C /media/SHARE/ubuntu.bin
```
search for some GRUB&#8217;s references. If it is blank (zeros) or has NTFS strings in it, you probably should 
check the if&#8217;s hda/sda parameters.
Thank Ilya Hevnikov's [Triple Boot XP,Vista, Ubuntu guide]("http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/") for the above
Hope you saved that grub backup to somewhere that's accessible from vista!
Now you need to basically create an entry in Vista's boot loader program that points to your backup GRUB .bin file
Now editing the boot menu in vista is WAY more complicated than it used to be in XP
here's all the help you should need if my text below doesn't guide you enough [1]("http://technet2.microsoft.com/WindowsVista/en/library/85cd5efe-c349-427c-b035-c2719d4af7781033.mspx?mfr=true"), [2]("http://technet2.microsoft.com/WindowsVista/f/?en/library/08d64d13-4f45-4a05-bd86-c99211a93dd91033.mspx"), [3]("http://vistafaqs.com/viewfaq.aspx?faq=73"), and [4]("http://www.x64bit.net/site/board/lofiversion/index.php?t1209.html")

Now In vista create a shortcut to command prompt and set it to run as administrator by right clicking the shortcut->properties->shortcut tab->advanced button->tick the "run as administrator" tick box->hit ok button->hit apply button->hit ok button and run command prompt. Vista will ask if it's ok to continue or not tell it to continue, my command prompt starts off in C:\Windows\System32> I hope yours does too. If a program is exhibitiing weird behavior and or not working in Vista you can use this trick of substituting a shortcut to run it as an administrator. This has fixed a number of issues for me in Vista especially on programs that run as a startup. Now type bcdedit /? and it will show you a list of the command parameters you can use. I type bcdedit /enum to enumerate the current listings for the vista boot editor
At that point in time it only listed one boot manager and one boot loader, since I had moved my GRUB backup which I had named Ubuntu.bin to C:\windows\.
Its important to make a backup at this point so that if you screw up you can fix it.
```
bcdedit /export "D:\bcdbackup\BcdBackup"
```
will backup your boot config, this folder must be created if it doesn't already exist prior to the backup operation
```
bcdedit /import "D:\bcdbackup\BcdBackup"
```
will import that backup to fix whatever you did if you have problems

now keep in mind that I don't triple boot but just dual boot Vista/Gutsy because windows is required for some of my school work. As such just point to my Linux grub backup ubuntu.bin as the legacy os entry. I will redo my entry to not only reflect my newer version of Ubuntu(feisty to gutsy) but also so that I can guide you through the process. So you'll be able to skip this first portion about deleting an entry but hop back in when I get to creating your new entry
so I type bcdedit /enum to get a listing of what's in my boot manager store and I get something like this
```
Windows Boot Manager
----------------------------
identifier                             {bootmgr}
device                                 partition=C:
description                            Windows Boot Manager
locale                                 en-US
inherit                                {globalsettings}
default                                {current}
resumeobject                           {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
displayorder                           {current}
                                       {ntldr}
toolisdisplayorder                     {memdiag}
timeout                                {30}

Windows Boot Loader
--------------------------
identifier                             {current}
device                                 partition=C:
path                                   \Windows\system32\winload.exe
description                            Microsoft Windows Vista
locale                                 en-US
inherit                                {bootloadersettings}
osdevice                               partition=C:
systemroot                             \Windows
resumeobject                           {3fcc4b92-260f-55ab-6a28-c3fd78c2f4ad}
nx                                     OptIn

Windows Legacy OS Loader
---------------------------------
identifier                             {ntldr}
device                                 partion=C:
path                                   \Windows\ubuntu.bin
description                            Ubuntu 7.04 [Feisty Fawn]
```

now to delete my now incorrect boot listing I type the following because my linux entry is listed as my legacy OS loader
```
bcdedit -delete {legacy} -f
```
I could have also typed
```
bcdedit -delete {ntldr} -f
```
now when I type bdedit /enum the legacy OS loader entry is gone so time to put a new one in it's place, I've already backed up a new gutsy GRUB backup and copied it over my Feisty GRUB backup so here goes nothing
```
bcdedit /create {legacy} /d "Ubuntu 7.10 [Gutsy Gibbon]"
```
or you could type
```
bcdedit /create {ntldr} /d "Ubuntu 7.10 [Gutsy Gibbon]"
```
Both ways show up as Windows Legacy OS Loaders, the drawback being you can only have one legacy entry.
```
bcdedit /enum all
```
shows my new entry, now time to enter some configuration for my new entry
```
bcdedit /set {legacy} device partion=C:
bcdedit /set {legacy} path \Windows\ubuntu.bin
bcdedit /displayorder {legacy} {current}
```
That last line adds your entry to the actual boot sequence with Ubuntu first and vista second you can reverse that if you would like. On a side note grub makes this whole boot selection process a lot easier to if you installed Linux after vista this process becomes a lot easier, since you don't have to mess with Vista's new boot loader at all if you don't want to. The only way I know of currently to create a new GUID so that you can create what amounts to multiple legacy entries is to do the following.
```
bcdedit /copy {current} /d "copyofcurrent"
```
This will make a new entry with all the settings of the current entry(Vista) but with a new GUID, so you can now start to set its parameters to what you would want just like above only using this method you aren't limited to making 1 new entry.
```
bcdedit /set {NewlyCreatedGUIDhere} path \Windows\ubuntu.bin
bcdedit /set {NewlyCreatedGUIDhere} DESCRIPTION "Ubuntu 7.10 [Gutsy Gibbon]"
```
Notice that there's a reason I typed the last line of code the way I did

---

### Post by kyleabaker on 2007-09-28
Thanks for the walk through with 7.10, however, it seems you've misunderstood the problem I'm having. As I mentioned earlier, I had Vista installed already and made another partition on the same hard drive for Ubuntu. After installing Ubuntu there were no signs that Grub had installed. I'm currently downloading 7.10 and will test it, but I'll be back if it doesn't work right off the bat. Thanks.

---

### Post by logos34 on 2007-09-28
Any reason you didn't make a swap partition?  It's really a good idea even if you have a ton of ram.

If 7.10 doesn't fix the problem, it may be that the ubuntu installer is getting the kernel path(s) wrong in menu.lst.  

Try this:

Use the [ubuntu live cd to reinstall Grub]("http://ubuntuforums.org/showthread.php?t=224351") to '(hd1)'.  When the menu screen comes up, select the kernel at the top and hit 'e' key to edit.  On the 'root' line hit 'e' again and change from (hd1,1) to (hd0,1), or vice-versa.  Press 'enter' and 'b' to boot.  If that boots you into linux go straight to menu.lst and change 'groot' and 'root' paths.

**gksudo gedit /boot/grub/menu.lst**

---

### Post by kyleabaker on 2007-09-29
I ended up disconnecting my 750GB hard drive that had nothing to do with the installation and reinstalled..somehow that eliminated any issues it was having..so I've got Ubuntu 7.04 installed now and grub is loading it fine as well as Vista. I still haven't reconnected the 750gb drive so we'll see how that goes later I suppose. Now I'm having problems with Beryl. At first the titles were disappearing, but I found a supposed fix and edited the xorg.conf file accordingly, however, now nothing si applied. Beryl loads (atleast the icon loads in the top right), but I don't have any Beryl features working for some reason. I'll take that to another forum forum/thread though. If anyone knows whats going on with Beryl though, please feel free to send me a pm or a link or something. Thanks for the help..

But to anyone ahving similar problems to mine, I suggest disconnecting all other harddrives outside of the ones that have OS's on them for Grub to configure. Maybe that will help someone else in the future.

---

### Post by BigDaddy-CF- on 2007-10-07
why r u using beryl when comp-fusion is available? your using 7.04(feisty fawn) so[ here]("http://ubuntuforums.org/showthread.php?t=272104") is the thread for you. Note that 7.10(gutsy gibbon) has compiz-fusion built in

---

### Post by kyleabaker on 2007-10-07
@BigDaddy-CF-
Thanks for the help. I actually got Beryl working fine not long after that post. I have dual monitors so that was the main problem, but I got it working by using Twin View.

---

