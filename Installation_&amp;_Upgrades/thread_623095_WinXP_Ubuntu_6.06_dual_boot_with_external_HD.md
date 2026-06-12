---
title: "WinXP/ Ubuntu 6.06 dual boot with external HD"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by Nubsy on 2007-11-25
Hi everyone. :)
Okay. So my computer, the main HDD is running WindowsXP SP2. I found an unused HD in an old computer I had, and I took the HD and bought a casing for it (USB) and it is now connected to my computer. So on the external HD, I installed Ubuntu using the Live CD. All went well, no errors or anything. One problem. I can't boot into it. It goes right to Windows. So I looked online, and read about adding to the C:\boot.ini:

```
c:\bootsect.lnx="Linux"
```

So now, when I restart, I get the screen showing 
Microsoft Windows 2000 Professional
Linux

When I go to linux, it gives me an error and the computer restarts. I can get into windows fine. (although the boot sequence for it seems quite longer now) 
Now, I also read that I need to start the live CD in rescue mode and put in:
```
dd if=/dev/hdan of=/bootsect.lnx bs=512 count=1
``` 
(Note: I would change 'hdan' to sdb, that's what ubuntu recognized the external HDD as at install.)
After, copy the code to a floppy and bring it back to XP and it would work. But I can't get into rescue mode.

Finally, I don't think Grub was installed. There doesn't appear to be anything about it anywhere, and I didn't see anything about it at install.

If it matters, the external HDD is IDE and 6GB. (small, I know) Let me know if I need to add anymore info. :)
:popcorn: Thank you all in advance. ^^

---

### Post by LaRoza on 2007-11-25
If you have an external drive, you can boot it from bios. Just enter "Setup" or something like it before Windows loads.

---

### Post by Nubsy on 2007-11-25
I did try that. The only options are:
1. normal
2. Diskette drive
3. Hard Drive C:
4. IDE CD drive

---

### Post by LaRoza on 2007-11-25
If your computer cannot boot from USB, there isn't anything you can do (usually). It is a BIOS issue and common on older (even newer) computers.

---

### Post by Nubsy on 2007-11-25
Seriously?
Okay, thanks. :)

---

### Post by confused57 on 2007-11-25
> **Nubsy said:**
> Seriously?
Okay, thanks. :)
I've never booted linux from boot.ini, but I believe grub has to be installed to the root partition...you can do this with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in the thread, but it would be something like:
```
sudo grub
find /boot/grub/stage1
```
if this returns "root (hd1,0)", you would enter:
```
root (hd1,0)
setup (hd1,0)
quit
```

Then your dd command would be:
```
dd if=/dev/sdb1 of=/bootsect.lnx bs=512 count=1
```

Read back over any instructions you've found about booting linux from boot.ini to see if this might be correct, especially since I've never personally done this.

---

### Post by meierfra on 2007-11-25
> There isn't anything you can do (usually)

 There are things you can try:

1) If you are lucky  where might be an update for your bios which allows booting from an USB drive.

 2) Create a small boot  partition on your internal drive, which is used to boot your external drive.

---

### Post by LaRoza on 2007-11-25
> **meierfra said:**
> There are things you can try:

1) If you are lucky  where might be an update for your bios which allows booting from an USB drive.

 2) Create a small boot  partition on your internal drive, which is used to boot your external drive.

Both are viable solutions, but if something goes wrong, you can possibly destroy your motherboard (if the bios update fails) or render Windows unbootable, if the second solution fails.

---

### Post by meierfra on 2007-11-25
1)  Don't really know how dangerous flashing the bios is. But I have to admit that its is generally not recommend unless your bios are causing problems. 

2) Creating a boot partition on the internal drive is no more dangerous than installing ubuntu on the internal drive.

---

### Post by Nubsy on 2007-11-25
> **confused57 said:**
> I've never booted linux from boot.ini, but I believe grub has to be installed to the root partition...you can do this with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
read the instructions in the thread, but it would be something like:
```
sudo grub
find /boot/grub/stage1
```
if this returns "root (hd1,0)", you would enter:
```
root (hd1,0)
setup (hd1,0)
quit
```

Then your dd command would be:
```
dd if=/dev/sdb1 of=/bootsect.lnx bs=512 count=1
```

Read back over any instructions you've found about booting linux from boot.ini to see if this might be correct, especially since I've never personally done this.


Okay. Thanks, I'll check out that thread. I dunno want to change my windows partitions at all- I mean, I need to have something to run on.

---

### Post by LaRoza on 2007-11-25
> **meierfra said:**
> 
2) Creating a boot partition on the internal drive is no more dangerous than installing ubuntu on the internal drive.

True, but for a beginner, that can cause a lot of problems if something goes wrong.

---

### Post by confused57 on 2007-11-25
Another possiblity would be to burn a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

or a GAG boot manager  floppy:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)
grub needs to be installed to the root partition for GAG to work

You can then boot with SGD or GAG floppy whenever you want to boot to your external drive.

---

