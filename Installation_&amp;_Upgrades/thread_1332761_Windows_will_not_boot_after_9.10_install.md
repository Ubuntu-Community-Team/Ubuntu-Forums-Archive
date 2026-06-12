---
title: "Windows will not boot after 9.10 install"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2009-11-20
Windows XP will not boot after fresh install of 9.10 64 bit with ext4. Windows boot screen appears then a fast BSOD then reboots.
 

 The entry in grub.cfg lists the Windows drive as (hd0,1) which seems incorrect with the fdisk info since there is only one partition on that drive. I manually edited in the grub boot screen to be (hd0,0) which does not work.
 

 Any ideas?
 

 Info below.
 

 sudo blkid 
```
/dev/sda1: UUID="778B551D5531B577" LABEL="sda" TYPE="ntfs"  
 /dev/sdb1: LABEL="sdb1" UUID="dab0a554-b49f-443b-be34-415902bc5fc3" TYPE="ext4"  
 /dev/sdb2: LABEL="sdb2" UUID="455628ea-a4a4-4cc9-a5ff-cacea6adfad0" TYPE="ext4"

``` 

 fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x000121d5 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       19457   156288321    7  HPFS/NTFS 

``` 

 GRUB2 Windows entry:
```
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" { 
     insmod ntfs 
     set root=(hd0,1) 
     search --no-floppy --fs-uuid --set 778b551d5531b577 
     drivemap -s (hd0) ${root} 
     chainloader +1 
 }

```

---

### Post by darkod on 2009-11-20
(hd0,1) was actually correct. The new Grub2 is counting the partitions from 1 not from 0 like grub1.
Not sure what the drivemap command does and whether it's necessary. It seems present in multiple drives situation. But I have only one drive and can't compare. Grub2 simply worked here.

The BSOD might be windows related and not ubuntu related. Just guessing here.

---

### Post by teward on 2009-11-20
If I may ask, what's the Windows BSOD say?  I'm a tech, and I have to deal with people coming to me saying "OMG WTF WHY DO I GET A BLUE SCREEN EVERY 5 SECONDS?!?!?"  :P

Also, if you can get your hands on gparted, can you either post or pm me a screenshot of the output for all your hard drives / disk drives shown in gparted so I can see the distribution of partitions along your drive?  (I prefer graphical views, personally, although I use the terminal if needed)

---

### Post by 73ckn797 on 2009-11-20
> **TrekCaptainUSA said:**
> If I may ask, what's the Windows BSOD say?  I'm a tech, and I have to deal with people coming to me saying "OMG WTF WHY DO I GET A BLUE SCREEN EVERY 5 SECONDS?!?!?"  :P

Also, if you can get your hands on gparted, can you either post or pm me a screenshot of the output for all your hard drives / disk drives shown in gparted so I can see the distribution of partitions along your drive?  (I prefer graphical views, personally, although I use the terminal if needed)

The BSOD goes by in a blink of the eye so that any message(s) cannot be read.

Gparted info screenshot attached.

I will also boot up a Windows disk and run chkdsk on the drive.

---

### Post by 73ckn797 on 2009-11-20
> **darkod said:**
> (hd0,1) was actually correct. The new Grub2 is counting the partitions from 1 not from 0 like grub1.
Not sure what the drivemap command does and whether it's necessary. It seems present in multiple drives situation. But I have only one drive and can't compare. Grub2 simply worked here.

The BSOD might be windows related and not ubuntu related. Just guessing here.


It could be likely that Windows is getting baumy. I am rarely using it these days except for one work site I have to use IE to upload images to. I still have my laptop with XP and Ubuntu to get my work finished.

---

### Post by darkod on 2009-11-20
It's probably hating you for using Ubuntu more. :)

---

### Post by 73ckn797 on 2009-11-20
> **darkod said:**
> It's probably hating you for using Ubuntu more. :)

If it has a life of it's own then we are in big trouble!

---

### Post by 73ckn797 on 2009-11-20
OPPS!!

Operator error. I remembered that I was doing something else the other day in the system BIOS and forgot to switch drives back to IDE mode. Windows boots properly from Grub2.

At the time of the installation of Ubuntu I thought I may be having a hard drive failing. I ran gsmartmontools which showed a healthy drive. I concluded that there was a problem with the prior 9.10 install. In the process of checking things over I changed the BIOS setting for the hard drive mode and did not switch it back. Ubuntu was up and running and only today did I have to go into Windows. That is when my "problem" surfaced.

---

### Post by brexsis on 2009-11-27
i have similar problem. i upgraded from 9.04 to 9.10, but things were weird and i installed fresh kubuntu 9.10.
but now i have problem that i cant boot WinXP, it says: "<Windows root>\ system32\ntoskrnl.exe is missing or corrupt."
i tried copy that file from CD, but no changes. only if i restore windows MBR, then i can get to boot windows, so Windows is all right, but grub or something is crashing my WinXP. 
what can i do to be able to boot both OS?

---

### Post by oldfred on 2009-11-27
brexsis I just happened on this thread, you will do better to start your own thread as this thread shows solved, so most poeple will not look at it unless they want the answer the OP had.

You also do not have a blue screen, but a missing windows file, which probably is that grub is looking at the wrong partition if your windows still works otherwise. 

Start a new thread  cannot boot XP from grub  -  ntoskrnl.exe is missing in the title and post your problem with this info, then everyone can help you:
Boot Info Script 0.34 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script034.sh 
sudo ./boot_info_script034.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

