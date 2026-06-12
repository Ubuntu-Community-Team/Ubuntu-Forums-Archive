---
title: "Installation Completes, then System Crashes"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by SilentLucidity on 2010-12-05
During the last 2 weeks i am trying to install a Linux Distribution. I have followed the procedure stated in ubuntu.com using a live usb, then a liveCD etc. Then (after lots of formats and re-installations of win7) i followed installation guides found in forums such as this [this]("http://forum.ubuntu-gr.org") and [this]("foss.ntua.gr"). The most common procedure followed can be described as: Installing win 7, booting from live CD, creating partitions with GParted, installing ubuntu in the correct partition. Always, after the installation the system reboots and then, after the list of devices it hangs to a black screen and a white cersor (_). The only difference occured was in the Debian Distribution, when the system hanged at "Loading GRUB. "
Repairing GRUB from live CD and from Debian Installation CD didn't work. The community foss.ntua.gr did not come to a conclusion about what my problem was after trying Ubuntu x64, Ubuntu x32 and Debian x64. I have also tryed with Fedora 14, which had the same problem as ubuntu. 
So i write here as my last chance of getting any solutions. 
Thank you in advance everyone. 

Sincerely Grateful for your time, Panagiotis

---

### Post by Quackers on 2010-12-05
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by davidmohammed on 2010-12-05
nvidia graphics?

assuming you have ubuntu correctly installed, have you tried booting with the "nomodeset" grub option?

n.b. - when booting, press shift to display your kernels in grub.  Press e to edit.  find the line ending quiet splash --

change the line to read

nomodeset quiet splash --

CTRL +X to boot.

---

### Post by SilentLucidity on 2010-12-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0A66F23D66F228D9                       ntfs       System Reserved               
/dev/sda2        9098F71198F6F516                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```

When in black screen and cursor, nothing works, neither shift nor e nothing. And after some clicks on the keyboard, it starts beeping with every extra stroke.

---

### Post by Quackers on 2010-12-05
So now you just have Windows 7 installed. No Linux system at all. Does Windows boot ok?

---

### Post by SilentLucidity on 2010-12-05
Yes. Windows 7 boots fine. How can i get rid of the extra partition? Is there a way? Do you want me to re-install some distribution of linux? (I have access to ubuntu 10.10 x32, x64 and fedora 14 x32 at the moment) Do you have any clues about what my problem might be? 

This is how my computer was as of 16/11 ```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2d7d

  
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       13080   104960000    7  HPFS/NTFS
/dev/sda3           13080       26141   104907777    5  Extended
/dev/sda4           26141       60802   278414336    7  HPFS/NTFS
/dev/sda5           13080       25382    98816000   83  Linux
/dev/sda6           25383       26141     6090752   82  Linux swap / Solaris 
```

---

### Post by Quackers on 2010-12-05
What do you mean by "the extra partition"? This is a normal(ish) installation for Windows 7. In oem installs it insists on creating a separate boot partition with just 2 of its boot files in it (sda1).
When booted in to Windows can you go to the Disk Management console and post a screenshot of that window please?

---

### Post by SilentLucidity on 2010-12-05
[IMG]http://i224.photobucket.com/albums/dd233/abstr2ct/diskmanager.png[/IMG]

---

### Post by Quackers on 2010-12-05
Thanks for that.
Your current C: drive takes up the whole disc. In order to make space for another operating system it will be necessary to resize that partition. This will create unallocated space which Ubuntu (or whatever) can use.
Please right-click on the C: drive in the disk management window and select "shrink" from the context menu.
This will display a small window giving details of how much the C: drive can be shrunk by. Choose the required amount of shrinkage and click OK.

Please note!
It is highly recommended that the Windows system be defragged as least once before shrinking!!!
It is also recommended that after shrinking you boot into Windows a couple of times to make sure all went well!

If all goes well you will now have free space for another operating system to use.

---

### Post by SilentLucidity on 2010-12-05
I usually make that space with GParted. Does it make any difference?

---

### Post by Quackers on 2010-12-05
Yes, it can do.
Windows systems should be resized by Windows programmes. It's safer and it's easier, and it's quicker.

---

### Post by SilentLucidity on 2010-12-05
[IMG]http://i224.photobucket.com/albums/dd233/abstr2ct/diskmanager-1.png[/IMG] this is my new diskmanager view. What should i do next (after the backup which is being done now)?

---

### Post by Quackers on 2010-12-05
Now you can install another operating system into that free space.
If it's Ubuntu run the Live cd/usb and either install into that free space in total or set up partitions manually, as you wish.

---

### Post by SilentLucidity on 2010-12-05
Backing up my files will take another hour. What are my chances of succeeding? :P

---

### Post by Quackers on 2010-12-05
Excellent, would be my estimation :-)
If you get stuck anywhere during installation or partitioning I will be here for a while yet. There are others though who can offer perfectly good advice too :-) Several others!

---

### Post by SilentLucidity on 2010-12-05
Thank you so much for your time :D
I still am a little suspicious for it working, it didn't work even when i set it to use the entire disk (neither ubuntu, nor debian or fedora) Time will tell i guess :P

---

