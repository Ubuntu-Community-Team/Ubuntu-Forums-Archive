---
title: "stuck in emergency mode at boot"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by gerard-seine on 2019-10-28
Hi all,

after a fresh install of xubuntu 18.4, I'm stuck at the boot phase.
I get first for a short time the xubuntu blue screen, then I get a white text on black screen saying:

[xxnumber] Coudn't get size 0x8000...000e
/dev/mmcblk1p3: clean, so/so files so/so blocks
[yynumber] systemd-gpt-auto-generator[240]: Failed to dissect: Input/output error
[zznumber] systemd[233]: /lib/systemd/system-generators/systemd-gpt-auto-generator failed with exit status 1.
You are in emergency mode. blalbla , type "journalctl -xb" blalbla "reboot",exit" etc..

The "journalctl -xb" gives a long log, among wich, in red, I can read:
again: this couldn't get size 0x8.....0e
and later down: Failed to dissect: Input/output error
and again: /lib/systemd/system-generators/systemd-gpt-auto-generator failed with exit status 1.

The nano fstab gives:
# / was on /dev/mmcblk1p3 during installation
UUID=blabla / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/mmcblk1p1 during installation
UUID=blabla /boot/efi vfat umask=0077
# /home was on /dev/sda2 during installation
UUID=blabla /home ext4 defaults 0 2
# swap was on /dev/mmcblk1p2 during installation
UUID=blabla / none swap sw 0 0

Before this installation, I had a W10 pre-installed system, I got rid of it during the format, I did not want to use it.
I tried first on this new PC to install MINT Tina Cinnamon but I had too many problems with wifi, touchpad and wake up from sleep, so I decided to move to xubuntu... I hope i did it right !!


During the install, I choosed :
one partition EFI (60MB)
one partition / (29GB)
one partition swap (4GB)
all on a MMC internal drive of 32GB
+
one partition /home on a separate HDD (500GB)

When I reboot, I get the same sequence again.

Any help to take me out of that trap will be very welcome !
Thanks in advance

Gerard

---

### Post by ajgreeny on 2019-10-28
What hardware are you using?

Show us the output (from the live system you used to install if necessary) of ***inxi -Fzx***

Please use **Code-Tags** for terminal output to show that text in a more readable format, the same as it is in the terminal, not as plain text. See my signature below for a **How-to**.

It will also be best to see exactly where you are at present with this installation, so go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script. again, you can do this from the live system if necessary. 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by gerard-seine on 2019-10-28
OK, thanks for your quick answer, I'll try all that and come back.

---

### Post by gerard-seine on 2019-10-28
here is inxi:

```

xubuntu@xubuntu:~$ inxi -Fzx
System:    Host: xubuntu Kernel: 4.15.0-20-generic x86_64 bits: 64 gcc: 7.3.0
           Desktop: Xfce 4.12.3 (Gtk 2.24.31) Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop System: SCHNEIDER product: SCL142ALDDP serial: N/A
           Mobo: N/A model: SCHNEIDER serial: N/A
           UEFI: American Megatrends v: 0.11 date: 01/08/2018
Battery    BAT0: charge: 36.5 Wh 100.1% condition: 36.5/36.5 Wh (100%)
           model: Intel SR 1 SR Real status: Full
CPU:       Dual core Intel Celeron N3350 (-MCP-) arch: N/A cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 4377
           clock speeds: max: 2400 MHz 1: 902 MHz 2: 992 MHz
Graphics:  Card: Intel Device 5a85 bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.01hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 500 (Broxton 2x6)
           version: 4.5 Mesa 18.0.0-rc5 Direct Render: Yes
Audio:     Card Intel Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster
           driver: snd_hda_intel bus-ID: 00:0e.0
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Failed to Detect Network Card!
Drives:    HDD Total Size: NA (-)
           ID-1: /dev/mmcblk1 model: N/A size: 31.3GB
           ID-2: /dev/sda model: ST500LM030 size: 500.1GB temp: 34C
           ID-3: USB /dev/sdb model: USB_Flash_Drive size: 4.0GB temp: 0C
Partition: ID-1: / size: 1.9G used: 83M (5%) fs: overlay dev: N/A
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 51.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 173 Uptime: 13 min Memory: 707.7/3777.0MB
           Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Shell (bash 4.4.191) inxi: 2.3.56 
xubuntu@xubuntu:~$ 



```

and I'll try later the boot-repair

---

