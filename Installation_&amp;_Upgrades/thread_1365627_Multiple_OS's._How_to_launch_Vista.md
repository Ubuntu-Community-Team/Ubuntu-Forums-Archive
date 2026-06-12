---
title: "Multiple OS's. How to launch Vista?"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by Makavcio on 2009-12-27
[LEFT]Hello,

I'm new to Ubuntu and I'm new here so please be patient dealing with my probably trivial problems :] 

I'll start from the begining. 
I had winXP on hdd(1)*, data on hdd(2) and winVista on hdd(3) which was instaled as an addition to xp. I was able to choose which system to boot up via a menu which was displayed every time my pc was starting.
Now i decidedt   remove XP, rearange partitions on hdd(1) and intall in its place Ubuntu 9.04 (downloading updates atm). So i cleaned hdd(1), made myself new partitions and started with installation of linux. Unforunately i was unable to choose installation option to set up multiple systems as installator informed me that there are no other operation systems on my pc. I decided to forget about my partitions and chosen to install ubuntu on athe whole hdd(1). Advanced instalation has proven to be too complicated for me so I used the option specified above as a safe choice.

Installation went smooth but I am unable to boot up Vista now. I've tried changing priorities of hdds but my hdd(3) seems not to be bootable. It seems that files needed to choose system were stored on hdd(1).

My question is simple: how to start Vista?
There's a lot of vital software I must use in my work. Reinstalling it all on a fresh Vista installation, activating it etc would take at least two weeks and would most likely cost me a nice sum of money... Help?

[/LEFT]
Is it possible to create a similar menu that I could choose my OS with to that created byXP? It would be perfect :]


*numbers are used keep track of my discs, it's not a formal numeration of any kind.

---

### Post by oldfred on 2009-12-27
When you uninstalled XP you also uninstalled your Vista startup.

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.


You can repair your Vista and since it is on a separate drive I would change that drive to be the boot drive and use the Vista repair to fix Vista. It will install its boot loader to that drive which is fine. You then can switch drive order to boot Ubuntu again. Those with one drive have to do the reinstall grub problem after fixing Vista.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After you get Vista to boot ok and then switch drive order. In Ubuntu run this and it should find your Vista install and add it to the grub menu.

sudo update-grub

---

### Post by Makavcio on 2009-12-27
> **oldfred said:**
> When you uninstalled XP you also uninstalled your Vista startup.

Yeah, I figured that out :]


> **oldfred said:**
> 
Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

In progress. 
Thee is a problem because for some reason NTFS partitions are being accessed horribly slow. Is that a compatibility issue?

> **oldfred said:**
> 
You can repair your Vista and since it is on a separate drive I would change that drive to be the boot drive and use the Vista repair to fix Vista. It will install its boot loader to that drive which is fine. You then can switch drive order to boot Ubuntu again. Those with one drive have to do the reinstall grub problem after fixing Vista.
Trying to repair Vista via its repair mechanism built in its installer (on DVD) was one of the first things i have tried. Unfortunately Vistas installer, as it was with Ubuntu, does not find any operating system and thus it does nothing.
Full repair (which could be also called a "fresh installation over the previous one") is not an option because it would destroy all my software licences etc.

> **oldfred said:**
> If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Fortunately, I'm a MSDN:AA participant and I have several XPs and Vistas at my disposal ;) Maybe I should be telling it to you now but if I had W7 here already I would be posting at W7 forum now ;) But now I'll try Ubuntu for a little why at least. 


> **oldfred said:**
> How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You aree better than Santa ;)

Thank you!

Will let you know when problem's fixed.

---

### Post by Makavcio on 2009-12-27
Unfortunately the problem wasn't fixed. 
bootrec.exe doesn't seem to be able to create it's own loader - it only fixes errors that prevent the existing loader to properly start Vista. /fixboot and rebuildBCD returned "element not found" error. /fixmbr fixed Master Boot Record somehow but it did not seem to have any effect at all. /scanOS found my installation at D:\WINDOWS (it used to be F:\ :] )

