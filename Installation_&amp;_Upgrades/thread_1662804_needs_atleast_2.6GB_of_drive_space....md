---
title: "needs atleast 2.6GB of drive space..."
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by Fibonacci184 on 2011-01-08
For some reason ubuntu will not install, as its saying that the 1.3gb of space is used up...yet there is a new 750gb seagate hooked up. bios reads the new hard drive. there are no other external/internal drives of any kind hooked up.

here is a run down of what i have done...

disconnected old hard drive
connected the new hard drive with the older cables
put the 10.10 installation disc in boot drive
it says i have the comp plugged into a power source and connected to the internet but it wont allow me to click the forward button because i dont have 2.6gb of drive space...is ubuntu not reading my new hard drive? any help would be appreciated. thanks

---

### Post by ajgreeny on 2011-01-08
Can you please run the live CD/USB and then in terminal run ```
sudo fdisk -l
```that's a lower case L at the end; and report back here the output from that command.

---

### Post by Fibonacci184 on 2011-01-08
there is no output after i entered the command. :(

---

### Post by ajgreeny on 2011-01-08
OK, so the disk is not detected by ubuntu.  Can you enter the BIOS at startup (usually you need to press a key, eg. Del or F2) and see if the disk is seen there.

---

### Post by Fibonacci184 on 2011-01-08
under the advanced menu in bios, then under the sub menu of drive config-->[SATA Port 1 it reads the 750gb drive. so im not sure where to go now. thanks for the help so far!

---

### Post by Fibonacci184 on 2011-01-08
well I played around with the bios settings and nothing happened. then I  set it back to the usual settings I had it on about an hour ago and it  read the hard drive, at least for this "boot up". when i try to install  it...it does some searching then this error appears "Warning! Error  fsyncing/closing/dev/sda:input/output error" I have the option to retry  or ignore....if i choose retry the message wont go away. if i choose ignore the "allocate drive space" window appears with the options of erase and use the entire disc (what is there to erase, its a brand new disc) or specify partitions manually....

Hate to sound bitter but this thread has 73 views and one person responds? Is this really support? what i have seen of ubuntu it looks very well done but if I cant install it and the support forums aren't giving support, maybe I should just buy an OS...I just refuse to support windows. :D

I will play around with it some more hopefully this can be solved.

---

### Post by Fibonacci184 on 2011-01-08
update...lol

it froze while installing, so i rebooted the comp and now it does not recognize the hard disk

---

### Post by Fibonacci184 on 2011-01-09
did a boot info script

the hard drive must be fried or I didnt "install" it right can anyone tell me what is going on lol.

```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found
/dev/sda1     ?             0            -1                   Unknown
/dev/sda2     ?             0            -1                   Unknown
/dev/sda3     ?             0            -1                   Unknown
/dev/sda4     ?             0            -1                   Unknown


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda


Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
ERROR: asr: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: ddf1: reading /dev/sda[Input/output error]
ERROR: hpt37x: reading /dev/sda[Input/output error]
ERROR: hpt45x: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: isw: reading /dev/sda[Input/output error]
ERROR: jmicron: reading /dev/sda[Input/output error]
ERROR: lsi: reading /dev/sda[Input/output error]
ERROR: nvidia: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: pdc: reading /dev/sda[Input/output error]
ERROR: sil: reading /dev/sda[Input/output error]
ERROR: via: reading /dev/sda[Input/output error]
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

```

any ideas are appreciated, thanks.

---

### Post by ajgreeny on 2011-01-09
I hesitate to say it, but it sounds like a hardware problem to me.

Can you try running the live CD/USB of ubuntu with this problem disk still connected in the machine, then opening gparted from the system ->administration menu.  Let's see if that finds the disk, and if it does, manually make the new partitions you will want for ubuntu, eg root, swap and home.

Now try installing again, choosing the manual partitioning when you get to that point, and allocating the premade partitions as you have already chosen.  It may still not work, but if not, then I think even more it points to hardware problems.

---

### Post by Fibonacci184 on 2011-01-09
i tried what you said above and it could not detect anything. i feel the hard drive vibrate and hear it make faint noises on boot up, and again bios reads it. is there something i need to do to the hard drive after taking it out of the box and connecting the two cords (maybe like prepping the hard disk before the os installation?) thanks for you help, its greatly appreciated.

---

### Post by oldos2er on 2011-01-09
Did you partition and format it?

---

### Post by Fibonacci184 on 2011-01-09
lol umm nope, i thought thats what the OS installation was for, along with "allocating drive space" i guess im wrong? :O

how involved is formatting? is it something I can do or does it require computer store?

im learning as i go! :D (its nice to see a fellow "Wyomingite" hardly come accross them on forums)

---

### Post by oldos2er on 2011-01-09
Yes, didn't notice you were from Wyoming. Howdy.

Boot from your LiveCD, and run Gparted (I think it's in the System menu) to partition your new drive.

---

### Post by Fibonacci184 on 2011-01-09
gparted doesnt recognize my hard disk, sadly.

---

### Post by oldos2er on 2011-01-09
I'm sorry, I see you already tried gparted. If possible, try the disk in another computer...? If that doesn't work, you may indeed have a bad disk, as ajgreeny suggested.

---

### Post by oldfred on 2011-01-09
Is the BIOS set corectly for this drive?

Some comments from others:
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
BIOS should be set for IDE compatibility mode

BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on)

---

### Post by Fibonacci184 on 2011-01-10
Well I have an Intel D875PBZ mobo and the latest BIOS was released in 2005. So I am "missing" a lot of options the newer technology has.

I have changed the disk from "Auto" to "User" - Nothing Changed

I can't find any AHCI or Compatibility settings in BIOS, I am thinking the mobo is to old for these.

The IDE/SATA option in BIOS has been set to Enhanced as this allows for the most compatibility.

BIOS is set to boot from my DVD drive as this allows the Ubunto CD to be read?

I have disabled the floppy drive in BIOS 

Haha I dont think my BIOS even recognizes the 3gb/s 
(can a hard drive be to "new" for BIOS to read?)

I have no idea how to find out if I have a "locked out boot sector"

I didnt see any option for "quickboot" in BIOS

I have no idea how to put ckdsk on a NTFS partition...lol

I am thinking the HD I received from newegg is "shot" I will test it in another computer tomorrow. Thanks for the help so far, I will report what I find out.

---

