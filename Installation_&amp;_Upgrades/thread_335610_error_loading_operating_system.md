---
title: "error loading operating system"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by lulabob on 2007-01-10
"error loading operating system" 

A8N-SLI deluxe
Athlon 64 3000+
geforce 6600GT x2
3 hard drives.
2 gigs ram
XP Pro

Have been tyring to get 6.06 installed w/o luck.  Using a commercial CD in a book as the iso had errors and i was just making coasters. I got the splash screen ok, but on install got the picure so nicely created by nemion in his post. Machine freezes. but i can get to the install screen if i chose safe graphics option. tried install from there, upon reboot machine does it's bios thing then "error loading operating system". that's all i get now. windows is gone, and no ubuntu.
Can u please help me.

---

### Post by goodfella on 2007-01-10
If the cd you have is a live cd then you can run ubuntu from the live cd and type in a terminal
```
 sudo grub-install --root-directory=/dev/hdb2
```
/dev/hdb2 is the drive and partition where ubuntu is installed.

---

### Post by lulabob on 2007-01-11
thanks goodfella,
 Yes i have a live CD, and also a retail copy of XP. I booted from the XP CD and found that my drives were all renamed, now windows is in e:. Was going to try fixmbr, but the warning was so stern i chickened out. What will the instructions you gave me do?
 lulabob

---

### Post by vmikalinis on 2007-01-11
He's asking you to boot to the ubuntu live cd and reinstall the boot loader, once this is done you will be able to boot into linux.  It may allow you to get to windows also, i'm not sure.  I know that if windows is on the drive before you install ubuntu and you choose to keep it on the drive, it will be a choice in the grub loader at boot time.

---

### Post by lulabob on 2007-01-13
thanks you guys for the help. sorry it's taking me so long to correspond, but i live in a black hole w/o internet(banks co. ga.) and so have to search at work, then try fix at home.
 
Well i typed in console just as you instructed, and i get "install device not specified"
So dev/hdb2 should be "harddisk 2/G:" where harddisk 2 has E: (windows probably), G: (ubuntu), and H: (swap?)?
      map command gives   A:  floppy
                                       C: harddisk 0
                                       D: harddisk 1
                                       E: harddisk 2  partition 1
                                       F: CD ROM
                                       G: harddisk 2 partition 2
                                       H: harddisk 2 partition 3


  tks so much for helping!
lulabob

---