My BootMgr folder was destroyed altogether with the whole disc. I was able to recover it when I was attempting to unerase boot.ini but now all the data must have been already overwritten beyond repair by several full formats and Ubuntu instalations.
And I'm not capable of recovering anything >100kB from my freeware bootcd... 
I'll try to find something that would work on linux. Scannig takes at least 2 hours :] Lovely :]

I think that I would need to create a whole new BootMgr somehow :]

---

### Post by raymondh on 2009-12-27
> **Makavcio said:**
> [LEFT]Hello,

I'm new to Ubuntu and I'm new here so please be patient dealing with my probably trivial problems :] 

I'll start from the begining. 
I had winXP on hdd(1)*, data on hdd(2) and winVista on hdd(3) which was instaled as an addition to xp. I was able to choose which system to boot up via a menu which was displayed every time my pc was starting.
Now i decidedt   remove XP, rearange partitions on hdd(1) and intall in its place Ubuntu 9.04 (downloading updates atm). So i cleaned hdd(1), made myself new partitions and started with installation of linux. Unforunately i was unable to choose installation option to set up multiple systems as installator informed me that there are no other operation systems on my pc. I decided to forget about my partitions and chosen to install ubuntu on athe whole hdd(1). Advanced instalation has proven to be too complicated for me so I used the option specified above as a safe choice.

Installation went smooth but I am unable to boot up Vista now. I've tried changing priorities of hdds but my hdd(3) seems not to be bootable. It seems that files needed to choose system were stored on hdd(1).

My question is simple: how to start Vista?
There's a lot of vital software I must use in my work. Reinstalling it all on a fresh Vista installation, activating it etc would take at least two weeks and would most likely cost me a nice sum of money... Help?

[/LEFT]
Is it possible to create a similar menu that I could choose my OS with to that created byXP? It would be perfect :]


*numbers are used keep track of my discs, it's not a formal numeration of any kind.

In Ubuntu .... kindly access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

Small L.  Paste results in your next post.

We may just have to chainload Vista.  Also, set hdd1 as first to boot in BIOS.

Lastly, open a terminal and type

gksudo gedit /boot/grub/menu.lst

Copy/paste that in your next post as well.

Regards,

---

### Post by oldfred on 2009-12-27
Take a look at this post on repairing Vista.