### Post by gerard-seine on 2019-10-28
here is the boot-repair link:
[http://paste.ubuntu.com/p/RMQHQHp4Kt/](http://paste.ubuntu.com/p/RMQHQHp4Kt/)

---

### Post by oldfred on 2019-10-28
Report shows no fstab and your output of fstab does not match. Did you reinstall?
Report (for too long) has not shown all the details on MMC type drives, so not all info ther.

Report says dev/mmcblk1p1 is ext3 and /boot. And p3 is ESP- efi system partition. Your list of fstab says ESP was p1 originally.
Generally better with smaller drives not to have separate /boot partition unless using full drive encryption and then it may be required.

---

### Post by rsteinmetz70112 on 2019-10-28
Check you fstab and run fsck on your filesystems. Check the UUID of your drives to see if it matched fstab.

---

### Post by gerard-seine on 2019-10-28
> 
Report shows no fstab and your output of fstab does not match. Did you reinstall?


I think that in the meantime between my first message and your first answer, yes, I tried again to reinstall, adding a partition "boot", just in case, but same behaviour.

> 
Report (for too long) has not shown all the details on MMC type drives, so not all info ther.


Ok, what should I do ?

> 
Report says dev/mmcblk1p1 is ext3 and /boot. And p3 is ESP- efi system partition. Your list of fstab says ESP was p1 originally.


Sorry, I don't know what that means...

> 
Generally better with smaller drives not to have separate /boot  partition unless using full drive encryption and then it may be  required.         


I don't use nor need encryption, so what would you suggest ? I can install again with proper partitions settings, assuming my /home with my documents from a former dead laptop can be safe.

Thanks for your time, I really appreciate.

---

### Post by gerard-seine on 2019-10-28
[**[COLOR=#000000]@rsteinmetz70112[/COLOR]**]("https://ubuntuforums.org/member.php?u=252572")      

> 
Check you fstab


Ok, I understand that I should open it in the text editor, correct ?

> 
 and run fsck on your filesystems.

This one, I don't know how to do ...

> 
Check the UUID of your drives to see if it matched fstab.         


This one neither ... Really sorry to be so silly ...

Thanks for your help !

---

### Post by gerard-seine on 2019-10-28
here is the fstab of the last install:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/mmcblk1p4 during installation
UUID=c623d29f-4614-4344-a382-1c52711f6f0f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/mmcblk1p1 during installation
UUID=2fef30d4-3b2c-427d-811b-cb79af8dbe24 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/mmcblk1p3 during installation
UUID=9904-6826  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda2 during installation
UUID=e8a8baf8-495b-4dda-8675-b393c3cdb328 /home           ext4    defaults        0       2
# swap was on /dev/mmcblk1p2 during installation
UUID=02f47fd5-c38a-43cb-894f-c7f279a8ab34 none            swap    sw              0       0


```

---

### Post by rsteinmetz70112 on 2019-10-28
TO get UUID in emergency mode logged in as root

```
 blkid
```

This should give you a list of UUIDS and device names you can match in the fstab.

```
fsck /dev/<device name>
```

---

### Post by gerard-seine on 2019-10-28
@[**[COLOR=#000000]rsteinmetz70112[/COLOR]**]("https://ubuntuforums.org/member.php?u=252572")

In emergency mode, I just have access to a restricted terminal. I don't know how to put the result of the commands in a file and paste it here on the forum.
The fsck returns an error. What you call <device name> is the name of the computer, the one following root@ in the prompt, right ?

---

### Post by gerard-seine on 2019-10-28
@[**[COLOR=#000000]rsteinmetz70112[/COLOR]**]("https://ubuntuforums.org/member.php?u=252572")
yes, the UUID numbers and names from blkid and fstab are the same

---

### Post by oldfred on 2019-10-28
MMC drives are usually pretty small. 
I might reinstall with just ESP & / on MMC and your /home on HDD.
Is it /home or an old install where /home is really /home/$USER inside an old install? So paths not correct?

To see all the ext2, ext3 & ext4 type partitions which may be repaired with fsck.
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

See also 
man e2fsck
man fsck

---

### Post by gerard-seine on 2019-10-29
Thanks oldfred,
> 
I might reinstall with just ESP & / on MMC and your /home on HDD.

So I will reinstall from the live usb key with a new partition table.
   - On the MMC (32 GB), I'll place ESP (what is it ? /EFI ?) and / .
   - On the HDD (500GB) /home;
Where should I put the swap ?
 I think I'll choose "format" for everything on the MMC, correct ?

> 
Is it /home or an old install where /home is really /home/$USER inside an old install? 


Here is the story about the /home:
It was the /home from an old laptop 32bits with xubuntu 18.2 at the end of life, started with 14 after XP.

All my job documents and mails are inside. The most important are documents  and .thunderbird. I'm the only user of this PC, and the username is the same as in the new install.
Before the end of life of this laptop, I made a backup of this /home on a usb drive. It is this copy that I restored on the new laptop Schneider. (Restore took hours).
On this new laptop, I started first with Mint, but gave up due to too many problems. This /home was there and already on the HDD. I still have the backup from the former xubuntu, and I can manage to get again the few documents created with Mint, if needed but I would prefer to avoid this very long restore.

After this new reinstall, I hope everything will be smooth and that I won't need this fsck thing !

Awaiting for advices before starting the reinstall, thanks again.

Gerard

---

### Post by gerard-seine on 2019-10-30
I did another re-install with a new partition table and I could boot. But I get sometimes mmcblock errors, so I suspect a hardware fault in the MMC.
I'll try to solve it.
Thanks guys for your useful help !

---

