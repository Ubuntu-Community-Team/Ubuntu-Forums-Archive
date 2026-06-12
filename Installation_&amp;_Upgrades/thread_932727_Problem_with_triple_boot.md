---
title: "Problem with triple boot"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by Houchy on 2008-09-28
Hello,

I can't have my grub working in my configuration, I had Ubuntu on a sata disk then I installed on an IDE disk Vista, then XP. But now I cannot launch XP or Vista properly. The Bios now boot on the SATA disk first.
Can anybody help?

Here is my configuration:

Disk IDE
2 partitions:
UUID=88702E5C702E50EC -> ../../**hda1  Vista**
UUID=66509B00509AD661 -> ../../**hda5  WindowXP**

```
Disk /dev/hda: 81.9 GB, 81964302336 bytes - Disk identifier: 0xac68976f
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *        2048    80766967    40382460    7  HPFS/NTFS
/dev/hda2        80774820   160055594    39640387+   f  W95 Ext'd (LBA)
/dev/hda5        80774883   121740569    20482843+   7  HPFS/NTFS
```

Disque SATA
3 partitions
UUID=1171C14E63F3808B -> ../../**sda1  Partage**
UUID=418dbac2-e53c-4379-997b-65e4ed279ad0 -> ../../**sda5 Swap**
UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 -> ../../**sda6 Ubuntu**

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes - Disk identifier: 0x51195119
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   512007614   256003776    7  HPFS/NTFS
/dev/sda3       935802315   976768064    20482875    5  Extended
/dev/sda5       974711745   976768064     1028160   82  Linux swap / Solaris
/dev/sda6       935802441   974711744    19454652   83  Linux
```

So I configured my /boot/grub/menu.lst like this:

```
## default num
default        0

## timeout sec
timeout        7

## hiddenmenu
#hiddenmenu

# Pretty colours
color light-blue/black white/blue

## password ['--md5'] passwd
# command 'lock'
# password topsecret


### BEGIN AUTOMAGIC KERNELS LIST
## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro

## Setup crashdump menu entries
# crashdump=0

## default grub root device
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
# alternative=true

## should update-grub lock alternative automagic boot options
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
# defoptions=quiet splash

## should update-grub lock old automagic boot options
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
# howmany=all

## should update-grub create memtest86 boot option
# memtest86=true

## should update-grub adjust the value of the default booted system
# updatedefaultentry=false

## should update-grub add savedefault to the default options
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=fe298933-90b8-4470-b3e9-be21f2d4a129 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# on /hda1
title        Windows Vista
root        (hd1,0)
makeactive            # cette commande positionne le bit de partition active à 1 (au cas où)
map        (hd0) (hd1)    # hd0 devient hd1
map        (hd1) (hd0)    # hd1 devient hd0 virtuellement
chainloader    +1        # saut au début de la piste suivante car c’est un OS Microsoft(R).

# on /hda5
title        Windows XP
root        (hd1,4)
makeactive            # cette commande positionne le bit de partition active à 1 (au cas où)
map        (hd0) (hd1)    # hd0 devient hd1
map        (hd1) (hd0)    # hd1 devient hd0 virtuellement
chainloader    +1        # saut au début de la piste suivante car c’est un OS Microsoft(R).
```

So with this configuration, when I can boot on Ubuntu, but when I select Vista, WindowsXP is booting, and if I select WindowsXP, I receive the error message:
    > Error 12 : Invalid Device Request

Thank you in advance for your help.

---

### Post by caljohnsmith on 2008-09-28
Try the following entries in your menu.lst and let me know exactly what happens:
```
title        Windows Vista
hide       (hd1,4)
unhide     (hd1,0)
rootnoverify (hd1,0)
makeactive           
map        (hd0) (hd1) 
map        (hd1) (hd0) 
chainloader    +1      

# on /hda5
title        Windows XP
hide       (hd1,0)
unhide     (hd1,4)
rootnoverify (hd1,4)
map        (hd0) (hd1)    
map        (hd1) (hd0)
chainloader    +1
```

---

### Post by Houchy on 2008-09-29
caljohnsmith, thanks a lot for your answer.
I tried exactly what you wrote :

[LIST]
[*]When I select **Vista** in the grub it says "Starting up ...", the Microsoft _Windows XP_ startup screen appears, then after 5 seconds, the computer reboots !!
[*]When I select **Windows XP** in the grub, it says "Starting up ..." and it gets stuck forever, whatever I do.
[/LIST]
I also tried to boot on my IDE disk, and in this case Microsoft Windows XP starts and also reboots after 5 seconds ? ?

Any idea of what is going on?
Thank.

---

### Post by caljohnsmith on 2008-09-29
OK, you've got at least a few issues I think, but I'm fairly certain we can sort them out. For one thing, you are trying to boot Win XP from a logical partition, and although that is possible, it's unfortunately not as straightforward as booting XP from a primary partition. Also, did the Windows XP installer let you install directly to hda5, or did you move it there from another partition? If XP's installer let you use hda5, that means that most likely XP put its boot files in your Vista primary partition hda1. If you had installed Vista after XP, I think things might have been better since Vista would have recognized your XP install. But when you installed XP after Vista, XP does not recognize the Vista install and doesn't deal with it correctly. But that's OK, like I said, I think we can sort this out and get both XP and Vista to boot without resorting to reinstalling either of them. :)

From Ubuntu, let's mount your XP and Vista partitions and see where XP's boot files are:
```
sudo umount /dev/hda1
sudo umount /dev/hsa5
```
Don't worry about any error about not being mounted, the above commands are just to be sure. Then do:
```
sudo mkdir /mnt/hda1 /mnt/hda5
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hda5 /mnt/hda5
ls -l /mnt/hda1
ls -l /mnt/hda2
cat /mnt/hda1/boot.ini
cat /mnt/hda5/boot.ini
```
One of those last cat commands will most likely give you a file not found error, and that's OK. Please post the output of all the above commands, and we'll go from there.

---

### Post by Houchy on 2008-09-29
To answer your first question, the WinXP installer let me install the OS on the extended partition, I didn't move it.

Here is the output to the commands :

```
jack@jack-desktop:/$ ls -l /mnt/hda1
total 1047946
-rwxrwxrwx 1 root root         24 2006-09-18 23:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-09-28 02:10 Boot
-rwxrwxrwx 1 root root        211 2008-09-28 09:17 boot.ini
-rwxrwxrwx 1 root root     333203 2008-04-11 22:43 bootmgr
-rwxrwxrwx 1 root root       8192 2008-09-28 02:10 BOOTSECT.BAK
drwxrwxrwx 1 root root       4096 2008-09-28 09:39 Config.Msi
-rwxrwxrwx 3 root root         10 2006-09-18 23:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 14:00 Documents and Settings
-rwxrwxrwx 1 root root 1070751744 2008-09-28 02:52 hiberfil.sys
-rwxrwxrwx 1 root root          0 2008-09-28 09:23 IO.SYS
-rwxrwxrwx 1 root root        219 2008-09-27 22:03 menu.lst
-rwxrwxrwx 1 root root          0 2008-09-28 09:23 MSDOS.SYS
-rwxrwxrwx 1 root root      47564 2004-08-12 08:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-12 08:00 ntldr
-rwxrwxrwx 2 root root       2731 2008-09-27 22:03 oemcert.xrm-ms
drwxrwxrwx 1 root root          0 2008-09-28 09:44 OEMSettings
drwxrwxrwx 1 root root          0 2008-04-11 23:34 PerfLogs
drwxrwxrwx 1 root root       4096 2008-09-28 01:25 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-28 09:39 Program Files
drwxrwxrwx 1 root root          0 2008-09-28 01:29 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-09-28 04:09 RECYCLER
drwxrwxrwx 1 root root       4096 2008-09-28 09:29 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-28 01:28 Users
drwxrwxrwx 1 root root       4096 2008-09-28 01:56 Vista Activation Dual Boot Method
-rwxrwxrwx 1 root root     166876 2008-09-27 22:03 vstaldr
-rwxrwxrwx 1 root root    1474560 2008-09-27 22:03 vstaldr.img
drwxrwxrwx 1 root root      16384 2008-09-28 02:45 Windows

```
```
jack@jack-desktop:/$ ls -l /mnt/hda5
total 1572912
drwxrwxrwx 1 root root          0 2008-09-28 04:07 ATI
drwxrwxrwx 1 root root       4096 2008-09-28 09:29 Documents and Settings
drwxrwxrwx 1 root root          0 2008-09-28 05:12 MSOCache
-rwxrwxrwx 1 root root 1610612736 2008-09-28 13:56 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-09-28 14:02 Program Files
drwxrwxrwx 1 root root          0 2008-09-28 09:43 RECYCLER
drwxrwxrwx 1 root root       4096 2008-09-28 09:29 System Volume Information
drwxrwxrwx 1 root root      32768 2008-09-28 13:56 WINDOWS

```
```
jack@jack-desktop:/$ cat /mnt/hda1/boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```
```
jack@jack-desktop:/$ cat /mnt/hda5/boot.ini
cat: /mnt/hda5/boot.ini: No such file or directory

```

XP doesn't have a boot.ini ...?
Thanks !

---

### Post by Herman on 2008-09-29
> XP doesn't have a boot.ini ...?:D No, XP doesn't have a boot.ini file because when you set up a dual boot between Microsoft Windows Vista and Windows XP it automatically sets up a 'Microsoft default dual boot', (without warning you).
To understand what a 'Microsoft default dual boot', you should read the following two web sites, 

[Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm")

[Multibooters - Dual/Multi Booting With Vista]("http://www.multibooters.co.uk/").

In short, your Windows XP has copied it's vital boot loader files into Windows Vista, since Windows Vista was already there and in a primary partition.
Windows XP installed itself in a logical partition, and it is only bootable through Windows Vista. (You cannot chainload Windows XP by it's boot sector, because the boot sector is empty and in any case, there are no bootloader files in Windows XP to boot with).

I'm not sure about how to fix your booting problem yet, I'm still thinking about it....
I think you might be able to get XP to boot by editing that boot.ini file in Vista.

I know that Vista depends on the 'disk signature' in the MBR, so maybe try chainloading the MBR of that hard disk instead of chainloading a partition and see if that helps.
```
title        Windows Disk - Vista and XP
root (hd1)
chainloader    +1
```

There is another thread similar to this one here, [COLOR=#980101]****[/COLOR] 			 			[Quadruple Boot, Grub problem]("http://ubuntuforums.org/showthread.php?t=931765").

---

### Post by caljohnsmith on 2008-09-29
Herman, how about we simply have Houchy move his Win XP boot files back to his Win XP partition? His boot.ini file refers to the correct partition, and then we can have him run "fixboot" on his XP partition to make sure it has a bootable boot sector; after that he should be able to boot it with the previous Grub Win XP entry I gave I believe. This is the same method that Meierfra wrote a tutorial about booting Windows XP from a logical partition (you've probably all ready seen it):

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Let's give it a shot, Houchy, as I've helped other people successfully boot Win XP from a logical partition using meierfra's method above. While you have hda1 and hda5 mounted like before, do the following:
```
cd /mnt/hda1
sudo mv boot.ini NTDETECT.COM ntldr /mnt/hda5/
```
Next boot your Win XP install CD, press "r" at the first main menu to use the "recovery console", and then do:
```
map
```
Find your XP drive letter from the above command, and then do:
```
fixboot <drive>
```
Where <drive> is C: or D: or similar. Then reboot, try booting Win XP from the Grub menu, and let us know exactly what happens.

---

### Post by Herman on 2008-09-29
caljohnsmith, 
That should be okay. :D

---

### Post by Houchy on 2008-09-29
My XP CD didn't have Recovery Console in it, so I burnt an XP boot disk to access it. I used [this image file]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). Hope it didn't compromise anything.

So I found the XP partition on drive E: the used the fixboot which seem to work properly.

Not, if I select Windows XP in the grub it says:
```
Starting Up ...
```
and stay frozen.

If I select Vista, I have the following message:
```
Starting Up ...
NTLDR is missing
Press Ctrl+Alt+Del to restart

```

I checked this in case it can help.```

jack@jack-desktop:~$ ls -l /mnt/hda1
total 1047650
-rwxrwxrwx 1 root root         24 2006-09-18 23:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-09-28 02:10 Boot
-rwxrwxrwx 1 root root     333203 2008-04-11 22:43 bootmgr
-rwxrwxrwx 1 root root       8192 2008-09-28 02:10 BOOTSECT.BAK
drwxrwxrwx 1 root root       4096 2008-09-28 09:39 Config.Msi
-rwxrwxrwx 3 root root         10 2006-09-18 23:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 14:00 Documents and Settings
-rwxrwxrwx 1 root root 1070751744 2008-09-28 02:52 hiberfil.sys
-rwxrwxrwx 1 root root          0 2008-09-28 09:23 IO.SYS
-rwxrwxrwx 1 root root        219 2008-09-27 22:03 menu.lst
-rwxrwxrwx 1 root root          0 2008-09-28 09:23 MSDOS.SYS
-rwxrwxrwx 2 root root       2731 2008-09-27 22:03 oemcert.xrm-ms
drwxrwxrwx 1 root root          0 2008-09-28 09:44 OEMSettings
drwxrwxrwx 1 root root          0 2008-04-11 23:34 PerfLogs
drwxrwxrwx 1 root root       4096 2008-09-28 01:25 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-28 09:39 Program Files
drwxrwxrwx 1 root root          0 2008-09-28 01:29 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-09-28 04:09 RECYCLER
drwxrwxrwx 1 root root       4096 2008-09-28 09:29 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-28 01:28 Users
drwxrwxrwx 1 root root       4096 2008-09-28 01:56 Vista Activation Dual Boot Method
-rwxrwxrwx 1 root root     166876 2008-09-27 22:03 vstaldr
-rwxrwxrwx 1 root root    1474560 2008-09-27 22:03 vstaldr.img
drwxrwxrwx 1 root root      16384 2008-09-28 02:45 Windows
```
```

jack@jack-desktop:~$ ls -l /mnt/hda5
total 345
drwxrwx--- 1 root plugdev      0 2008-09-28 04:07 ATI
-rwxrwx--- 1 root plugdev    211 2008-09-28 09:17 boot.ini
drwxrwx--- 1 root plugdev   4096 2008-09-28 09:29 Documents and Settings
drwxrwx--- 1 root plugdev      0 2008-09-28 05:12 MSOCache
-rwxrwx--- 1 root plugdev  47564 2004-08-12 08:00 NTDETECT.COM
-rwxrwx--- 1 root plugdev 250032 2004-08-12 08:00 ntldr
drwxrwx--- 1 root plugdev   8192 2008-09-28 14:02 Program Files
drwxrwx--- 1 root plugdev      0 2008-09-28 09:43 RECYCLER
drwxrwx--- 1 root plugdev   4096 2008-09-28 09:29 System Volume Information
drwxrwx--- 1 root plugdev  32768 2008-09-28 13:56 WINDOWS

```

Thanks again for your help!
Houchy

---

### Post by caljohnsmith on 2008-09-29
OK, I think we're making progress. Do you have your Vista Install/Recovery CD? If not you can download a recovery CD [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Boot that CD, and just do a "Vista Repair". That will probably be all it takes to get Vista working, but if not we can repair it from the command line. Also, once you can boot Vista, you can use "[EasyBCD]("http://neosmart.net/dl.php?id=1")" to modify the Vista boot loader if you need to.

Next thing would be to boot your Windows CD, and this time run:
```
chkdsk /r E:
```
Reboot, and see if that changes anything. If it doesn't, then boot into Ubuntu, enable all your repositories in System > Prefs > Software Sources, and do the following:
```
sudo apt-get install testdisk
sudo testdisk
```
after starting testdisk, choose "no log", choose HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS". 

After you are done doing the "rebuild BS" in testdisk, reboot and let us know what happens.

---

### Post by Houchy on 2008-09-30
Ok, so with my Vista DVD I did the Startup repair but it doesn't seem to change anything?

Boot on XP => "Starting up ..." stay frozen
Boot on Vista => "NTLDR missing. Press ... to reboot"

Then I still tried with WinXP recovery console to execute "Chkdsk E:" but it still didn't change anything.

What's next, Boss? :)
I'm kind of lost now, should I repair Vista with command line? how?

Thanks so much again ...

---

### Post by caljohnsmith on 2008-09-30
Did you run "chkdsk /r E:" or just "chkdsk E:"? You need to run "chkdsk /r E:" for chkdsk to actually fix any errors. So if you haven't done that on your Win XP partition, be sure to do it now.

About Vista, boot your Vista Recovery CD, go to the command line, and run:
```
bootrec /fixboot
```
And also run chkdsk on your Vista partition just to make sure:
```
chkdsk /r C:
```
I'm assuming above Vista is on the C drive, but you can use the "map" command like before to know for sure. 

Next follow the directions from my previous post about using testdisk to "Rebuild BS" for the XP partition. We might have to do the same for Vista, but first do the above steps for Vista and report what happens when you try and boot again.

---

### Post by Houchy on 2008-09-30
I confirm I did execute "chkdsk /r E:".

I did the "bootrec /fixboot" with Vista Recovery CD

Then I did "chkdsk /r E:" then "chkdsk /r C:" with XP Recovery CD.

Now:
- Boot on Vista is working (I just can't see XP partition) !
- Boot on XP still frozen after "Starting Up ..."

Then I did the testdisk ...Rebuild BS for XP partition and I got some weird message, not sure it was an error message, but something saying boot sectors were different ???

I did the testdisk a second time and I got the following message:
```
Disk /dev/hda - 81 GB / 76 GiB - CHS 158816 16 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS          80133  13  1 120774   5 63   40965687 [Windows XP]

Boot sector
Warning: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
Status: OK

Backup boot sector
Warning: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
Status: OK

Sectors are identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.

```

I did a reboot ... same thing.
I notice that in testdisk, the size of the WinXP partition is not correct, it gives the size of the extended partition that contains WinXP ...

---

### Post by caljohnsmith on 2008-09-30
I don't think you have to worry about the "Incorrect number of heads/cylinder" errors at least yet, because I'm pretty sure that just means you used Windows software to set up the Windows partitions originally; linux always uses 255 heads/cylinder geometry, but I believe some Windows partitioning tools use different geometry numbers. I don't know the nitty-gritty technical details of it all, but I don't think that error is something to be concerned about yet. Maybe someone else can jump in and educate us about the exact differences. :)
> **Houchy said:**
> I notice that in testdisk, the size of the WinXP partition is not correct, it gives the size of the extended partition that contains WinXP ...
That sounds strange, how about posting the full output of:
```
sudo fdisk -l

```
And also run testdisk again, but this time to check your partition table:
```
sudo testdisk
```
Choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the full output of that screen.

---

### Post by Houchy on 2008-10-01
```
jack@jack-desktop:~$ sudo fdisk -l
[sudo] password for jack: 

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac68976f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5028    40382460   17  Hidden HPFS/NTFS
/dev/hda2            5029        9963    39640387+   f  W95 Ext'd (LBA)
/dev/hda5            5029        7578    20482843+   7  HPFS/NTFS

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51195119

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31871   256003776    7  HPFS/NTFS
/dev/sda3           58252       60801    20482875    5  Extended
/dev/sda5           60674       60801     1028160   82  Linux swap / Solaris
/dev/sda6           58252       60673    19454652   83  Linux

Partition table entries are not in disk order

```

Analysis of the partition table with testdisk:
```
Disk /dev/hda - 81 GB / 76 GiB - CHS 158816 16 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
 1 * hid. HPFS/NTFS           2   0 33 80125  15 23   80764920 [Vista]

Warning: Bad starting head (CHS and LBA don't match)
 2 E extended LBA         80133  12  1 158785   4 63   79280775

Warning: Bad starting head (CHS and LBA don't match)
Warning: Incorrect number of heads/cylinder 255 (NTFS) != 16 (HD)
 5 L HPFS - NTFS          80133  13  1 120774   5 63   40965687 [Windows XP]

Warning: Bad starting head (CHS and LBA don't match)



*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted

```

Then I clicked on Proceed
```
Disk /dev/hda - 81 GB / 76 GiB - CHS 158816 16 63

Warning: the current number of heads per cylinder is 16
but the correct value may be 32.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

```

Thanks for your help!!

---

### Post by caljohnsmith on 2008-10-01
It's possible your partition table may be messed up, or it could be that testdisk just isn't dealing with your HDD's geometry correctly; I'm not experienced with these kind of geometry errors in testdisk, so I really don't know at this point. How about producing a log file with testdisk and attaching it to your next post; that way I can send the log file to a few of my friends who know more about testdisk, and maybe they can help resolve what is going on. So run testdisk again from your desktop, but this time use testdisk's deeper search feature:
```

cd ~/Desktop
sudo testdisk
```
Select "create log" and testdisk should create a log file on your desktop; then select HDD and "proceed", "Intel", "Analyze", then "proceed", Y to search for Vista partitions, hit enter, and select "search!" so it does a deeper search which could take a while. Once it shows your partitions, select each partition and press "p" to list the root directory of that partition. Once you are finished listing the contents of all found partitions, exit testdisk. Please attach the testdisk log from your desktop to your next post.

EDIT: I just realized, I don't think testdisk can list the files in an NTFS partition, so if testdisk errors when you try that, just skip that part.

---

### Post by meierfra. on 2008-10-01
> Then I did the testdisk ...Rebuild BS for XP partition and I got some weird message, not sure it was an error message, 

One always gets that message. It is not an error message. Did you choose  "write"  at the testdisk  menu after "rebuild BS"?  If not I suggest to run "testdisk rebuild BS" again and then "write" the changes to the boot sector.

---

### Post by Houchy on 2008-10-01
Hello,

I did what you asked me but when I tried to list the files from my 1st Vista partition, there was a Segmentation Fault ...

The file testdisk.log should be in attachment.

ps: to begin with I never wanted to install XP on an extended partition, it's not necessary to my because I just need 3 partition that can all be primary. I don't know what happened during the XP install but I ended up with this extended partition. So if I reinstall XP making sure I install it on a primary partition, will there be a quick way to fix the situation?

Thanks again for all the effort ...

---

### Post by caljohnsmith on 2008-10-01
Well, reinstalling might be a quick fix for the situation like you say, but I think we are close to getting your XP working. When you did the "rebuild BS" with testdisk, did you actually write the boot sector like meierfra said in his post? I guess I should have been more clear about that. Don't worry about that error you got, go ahead and write the boot sector, reboot, and let us know what happens when you try and boot XP. :)

---

### Post by Houchy on 2008-10-01
That was more than close :)

It is working!! oh my god, I'm so relieved! :)

Thank you so much for your great job, and sorry for loosing s)

There's just one little thing left. In XP I cannot access the Vista drive and vice versa. Is it due to the hide command in the grub? is there an easy fix to this? if not it's ok, I guess like me you have other things to do ...

[I]Just for curiosity ... how much time do you spend helping people in this kind of forum? I mean that's great to have people like you helping but ... you're probably far from getting back as much as you're giving ... what's your main motivation?

[/I]

---

### Post by caljohnsmith on 2008-10-01
That's great news your Windows XP is booting now. :) It shouldn't be necessary any more to use the "hide" and "unhide" commands in Grub's menu entries for both Vista and XP; that was mainly for troubleshooting purposes to make sure they were entirely independent of each other when booting them. And like you suspected, that is what is keeping them from accessing each other. So go ahead and remove the "hide" and "unhide" lines in both of their Grub entries, and also do:
```
sudo fdisk -l
```
Either hda1 or hda5 will probably say "hidden NTFS" instead of "NTFS", so then do:
```
sudo grub
```
And if hda1 is "hidden NTFS" do:
```
grub> unhide (hd0,0) 
``` 
Or if hda5 is the hidden partition do:
```
grub> unhide (hd0,4)
```
That way both of them should be back to normal, and you should be able to access your files from either partition.
[QUOTE=Houchy]
Just for curiosity ... how much time do you spend helping people in this kind of forum? I mean that's great to have people like you helping but ... you're probably far from getting back as much as you're giving ... what's your main motivation?[/QUOTE]
Well, due to certain medical problems that recently came up in my life, I've been sidelined from my career for a while; because I like Ubuntu and have an interest in this kind of stuff, I try to help out in the forums here when I can now. I enjoy it most of the time, especially when I meet people like you, but sometimes it is a thankless job helping others who don't have any appreciation for anyone who helps them out, including someone who gives them free technical help. I mean I never expect anything, but I lose my motivation helping people who can't even express a simple thank you after I spend a long time helping them solve their problem. But the Ubuntu forums are far better about this than any of the other linux forums I've visited. 

Anyway, I'm glad you can use all your OSes now, and I'm glad I could help out. Cheers, and I hope to see you around the forums in the future. :)

---

### Post by Houchy on 2008-10-01
One more time it worked like a charm! :)
Thank you so much for all that you did, I really appreciate it. That was a pleasure to deal with you.

Hope to see you around anytime soon and who knows, maybe one I can help you too :)

Cheers from France!

---

