---
title: "Ubuntu cannot boot after installation"
date: 2011-02-26
forum: Installation &amp; Upgrades
---

### Post by stephenstop on 2011-02-26
OK. i have downgraded from Ubuntu 10.10 to Ubuntu 10.04. I've had some bumps along the way and finally was able to install 10.04 successfully. Right now, my computer will not boot from the HDD and will only boot from the USB drive that the LiveCD is on. When I reorganize to set HDD as primary boot, i get:

id-laptop login:
id-laptop password:

and I can put that in but then it just gives me a command line that says"id@id-laptop:~$ 

 How do I get it to boot from the HDD instead of from the USB without running into this problem?

If I resequence the boot to HDD as number two, it will juts go into the LiveCD mode. Am I supposed to reinstall 10.04 again? I know 10.04 was successfully installed because it said it was and it needed to restart so i hit the restart button. It also had my old desktop picture there and all my files AND i checked the system info before restarting (it confirmed that lucid lynx was running).

PLEASE HELP I am new to ubuntu and do not know much about commands.

---

### Post by jeremyjjbrown on 2011-02-26
Sounds like a bad install. You are getting the text shell because Nautilus will not start. Type "nautilus" at the id@id-laptop:~$ prompt and post the errors it lists if you can.

---

### Post by stephenstop on 2011-02-26
I typed in nautilus and this is what I got:

id@id-laptop:~$ nautilus
Could not parse arguments: Cannot open display:
id@id-laptop: ~$ nautilus

---

### Post by thefasterblueone on 2011-02-26
Put this in terminal and post the results.

```
sudo fdisk -l
```

---

### Post by stephenstop on 2011-02-26
ok

-----------------------------------------------------------------
id@id-laptop:~$sudo fdisk -1
[sudo] password for owner:
fdisk: invalid option-- '1'

Usage:
  fdisk [options] <disk>      change partition table
  fdisk [options] -1 <disk>   list partition table(s)
  fdisk -s <partition>        give partition size(s) in blocks

Options:
-b <size>            sector size (512, 1024, 2048 or 4096)
-c                   switch off DOS-compatible mode
-h                   print help
-u <size>            give sizes in sectors instead of cylinders
-v                   print version
-C <number>          specify the number of cylinders
-H <number>          specify the number of heads
-S <number>          specify the number of sectors per track

id@id-laptop:~$
----------------------------------------------------------------

---

### Post by thefasterblueone on 2011-02-26
Try again, that is not a "1" it is a lower case "L".

sudo fdisk -[COLOR="Red"]l[/COLOR]

And why are you making so many posts on the same problem?
you will get better help if you choose a descriptive topic and describe your problem accurately, then wait patiently for someone to reply.

Everyone here is volunteering thier help. Have you even tried to find a solution yourself, aside from asking for the answers?

Google is your friend.

---

### Post by stephenstop on 2011-02-26
Disk /dev/sda: 40.0GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes/512 bytes
I/O size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00026866
   Device Boot       Start    End    Blocks    ID    System
/dev/sda1  *           1      4659   37419008  83    Linux
/dev/sda2             4659    4864   1648641   5      Extended
/dev/sda5            4659     4864   164865   82 Linuxswap/Solaris

Disk/dev/sdb: 1040 MB, 1040711680 bytes
128 heads, 40 sectors/track, 397 cylinders
Units = cylinders of 5120 * 512 = 2621440 bytes
Sector size (logical/physical): 512/512 bytes
IO size (minimum/optimal): 512 bytes/512 bytes
Disk identifier: 0x00000000
   Device Boot     Start     End     Blocks    Id    System
/dev/sdb1 *         1        397    1016300     b    W95 FAT32
id@id-laptop:~$
_______________________________________________________________

Yes, I am aware I can use Google, and I have been googling all day and night but I am not a computer person so command prompts are new to me.  Therefore, it is really hard for me to know much about using sudo and the prompts.  This computer was given to me with Ubuntu 10.10 on it and I did not like the OS so I decided to downgrade.

I have had other issues with the install and I finally got it to the point where I can boot up with LiveCD on USB.  I just don't know if I should reinstall and partition or if it is better to repair the installation a different way.

ANY help is greatly appreciated . Thanks in advance.

---

### Post by IWantFroyo on 2011-02-26
Try redownloading and reburning the image. Downgrading can be bumpy.

---

### Post by thefasterblueone on 2011-02-26
Just copy and paste these commands to avoid errors.

Run this in terminal:

```
sudo mount /dev/sda1 /mnt
```


then run this:


```
sudo grub-install --root-directory=/mnt /dev/sda

```


after that reboot and remove the media from cd or usb drive.

then post back here and let us know. There maybe one more thing to do.

---

### Post by stephenstop on 2011-02-27
thefasterblueone,
I did what you suggested.  After reboot the screen said:


_______________________________________________________
*Setting sensors limits           OK

Ubuntu 10.04.2 LTS owner-laptop tty1

id-laptop login:
Password:

Welcome to Ubuntu!
*Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
0 packages can be updated
0 updates are security updates

id@id-laptop:~$
____________________________________________________________

---

### Post by thefasterblueone on 2011-02-27
Login, get your updates, and run this just to be sure:

```
sudo update-grub
```

---

### Post by stephenstop on 2011-02-27
Okay I used sudo update-grub and it found linux image, initrd image, etc.  and now i'm back on the id@id-laptop:~$

---

### Post by stephenstop on 2011-02-27
id@id-laptop:~$ sudo update-grub
[sudo]password for id:
Generating grub.cfg...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrid image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-28-generic
Found initrid image: /boot/initrd.img-2.6.32-28-generic
Found memtest86+ image: /boot/emtest86+.bin
done
id@id-laptop:~$
_________________________________________________________________

---

### Post by thefasterblueone on 2011-02-27
Type:   startx   then press enter.

---

### Post by stephenstop on 2011-02-27
Yes I've tried startx and it says Fatal server error:
AddScreen/ScreenInit failed for driver 0

So I typed: sudo apt-get install ubuntu-desktop
and tried startx again, but it says to check the log file at "/var/log/Xorg.0.log" for additional information

pretty much the same response AddScreen/ScreenInit failed for driver 0

---

### Post by thefasterblueone on 2011-02-27
Ok try this:

```
fixvesa
```

then

```
startx
```

---

### Post by stephenstop on 2011-02-27
Okay after i typed fixvesa

it said: 
fixvesa: command not found

---

### Post by stephenstop on 2011-02-27
I think I need to enable agpgart.  it says its not available or cannot be used.  Do you know how I can do this?

_________________________________________________________________
(EE) intel (0): Failed to initialize kernel memory manager
(EE) intel(0): AGP GART support is either not available or cannot be used.  Make sure your kernel has agpgart support or has the agpgart module loaded.
(EE) intel (0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0

Please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log giving up.

---

### Post by thefasterblueone on 2011-02-27
```
cat /proc/driver/nvidia/agp/status 

```

---

### Post by stephenstop on 2011-02-27
-bash: cat/proc/driver/nvidia/agp/status: No such file or directory

---

### Post by stephenstop on 2011-02-27
Would it be wrong to try reinstalling Ubuntu 10.04?  Or will that give me more problems?

---

