---
title: "Can't install Ubuntu!"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by kyral210 on 2011-02-18
I thought I would take the plunge and install Ubuntu on my PC. Not taking a massive leap though, im installing it inside Windows. It seemed to install fine, but then it had to restart and I got this screen:

[IMG]http://farm6.static.flickr.com/5252/5455115673_35f98f4127_z.jpg[/IMG]

What does it mean? What can I do to get Ubuntu working? Oh, I run Windows 7 as my main OS.

---

### Post by sikander3786 on 2011-02-18
The error you are receiving is a result of bad burn or corrupt ISO image in most cases.

Check the MD5SUM of your downloaded image and make sure it is healthy.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, burn it to a CD and burn it at the lowest possible speed. I use 4x.

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Or if your Bios supports USB boot, burn a USB using UNetbootin.

[http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html](http://ubuntu4beginners.blogspot.com/2011/01/create-ubuntu-live-usb-using-unetbootin.html)

---

### Post by Rubi1200 on 2011-02-18
See my answer here:
[http://ubuntuforums.org/showthread.php?t=1041067](http://ubuntuforums.org/showthread.php?t=1041067)

Please don't hijack threads or post on the same subject multiple times. It makes it harder for those who want to try and help you to keep track of what is happening.

Try also to be more specific about when exactly you did during the installation process e.g. did you choose to install to the C drive or another drive?

The more information we have, the better we can help you.

Thanks.

---

### Post by kyral210 on 2011-02-18
Hi

Sorry, I wasn't trying to hijack any other threads or anything. Im just a bit lost in all of this.

Yes, I installed on my C Drive.

I uninstalled Ubuntu and then reinstalled it with a new DVD burnt with the latest download ISO. All was fine. I was in Ubuntu. So I did what I always do with OS's and I installed the updates. All seemed fine. I added the additional Nvidia driver and I had to restart to complete. Ok, so I restarted and lo and behold, the error I posted above came back.

Does that mean I have to uninstall Ubuntu again?

---

### Post by Rubi1200 on 2011-02-18
This is what I suggest you do:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by kyral210 on 2011-02-20
Here you go, sorry it took me so long.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => HP/Gateway is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   156,299,263   156,297,216   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *     11,197,305   488,392,064   477,194,760   7 HPFS/NTFS
/dev/sdc2                  63    11,197,304    11,197,242  12 Compaq diagnostics


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       79ce9e68-a97c-47e2-a23c-cb6e5434d49f   ext4                                     
/dev/sda1        4AD08D69D08D5BD7                       ntfs       Main Hard Drive               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4E9C0CFA9C0CDDF9                       ntfs       Speed Disk                    
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3C3C1BAF3C1B6366                       ntfs       Data Store 1                  
/dev/sdc2        2D55-4C0A                              vfat       RECOVERY                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        54F4B347F4B32A5E                       ntfs       Backup                        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


```

---

### Post by Miguel Tavares on 2011-02-20
Hi,
this is a bug in the windows installer + grub config and ive created a bug ticket on this issue and a workaround for it:

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/722030](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/722030)

Regards

Miguel Tavares

---

### Post by Miguel Tavares on 2011-02-20
Its simple man,
you just have to do the following:
umount /host
ls -l |grep /dev/sd*
find the sd that as the /ubuntu and to do this if you do not recall mount them one by one untill you mount the correct one.
When you find it, memorise the /dev/sd that provided the /ubuntu and edit the /boot/grub/grub.cfg for the correct menuentry... eg below

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set 6e6c082d6c07eea1
        loopback loop0 /ubuntu/disks/root.disk
        set root=(loop0)
        linux /boot/vmlinuz-2.6.35-25-generic root=[SIZE=3][COLOR=Red]**/dev/sda5**[/COLOR][/SIZE] loop=/ubuntu/disks/root.disk ro   quiet splash
        initrd /boot/initrd.img-2.6.35-25-generic
}

after that just issue a reboot and you should not drop to a shell again :D

Kindest Regards

Miguel Tavares

---

### Post by kyral210 on 2011-02-20
Im really sorry, but im not sure what all of that means. Im very new to Linux and I dont know how to interpret and carry out what you said. Could you make it a bit clearer, sort of 'idiots guide'?

---

### Post by Miguel Tavares on 2011-02-20
ok ,
when you drop to the shell, give me the output from these commands and we will go from there:

Q. --> How many Disks and Slices / Partitions do you have--> 
Please Execute the Following 
1 - ls -ls /dev/sd*
2 - ls -ls /host

_Good to Know_
 
 sda is a hard disk drive
                        sdb is a hard disk drive
                        sdc is a hard disk drive
                        [COLOR=Red]sda1[/COLOR] is a slice or partition within the [COLOR=Red]sda[/COLOR] hard disk drive
                        sda2 is a slice or partition within the sda hard disk drive
                        [COLOR=Red]sdb1[/COLOR] is a slice  or partition within the [COLOR=Red]sdb[/COLOR] hard disk drive

Now:

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             15G  3.9G  9.7G  29% /
none                  993M  276K  993M   1% /dev
none                 1000M  876K  999M   1% /dev/shm
none                 1000M  108K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
**[COLOR=Red]/dev/sda5             [/COLOR]**[COLOR=Red][COLOR=Black]120G   67G   54G  56%[/COLOR][/COLOR]**[COLOR=Red] /host[/COLOR]**

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    62926604    31463271    7  HPFS/NTFS
/dev/sda2        62926605   312576704   124825050    f  W95 Ext'd (LBA)
[COLOR=Black][COLOR=Red]/dev/sda5[/COLOR]        62926668   312576704   124825018+   7  [COLOR=Red]HPFS/NTFS[/COLOR][/COLOR]

root@ubuntu[COLOR=Red]:/host/ubuntu/disks[/COLOR]# ls -lh
drwxrwxrwx 1 root root    0 2011-02-18 14:40 boot
-rwxrwxrwx 2 root root  [COLOR=Red]15G[/COLOR] 2011-02-20 11:00 [COLOR=Red]root.disk[/COLOR]
-rwxrwxrwx 2 root root 256M 2011-02-18 16:11 swap.disk

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             [COLOR=Red]15G [/COLOR] 3.9G  9.7G  29% /

the root.disk is the file that you are looking for and it is not on the disk that you currently have mounted on the directory /host.
You will need to find this file in your /dev/sd* in order to put the correct path for it to boot properly because *_[COLOR=Red]the partition that you currently have mounted in /host does not contain the install dir of ubuntu, nor root.disk...[/COLOR]_*

Please Execute the Following:
1 - ls -ls /dev/sd*
2 - ls -ls /host

---

### Post by kyral210 on 2011-02-20
Ok, this is weird. I rebooted my PC, chose Ubuntu and after briefly flashing the 'log in with user name' screen, went strait into Ubuntu. I am not writing this from the desktop environment. Do you think launching Ubuntu from the CD somehow fixed it? I cant think how. Either way, I will let you know if the problem comes back.

---

### Post by Miguel Tavares on 2011-02-20
> **kyral210 said:**
> Ok, this is weird. I rebooted my PC, chose Ubuntu and after briefly flashing the 'log in with user name' screen, went strait into Ubuntu. I am not writing this from the desktop environment. Do you think launching Ubuntu from the CD somehow fixed it? I cant think how. Either way, I will let you know if the problem comes back.

Cool, in the mean time, consider SOLVING this thread using the [Thread Tools]("http://ubuntuforums.org/showthread.php?t=1690220&page=2&nojs=1#goto_threadtools")

Kindest Regards

Miguel Tavares

---

### Post by Rubi1200 on 2011-02-20
Hi kyral210,
thanks for posting the results of the script.

I see meanwhile you seem to be back in business:
> I rebooted my PC, chose Ubuntu and after briefly flashing the 'log in with user name' screen, went strait into Ubuntu.

We have seen this happens sometimes; not sure if there is a logical explanation for when it happens.

In any event, I suggest you lock the grub packages to prevent this happening again.

See here for more details (section right after the Permanent Fix):
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by kyral210 on 2011-03-20
It keeps happening to me. Why? Pretty much every time I do an update it happens. Sometimes I boot into Windows and that solves it, other times not (like now). 
 
Myother laptop is really reqally old, and duel booting Vista and Ubuntu (same installation CD) and guess what, not a single Ubuntu problem ever. Is it worth I uninstall UBuntu and reinstall it?

---

### Post by kyral210 on 2011-03-21
NOpe, reinstalling with a freshly burnt CD installation of Ubuntu 10.10 doesnt help

---

### Post by Rubi1200 on 2011-03-21
Before you reinstall again, which I suggest, first defragment the drive and run chkdsk.

After reinstalling, lock the grub-* packages. Details can be found in the main post here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

