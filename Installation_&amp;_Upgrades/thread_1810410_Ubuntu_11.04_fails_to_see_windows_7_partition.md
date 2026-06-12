---
title: "Ubuntu 11.04 fails to see windows 7 partition"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by Bob Bobbio on 2011-07-23
I've installed windows 7 on my computer, leaving enough room to install ubuntu in the unallocated space, but when I boot up into the ubuntu live cd, it shows my whole hard drive as unallocated space, and doesn't show the windows 7 partition at all.  I really want to dual-boot ubuntu, but I don't know what to do.  I looked at some other threads, and tried using EasyBCD to write the MBR, but it didn't do anything.  Thank you.

---

### Post by Quackers on 2011-07-23
Does Windows boot up ok? 
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2011-07-23
> **Bob Bobbio said:**
>  ...and tried using EasyBCD to write the MBR, but it didn't do anything.  Thank you.

Don't mess with EasyBCD -- it's not going to help you, and you run the risk of damaging the existing Win7 boot stuff in the process.

IF you really Do want to dual-boot your PC, then BEFORE you do anything else, boot into Win7, invoke the Backup function, and use the feature to create and burn a Win7 Repair CD.  This will be necessary later, should you need to repair your Win7 boot loader from the dual-boot setup.

---

### Post by Bob Bobbio on 2011-07-23
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   266,242,047   266,035,200   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        8EAEE6F0AEE6D02F                       ntfs       System Reserved
/dev/sda2        5E22F4AE22F48BF1                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)



```

The results of the boot script seem to be correct, I was thinking now though, that perhaps it has to do with the fact that this hard drive was taken from an old iMac, and that somehow gparted is looking for the partition table in the firmware, and it doesn't exist, I'm not sure about how this works at all.  Thank you so much for your reply, I'm really lost on this one.  Also thanks for the advice about EastBCD, I really wasn't sure what I was doing there.

---

### Post by Quackers on 2011-07-23
Yes
```
GUID Partition Table detected, but does not seem to be used
``` would be explained by the fact that it came from a Mac.
I am not experienced in GPT, though I have seen posts on the subject. It may be just a mtter of deleting the GPT data.
Have a search for recent posts by forum user srs5694 as he has posted several times recently with regard to this issue. Just make sure that the thread you are looking at has your specific problem before you do anything!

---

### Post by Quackers on 2011-07-23
In fact look at the last post in this thread. I can vouch for the Fixparts programme, written by srs5694. It works wonders :-)

[http://ubuntuforums.org/showthread.php?t=1772936&page=2](http://ubuntuforums.org/showthread.php?t=1772936&page=2)

---

### Post by sk3499 on 2011-07-23
> **Quackers said:**
> In fact look at the last post in this thread. I can vouch for the Fixparts programme, written by srs5694. It works wonders :-)

[http://ubuntuforums.org/showthread.php?t=1772936&page=2](http://ubuntuforums.org/showthread.php?t=1772936&page=2)

I'm having the same problem with a GPT disk, except my partition table is fine, and ubuntu sees it as GPT. Grub 2 doesn't seem to see win 7 partition by itself, but the boot script shows this:

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe


How do i point grub2 at sda3 to see windows 7?

---

### Post by Bob Bobbio on 2011-07-23
Thank you so much Quackers! The advice you gave me worked like a charm. Fixparts (link for reference [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)) totally fixed it, I partitioned and Ubuntu is installing right now.

---

### Post by sk3499 on 2011-07-23
Ive tried editing the grub.cfg (using the scripts) to add:

insmod part_gpt
insmod ntfs
set root='(/dev/sda,gpt3)'

for the windows 7 booting.

When I try to boot with grub2, I don't get 'no such partition' anymore, I get 'no such disk', but /dev/sda is what the other options have in set root. gpt3 is where windows is located....

Anyone know why this isn't working, or how to fix it?

---

### Post by Quackers on 2011-07-24
Bob Bobbio, you're welcome and I'm glad it worked :-)

sk3499 the sda3 partition you show is missing 2 Windows boot files (bootmgr and /Boot/BCD) so grub will not find that partition. Those 2 files could be in a different partition (like sda1). Check the boot script, or post it here.

---

### Post by sk3499 on 2011-07-24
here is the sda output from the script:

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       118606544 sectors, but according to the info from 
                       fdisk, it has 1192348379 sectors.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 733008604. But according to the info from 
                       fdisk, sda7 starts at sector 1806750428. According to 
                       the info in the boot sector, sda7 has 0 sectors.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 733047667. But according to the info from 
                       fdisk, sda8 starts at sector 1806789491. According to 
                       the info in the boot sector, sda8 has 0 sectors.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

...

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   614,402,047   613,933,056 Data partition (Windows/Linux)
/dev/sda4     614,402,048 1,806,750,427 1,192,348,380 Data partition (Windows/Linux)
/dev/sda5   2,209,224,704 2,629,066,751   419,842,048 Data partition (Windows/Linux)
/dev/sda6   2,629,066,752 2,639,306,751    10,240,000 Swap partition (Linux)
/dev/sda7   1,806,750,428 1,806,789,490        39,063 EFI System partition
/dev/sda8   1,806,789,491 1,806,828,553        39,063 EFI System partition
/dev/sda9   2,192,482,851 2,209,224,703    16,741,853 Swap partition (Linux)
/dev/sda10  1,806,828,554 2,175,742,616   368,914,063 Data partition (Windows/Linux)
/dev/sda11  2,175,742,617 2,192,482,850    16,740,234 Swap partition (Linux)






I don't see the files you specified listed, can I fix that with the windows boot recovery on the windows install CD?

---

### Post by Quackers on 2011-07-24
They could be in sda2, which is not mounting. That can sometimes happen with system reserved partitions. It's not necessarily a bad thing.
I am not the person to ask with regard to booting GPT systems. I could do more damage than good. Hopefully someone with some GPT experience will see your request.
I would say though, that you may be better off with a thread of your own, with someting about GPT or EFI in the title. You could explain exactly what has happened, what you have done about it and you can include the full output of your boot script in code tags.
This may bring you more specific help.

---

### Post by srs5694 on 2011-07-24
Sk3499, first, it's best to start your own thread to resolve your own problem rather than "hijack" another thread, since discussing two problems in one thread gets very confusing very quickly and can actually slow down resolution of both problems. I'll reply here only because Bob Bobbio's problem seems to have been resolved. In the future, though, please start new threads rather than add your problem to an existing one.

It appears that you've got a computer with UEFI firmware that's booting in UEFI mode. This throws out all the usual rules for booting a computer, and my guess is that Ubuntu's GRUB OS-detection scripts don't know how to add Windows in this case. You should be able to get it to work with an entry like this:

```