meierfra.
[http://ubuntuforums.org/showthread.php?t=1350824](http://ubuntuforums.org/showthread.php?t=1350824)   post 10 on repair of Vista
I agree. But I recommend to use testdisk to fix your boot sector. (Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

When you changed partitions in XP you could edit boot.ini to fix it. Can you edit BCD which now holds that type of info? I only have XP so I do not know.

---

### Post by Makavcio on 2009-12-27
[FONT=monospace]COMMAND 1:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82949ef5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sda5               2       19124   153605466    7  HPFS/NTFS
/dev/sda6           19125       38913   158955111    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b01b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23330   187398193+  83  Linux
/dev/sdb2           23331       24321     7960207+   5  Extended
/dev/sdb5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82949ef4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdc5               2       38913   312560608+   7  HPFS/NTFS


COMMAND 2:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=67719248-efd4-4f9b-b28d-8194c8659b82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=67719248-efd4-4f9b-b28d-8194c8659b82

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        67719248-efd4-4f9b-b28d-8194c8659b82
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=67719248-efd4-4f9b-b28d-8194c8659b82 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        67719248-efd4-4f9b-b28d-8194c8659b82
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=67719248-efd4-4f9b-b28d-8194c8659b82 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
uuid        67719248-efd4-4f9b-b28d-8194c8659b82
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=67719248-efd4-4f9b-b28d-8194c8659b82 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
uuid        67719248-efd4-4f9b-b28d-8194c8659b82
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=67719248-efd4-4f9b-b28d-8194c8659b82 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, memtest86+
uuid        67719248-efd4-4f9b-b28d-8194c8659b82
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


PERSONAL ANNOUNCEMENT: SPAM FTW!


Will change boot priority in a moment.



And I Believe that my BCD what's the main reason it cannot be fixed. One cannot fix something that doesnt exist anymore :]

Btw, when I'll manage to start Vista, I believe that configuring grub for my needs will not be a problem. I just need to start that bloody OS :]


EDIT:
Tried to install testdisk. Found a funny, 5-kilometer-long command, pasted it in terminal, got "access denied" error... Somebody end my misery... 
[/FONT]

---

### Post by oldfred on 2009-12-27
More ways to repair BCD:

[http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391)

---

### Post by Makavcio on 2009-12-27
All these solutions (and i tried many more too) require that I specify which system I want to repair on the system list in System Repair. I have nothing listed there...

---

### Post by oldfred on 2009-12-27
Is the boot flag set on your Vista partition? Windows seems to require that. It was on your XP partition before you deleted it and that was why it booted that.

---

### Post by Makavcio on 2009-12-27
Not sure if I understand you.

A disk utility I used before (Partition Magic as far as i remember its name) stated that the partition with vista is not bootable (boot record: no). In BIOS, my settings demand that the 1st boot device should be hdd. Submenu determines priority of hdds: the one with vista -> the one with data -> the one with ubuntu.

Btw, all my partitions, the one with vista too, are "logical, extended" and none of them are "primary". It was never an issue as i were booting up systems from non-primary partitions. Can it be causing troubles? Is there a way to change it without loosing data?

Btw mkII, "bcdedit /enum" all returned an error: "The boot configuration data store could not be found. The requested system device canot be found". I had high hope with this procedure from your previous nick as it seemed to be creating new boot info basing on info from win/sys32 but it seems again that it ~"cannot create something that doesnt exist" :]


EDIT
I've got an idea but i dont know how to make it happen. From wiki:
"**winload.exe** is the operating system [boot loader]("http://en.wikipedia.org/wiki/Booting"). It is invoked by the **Windows Boot Manager** in order to load the operating system kernel ([ntoskrnl.exe]("http://en.wikipedia.org/wiki/Ntoskrnl.exe")) and (boot-class) device drivers,[[1]]("http://en.wikipedia.org/wiki/Boot_Configuration_Data#cite_note-BCDIWV-0") and is in that respect functionally equivalent to (the operating system loader functionality of) [NTLDR]("http://en.wikipedia.org/wiki/NTLDR") in prior versions of Windows NT."
So we just need to tell bios to run winload.exe, aren't we?


It's 3am in Poland. Time to get some sleep :] Thans for your help. If you'd have any more ideas plz put them down here. Good night.

---

### Post by oldfred on 2009-12-27
You need the boot flag for windows to find the windows partition and you need to only have one partition per drive with the boot flag, Ubuntu does not use it but it is essential for windows:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

fdisk -l   (lowercase el)   will show you flag as *
You  can set it with gparted or:

    #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-


I just noticed that you have windows partitions as sda5 and sda6. I hope one of these are not your Vista install. Windows will allow an install into an extended partition as long as the boot files (your old XP) are in a primary partition. Windows just about is impossible to boot from an extended partition. Most of the workarounds are based on an install of a primary partition with the boot files.

---

### Post by Makavcio on 2009-12-28
My vista was installed on an extended partition. Disk tools inform me that it's impossible to convert it to system partition without loosing all data...

I have a very last idea to boot vista up.
All commands used in vista's restore were trying to access MBR and boot files but were unable to locate them and later, to create new ones. It seems that vista was unable to find a primary partition to perform this operation. Linux installation has changed my hdd(1) and altogether with altering file system it could remove the needed properties.

I'll format my hdd(1) to contain a ntfs primary partition using vista's partition tools from installation dvd. Then I'll try to use recovery again and hopefully all boot files will be recreated.

If it helps, I'll create myself a tiny boot partition on hdd(1) which will be easy to backup using tools like norton ghost. Unfortunately i was unable to backup my old settings because to damage done by Partition Magic to my hdd(1) (wrong start sector of the disk - fixed it but lost all the data -> it was the main reason of cleaning up taht disk).

If I succeed I'll post here in a separate post a "problem -> solution" info for others who might encounter similar problems.

Cheers

---

### Post by oldfred on 2009-12-28
You can copy partitions with gparted and with dd which does a low level copy. I do not know if Vista would still work if it was moved.

I also saw a post where caljohnsmith totally rewrote the partition table with the command line and a text file. It was still within the 4 partition rules but he changed a partition from the extended into a primary.

---

