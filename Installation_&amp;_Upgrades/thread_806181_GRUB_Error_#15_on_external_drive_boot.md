---
title: "GRUB Error #15 on external drive boot"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by Adys on 2008-05-24
Hi there,

I bought not too long ago a 500gb WD external drive and had for a while two ext3 partitions, one for data (430gb) and another for an ubuntu "tool-install".
On my main laptop I got a small winxp partition and another Ubuntu one. 

It was working fine until a powercut which got some data corrupt. I was unable to boot anything (the bootloader was installed in the MBR and always directed to the unbootable USB drive), and had to reinstall both OSs on my laptop. That done, I reformatted the Ubuntu partition on my external drive and reinstalled it today.
In Ubiquity I made sure the bootloader was installed on the external drive (/dev/sd5 iirc).

In Grub, when booting from main drive, I don't get the USB drive at all (not sure if that is normal), but booting anything is fine.
When forcing boot on external drive, Grub loads fine and gives me this list:
Ubuntu 8.04 ... kernel .24-16
Ubuntu 8.04 ... kernel .24-26 recovery
Memtest86+
**Other Operating Systems**
Ubuntu 8.04 ... kernel .24-17 (/dev/sd5)
Ubuntu 8.04 ... kernel .24-26 recovery (/dev/sd5)
Memtest86+
Windows XP

Booting any of the Ubuntu systems give me Error 15: File not found. Windows XP gives me an Invalid Executable error, and both memtest work fine.

Any idea what's wrong?

---

### Post by Pumalite on 2008-05-24
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Adys on 2008-05-24
Cheers pumalite, but i've seen that link and tried googling a lot. I can't see why it would be a typo since it installed automatically, too. I strongly doubt the files are corrupt, but it's likely looking in the wrong directory. Unfortunately, I've no idea how to check or change that.

---

### Post by Pumalite on 2008-05-24
I'd fix Windows MBR with Super Grub and start from scratch with a good CD after md5sum and burning at 4x or less.

---

### Post by Adys on 2008-05-24
> **Pumalite said:**
> I'd fix Windows MBR with Super Grub and start from scratch with a good CD after md5sum and burning at 4x or less.

Did that aswell (cd was doublechecked for errors). I tried a lot of stuff, it's my third full reinstall of main + external.

Also, forgot to link my menu.lst (external):
[http://pastebin.com/d7bcc554b](http://pastebin.com/d7bcc554b)

---

### Post by cdtech on 2008-05-24
> 15 : File not found This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK

Could I see your drive list:
sudo fdisk -l

If you have Windows installed, you may need to "fixmbr" the Windows installation first and then reinstall the GRUB bootloader (if your using the Windows MBR).

Just a thought. I need to know your drive scheme.

---

### Post by Pumalite on 2008-05-24
> **Adys said:**
> Did that aswell (cd was doublechecked for errors). I tried a lot of stuff, it's my third full reinstall of main + external.

Also, forgot to link my menu.lst (external):
[http://pastebin.com/d7bcc554b](http://pastebin.com/d7bcc554b)

Check this; it might help you:
[http://ubuntuforums.org/showthread.php?t=804082](http://ubuntuforums.org/showthread.php?t=804082)

---

### Post by meierfra. on 2008-05-24
I don't see any reason for  "fixmbr".

Boot into the ubuntu and copy and paste the items for the ubuntu on the external drive from the menu.lst on the external drive to the menu.lst  on the internal drive.

Then boot from the internal drive and you should be able to get into all your OS's

---

### Post by meierfra. on 2008-05-24
If that was to confusing:

Boot into the ubuntu on the internal drive. Open "menu.lst"


```
gksudo gedit /boot/grub/menu.lst
```

add this to the end of the file:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4f599e19-7d83-4a69-beba-e236372abda3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

Save the file and reboot from the internal drive

---

