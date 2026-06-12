---
title: "Win 7 won't boot after installing xubuntu on 2nd hdd on asus laptop"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by Paco62 on 2012-11-27
I have an Asus G75VW 'Republic of Gamers' laptop with Win 7 installed, and the os worked properly.  I removed the hdd containing win7 and installed a hdd containing ubuntu 12.04.   I wiped that hdd and installed Xubuntu 12.10 successfully, with GRUB of course installed on that same drive.  I then installed the second hdd containing win7 and updated grub and it recognized win7.  But win7 will not boot properly,  there is an error message saying windows has failed to boot properly, with an option to do startup repair or continute to boot windows normally.   I know from past experience with a second drive containing ubuntu 12.04 that startup repair won't work, and if I choose the option to boot windows normally then I get a white bar saying "windows is loading files"  (which shouldn't happen in a normal win7 boot) and then it reverts back to the grub menu.   Xubuntu 12.10 works fine.  I know from previous experience that installing grub on the drive containing win7 will wreck the os and require reinstalling win7.  I have tried disabling UEFI boot in bios but that did not help.   Any suggestions on how I can get windows 7 to boot properly and work?

---

### Post by oldfred on 2012-11-27
Is Windows in UEFI and Ubuntu in BIOS mode? Both have to be the same.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Paco62 on 2012-11-27
I disabled UEFI boot in the bios setup menu (accessed by tapping the delete key during bootup.  I am not sure but I think this means that it is disabled for all hdd's.   Here is the url for the boot-info report:  [http://paste.ubuntu.com/1392885/](http://paste.ubuntu.com/1392885/)

---

### Post by Paco62 on 2012-11-27
I went into bios setup and changed the boot order so that the first boot device is the hdd containing Xubuntu 12.10 and then did the boot-info again.  Here is the url:  [http://paste.ubuntu.com/1392919/](http://paste.ubuntu.com/1392919/)

---

### Post by oldfred on 2012-11-27
You have Ubuntu in BIOS/MBR mode on sda and Windows in UEFI/gpt on sdb.

Best to delete Ubuntu on sda and convert from msdos(MBR) to gpt and install Ubuntu in UEFI mode. How you boot installer is how it installs, so boot install DVD or flash from UEFI menu.

You also have this issue.

/dev/sdb5 ends after the last sector of /dev/sdb

Windows may not work or many tools in Ubuntu will not see a drive with defective partitions. Not sure about Windows.

Either from liveCD/USB install gdisk from repository or after you install download and install gdisk. Also can be downloaded from gdisk site.
       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)
       
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

    
Ubuntu also has a bug in os-prober that it finds Windows ok, but creates a BIOS boot which does not work in UEFI. Boot-Repair can fix that after you install Ubuntu and get it booting from UEFI. But use gdisk first or it may not find partitions correctly.

Other examples that eventually worked.
       UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by BertN45 on 2012-11-27
When you installed windows 7 it was on the only HDD available. Afterwards you took that drive out and installed Xubuntu and did put the windows drive back as second HDD. Grub uses a chain loader for Windows, so it will start the Windows boot loader and that one still thinks Windows is on the first HDD and fails. So you have to change that in Windows installation (boot.ini?) or you have to re-install Xubuntu or GRUB2, while the Windows HDD is present as first HDD.

EasyBCD a windows boot manager could also be used to create a dual boot or to change boot.ini.

---

### Post by oldfred on 2012-11-27
EasyBCD does not work with UEFI.
       EasyBCD does not work with Windows 8
[http://neosmart.net/forums/showthread.php?t=11135](http://neosmart.net/forums/showthread.php?t=11135)

---

### Post by Paco62 on 2012-11-27
I reinstalled xubuntu 12.04 64 bit, and at the very beginning, chose to boot from the UEFI cd-rom, so presumably this means xubuntu is now also in uefi format.   Now when I try to load windows7 from grub, I get a different error message:  warning invalid efi file, press any key to continue.  I press a key and the grub menu comes back up.  I installed boot-repair again and ran boot-info.  Here is the url:  [http://paste.ubuntu.com/1393116/](http://paste.ubuntu.com/1393116/)
I have not installed gdisk yet.

---

### Post by oldfred on 2012-11-27
Does Ubuntu boot ok? Some have had issues with very large / (root) partitions as some boot files are near start of drive and others near end as yours is (see line 400 of BootInfo report). I often suggest smaller / of 25GB and separate /home or data partiton(s).

Grub2's os-prober creates the BIOS type chain entry. There is a bug report.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

    
But boot repair can create a correct entry and it think it creates a valid entry even for two drives as it searches by UUID or Windows file.

Best to sort out issues with gdisk before using Boot-Repair to fix grub chain entry.

---

### Post by Paco62 on 2012-11-27
Yes, Xubuntu boots and works just fine.   I have installed gdisk now and will try that.

---

### Post by Paco62 on 2012-11-27
I ran gdisk on both hdd's,  here is the result:

marsdenf@marsdenf-G75VW:~$ gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.5

Problem opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo!
marsdenf@marsdenf-G75VW:~$ sudo gdisk /dev/sda
[sudo] password for marsdenf: 
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): ?
b    back up GPT data to a file
c    change a partition's name
d    delete a partition
i    show detailed information on a partition
l    list known partition types
n    add a new partition
o    create a new empty GUID partition table (GPT)
p    print the partition table
q    quit without saving changes
r    recovery and transformation options (experts only)
s    sort partitions
t    change a partition's type code
v    verify disk
w    write table to disk and exit
x    extra functionality (experts only)
?    print this menu

Command (? for help): v

No problems found. 3757 free sectors (1.8 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help): q
marsdenf@marsdenf-G75VW:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Warning! Secondary partition table overlaps the last partition by
370 blocks!
You will need to delete this partition or resize it in another utility.

Command (? for help): 



It looks like the drive with xubuntu is fine,  but i have no idea how to delete the last partition or resize it.

---

### Post by oldfred on 2012-11-27
I was hoping gdisk would auto fix it.

With MBR not many tools open partitions with partition table errors and the author of gdisk wrote one of the few tools used to repair MBR partition tables with errors.

Backup partition table info as explained here:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Try gparted and see if you can shrink the last partition sdb5 by just a bit.

---

### Post by YannBuntu on 2012-11-28
sdb2 seems also damaged:

```
sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

(..)

sdb5: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
```

---

### Post by oldfred on 2012-11-28
@Yann
sdb2 is ok. 
That it the Windows system reserved which has its own gpt partition code. 

I believe it is just like the bios_grub partition in that it is just unformatted space for Windows use. Windows & Windows software in MBR liked to write serial numbers and other data into the sector after the MBR. Just as grub2 did not have a place to write after the MBR as gpt does not have that space, Windows has to have a place to write stuff.  

Microsoft system reserved, bios_grub, and encrypted swap partitions will show as unknown file system as they have to be unformatted space just for the system to write into.

---

### Post by oldfred on 2012-11-28
Another user with similar issue. 

[http://ubuntuforums.org/showthread.php?t=2087057](http://ubuntuforums.org/showthread.php?t=2087057)

@Paco62
What tool did you use to create partitions that ended up with the overlap error?

---

### Post by YannBuntu on 2012-11-28
good to know, thanks fred.

---