menuentry "Windows x86_64 UEFI-GPT" {
   search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
   chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```

You can add this directly to your /boot/grub/grub.cfg file for testing purposes; however, Ubuntu's GRUB scripts will wipe out that change the next time they're called (such as when your kernel is next updated). A better long-term solution is to add those lines to /etc/grub.d/40_custom and then run update-grub to generate a new grub.cfg with these changes.

One other word of warning: On UEFI systems, Ubuntu's package system sometimes tries to replace grub-efi (which you've presumably got now) with grub-pc (which is the version of GRUB for BIOS systems). ***Don't let it do so!!!!!*** There's [another current thread](http://ubuntuforums.org/showthread.php?t=1805759) in which somebody's system has stopped booting, apparently because of such an "upgrade."

---

### Post by Quackers on 2011-07-24
Now that's a man to listen to :-)
Thanks, as always for your input srs5694!

---

### Post by sk3499 on 2011-07-24
> **srs5694 said:**
> Sk3499, first, it's best to start your own thread to resolve your own problem rather than "hijack" another thread, since discussing two problems in one thread gets very confusing very quickly and can actually slow down resolution of both problems. I'll reply here only because Bob Bobbio's problem seems to have been resolved. In the future, though, please start new threads rather than add your problem to an existing one.

It appears that you've got a computer with UEFI firmware that's booting in UEFI mode. This throws out all the usual rules for booting a computer, and my guess is that Ubuntu's GRUB OS-detection scripts don't know how to add Windows in this case. You should be able to get it to work with an entry like this:

```

menuentry "Windows x86_64 UEFI-GPT" {
   search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
   chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

```You can add this directly to your /boot/grub/grub.cfg file for testing purposes; however, Ubuntu's GRUB scripts will wipe out that change the next time they're called (such as when your kernel is next updated). A better long-term solution is to add those lines to /etc/grub.d/40_custom and then run update-grub to generate a new grub.cfg with these changes.

One other word of warning: On UEFI systems, Ubuntu's package system sometimes tries to replace grub-efi (which you've presumably got now) with grub-pc (which is the version of GRUB for BIOS systems). ***Don't let it do so!!!!!*** There's [another current thread]("http://ubuntuforums.org/showthread.php?t=1805759") in which somebody's system has stopped booting, apparently because of such an "upgrade."

I tried what you suggested... didn't work. Grub2 just sits there with a blank maroon screen when I select the 'Windows x86_64 ...' option.

Any other ideas?

Also, how do I know if it is using grub-efi?

---

### Post by sk3499 on 2011-07-24
ok im going to start a new thread

---

