---
title: "Failed reboot after install of 7.10"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Wheelz77 on 2008-04-16
Hi,

I'm a noob to Linux and just trying it out to evaluate it's suitability to meet my needs.
I have WinXP Home installed on my laptop and am endeavouring to set up a dual boot.
I installed 7.10 using "Wubi-7.10-alpha-rev386.exe" because I have insufficient space on my C: drive and wanted to put it on my 2nd partition (D: )
The install appeared to go successfully and it rebooted to perform the system installation which also appeared to be successful. It got to 100% and rebooted, went through a few checks and proceeded with the Ubuntu start logo and progress bar then went to a blank screen.
After waiting some time I pressed Ctr+Alt+F1 and got the following text:

>   Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'
  
  (hd0,2)
  Filesystem type is fat, partition type 0xc
    [Linux-bzImage, setup=0x1e00, size=0x1acbb8]
    [Linux-initrd @ 0x16e6775 bytes]

Loading...
mount: Mounting /dev/disk/by-uuid/82D0-A480 on /root failed: No such device
mount: Mounting /root on /host failed: Invalid argument
ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to shell!

Don't understand most of it but the alert claims "root.disk" doesn't exist. Well it does except the path doesn't have "/host" unless that is referring to the installation drive (in this case D: ) 
To my mind it should read: "D:/ubuntu/disks/root.disk"

Does this mean anything to anyone?

Cheers,
Wheelz77

---

### Post by dstew on 2008-04-16
It seems you have installed an alpha version. It might be best to install a more recent beta version.

---

### Post by Wheelz77 on 2008-04-17
Thanks dstew,

That was the first one I found for 7.10 so I'll do another search and try that.

Cheers.

---

### Post by Wheelz77 on 2008-04-17
I've had look around and can only find the alpha version of 7.10 ([http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)) 
If I tried using the 8.04 version, would it then go looking for Ubuntu 8.04 or would it still use the downloaded Ubuntu 7.10?

---

### Post by dstew on 2008-04-17
It would install the 8.04 version. Why do you need or want the alpha 7.10 version?

---

### Post by Wheelz77 on 2008-04-17
The only reason I used Wubi 7.10 was because I'd already downloaded Ubuntu 7.10 and the alpha was the only version of Wubi 7.10 I could find.
Since then I've downloaded Ubuntu 8.04 beta along with Wubi 8.04 and now have a successful installation. Just have to learn the language now. lol
Thanks for the help. :)

---

