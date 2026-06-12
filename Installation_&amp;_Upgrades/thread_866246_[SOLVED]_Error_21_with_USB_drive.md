---
title: "[SOLVED] Error 21 with USB drive"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by artisan on 2008-07-21
I have just tried to install Ubuntu onto a usb drive.
I am now getting "error 21"
It looks like I have somehow screwed with the grub??
There is Ubuntu on three drives. 2 hard drives and a usb drive.
It is possible to boot into the hard drives (using F11). The usb drive does not boot. The real problem occurs when the usb drive is not installed.
That is when I get error 21
fdisk -l gives.....


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1672f2fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38156   306488038+  83  Linux
/dev/sda2           38157       38913     6080602+   5  Extended
/dev/sda5           38157       38913     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75247dfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14334   115137823+  83  Linux
/dev/sdb2           14335       14946     4915890    5  Extended
/dev/sdb5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdc: 3944 MB, 3944742912 bytes
255 heads, 63 sectors/track, 479 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa3ec4f31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         451     3622626   83  Linux
/dev/sdc2             452         479      224910    5  Extended
/dev/sdc5             452         479      224878+  82  Linux swap / Solaris


Can some one help me untie the mess I made?
Thanks.

---

### Post by falcon61102 on 2008-07-21
Sounds like when you did that last install you installed the GRUB to your External HD so now when it's not present, you get that error.  

You could download the Super Grub Disk and use it's utilities to fix it, or you could reinstall the GRUB back to your HD manually which takes just a couple minutes.

Super GRUB Disk: [www.supergrubdisk.org](www.supergrubdisk.org)

Manually - 

Boot from LiveCD and open terminal
```
sudo grub
find /boot/grub/stage1
```

This should list any grubs that are your system currently, and based on the above information, you're probably going to get one that says:
```
hd(0,0)
```

That's the first partition of your first drive.  Next:
```
root hd(0,0)
setup hd(0)
```

The last code should generate a few lines in responce and you shouldn't see any fails at the end of the lines.  That should reinstall the GRUB back to your first drive and you can then edit the menu.lst to ensure all your installations are on it.

---

### Post by Potatoj316 on 2008-07-21
Im not really an expert in GRUB but perhaps it dosent like it when one of its drives disspaears, maybe its looking for the flash drive and cant find it.

---

### Post by artisan on 2008-07-21
I get the following....

 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd2,0)

grub> root hd(0,0)

Error 11: Unrecognized device string

grub> 


Thanks but,
?????

---

### Post by falcon61102 on 2008-07-21
Ok... which is your primary partition that you normally run Ubuntu off of?

Also, here is the GRUB Manual that lists all the error codes.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by falcon61102 on 2008-07-21
Also if you could, post the menu.lst for your primary partition.  There may be an error with how the GRUB is reading because it has been overwritten by one of the other ones.

---

### Post by artisan on 2008-07-21
> **falcon61102 said:**
> Ok... which is your primary partition that you normally run Ubuntu off of?
Disk /dev/sda: 320.0 GB 

> **falcon61102 said:**
> Also, here is the GRUB Manual that lists all the error codes.
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
Ouch:) I will read up on when i get the time.....:)


> **falcon61102 said:**
> Also if you could, post the menu.lst for your primary partition
I will/would if I knew how.
Would you be kind enough to let me know how??

---

### Post by falcon61102 on 2008-07-21
Your menu.lst is stored in /boot/grub.  Since you are not going to have to edit right at this moment, the easiest way to find it would be through you File Browser. 

Click Places>Computer (Or just click on the icon on the desktop if its mounted) and open your drive.

Navigate to /boot/grub and you should see your menu.lst.  You should be able to open that and copy it, but you won't be able to write to it, that you need to do in command line, which would be something like:
```
sudo gedit /media/disk/boot/grub/menu.lst
```
where /media/disk/ is where your /dev/sda1 partition is mounted.

---

### Post by artisan on 2008-07-22
> **falcon61102 said:**
> Also if you could, post the menu.lst for your primary partition. There may be an error with how the GRUB is reading because it has been overwritten by one of the other ones.

This is something I am expecting.
But don't know how to look for it or fix.

> 

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6f21d373-dc9f-4109-9b2c-6ba8a4cd2e18 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6f21d373-dc9f-4109-9b2c-6ba8a4cd2e18 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6f21d373-dc9f-4109-9b2c-6ba8a4cd2e18 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6f21d373-dc9f-4109-9b2c-6ba8a4cd2e18 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-18-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro single 
initrd		/boot/initrd.img-2.6.24-18-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro single 
initrd		/boot/initrd.img-2.6.24-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro quiet splash 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode) (on /dev/sda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro single 
initrd		/boot/initrd.img-2.6.24-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title		Ubuntu 8.04, memtest86+ (on /dev/sda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


---

### Post by falcon61102 on 2008-07-22
Alright, based on what you posted, it looks like the GRUB is looking for your Ubuntu installation on your second drive, first partition.  Run the GRUB commands that I posted above, and when you use
```
find /boot/grub/stage1
```
You should have one that comes out looking like hd(0,0) or just hd(0).  Use that for the next line which would be:
```
root hd(0,0)
```
Then finally:
```
setup hd(0)
```

Like I said earlier, you should get 6-8 lines of output and you shouldn't see "Failed" at the end of any of the lines.

Now you need to edit your menu.lst a little bit.  So open it:
```
sudo gedit /boot/grub/menu.lst
```

Now to get it to boot to your first drive you need to do a little copy and pasting... 

Copy the first entry under Other Operating Systems... this one:
```
title Ubuntu 8.04, kernel 2.6.24-19-generic (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=95384b45-c73b-4c24-b635-a31975ce503d ro quiet splash 
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

```

And place it above the first entry that you listed here.  Save the file and close.  Now try rebooting and see if that helped or what error it produces when you try.  This should work though.

---

### Post by artisan on 2008-07-22
Am still getting the reply

grub> find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd2,0)

grub> root hd(0,0)

Error 11: Unrecognized device string


The page
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)
gives no information on that error, that I can find.

---

### Post by artisan on 2008-07-22
ok, so if I

sudo grub
and then
find /boot/grub/stage1
and then 
root hd(0,0)

using the terminal on the live cd I get:
Error 11: Unrecognized device string

but if I

sudo grub
and then
find /boot/grub/stage1
and then 
root hd(0,0)
using the terminal on the main hard drive
I get
grub>

the next question is 
can I then use 
setup hd(0)

if I am using the terminal on the main hard drive???

Sorry, but I have no idea on grub.

---

### Post by falcon61102 on 2008-07-22
Ok, I see what's happening, that I forgot to tell you about.  When you use your LiveCD, you have to make sure that you mount the partition prior to using it in GRUB.  

What you are seeing when you use if off your hard drive is correct.  Once you do the root string it will just return to the grub prompt.  Go on to the next step which is the setup.

Sorry about the confusing.  If you can run it from your hard drive, do so and based on what you're saying, it should work fine.

---

### Post by artisan on 2008-07-23
Thread marked as solved.

falcon61102 Thank you for your time and patience.
I ended up using super grub. I downloaded it and repaired the MBR (I think)
But I can now run the system without having to have the usb drive installed. :)

---

### Post by falcon61102 on 2008-07-23
Hey, no problem... I'm glad you got it working.  

With the way you have your system set up, Super Grub was probably the best bet anyway but sometimes it's easier/quicker to do things manually.

---

