---
title: "Got Busybox and cant get LiveDVD thing happening"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by rapattack1 on 2013-06-17
Hi i have presently Ubuntustudio 12.04 and having heaps of problems with USB devices especially my usb mic (samson)so thought i would try the live dvd of ubuntustudio 13.10. Yes i have enough ram according to specs. Anyway i got this on the screen:
Busybox v1.20.2 (ubuntu 1:1.20.0 - Bubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands
(initramfs)

I have seen this sort of thing before and suspect it is something to do with something corrupt? Sorry not that expert at my commands and linux. I have burnt many Linux versions over the years and i know i have seen this before. Do i have to redownload and burn? I used k3b to burn the iso and i got the iso from here [http://cdimage.ubuntu.com/ubuntustudio/dvd/current/](http://cdimage.ubuntu.com/ubuntustudio/dvd/current/)

oh and i keep hearing about stable and unstable. IF the most recent version is unstable i bet its not for me. Me not being very proficent in linux :0) ):P

---

### Post by Cheesehead on 2013-06-18
Are you *sure* you are booting from the live media?

The busybox prompt occurs during a strange and rare class of errors: 
During the initial boot, the kernel loads first. Then the "init" process (which uses the kernel) loads.
One of the first things init does it create the filesystem, then attach appropriate storage to the filesystem.

There's a problem there: How does the kernel and init load if the storage isn't attached yet?
The current answer is that the bootloader (that's why there is one) mounts your disk -or live media- read-only.
Then init cleverly unmounts the disk and remounts it read/write.

The busybox prompt (mostly) occurs when init fails to unmount or remount the disk or live-media.
Sometimes it's due to hardware - a flaky or dying disk controller.
Sometimes it's due to a misconfiguration...but most Live images are tested for that before release.
Sometimes it's due to a system booting off the wrong disk (like the hard drive instead of Live-media, or the reverse)

---

### Post by rapattack1 on 2013-06-18
Yep i am sure. Dvd is in the drawer. I dont know what to say coz i dont understand most of it. I set the bios to boot from the cd...otherwise if i hadnt then i would be booting into the system which is what i am using right now

---

### Post by Cheesehead on 2013-06-18
Since Live media are read-only, it may not be worth your time to dig too deep.
Try burning a different image - different version, different flavor, etc.
If you were using a USB stick (I realize you're not), try a different stick.

---

### Post by rapattack1 on 2013-06-22
Oh thanks yeah did another livedvd and it worked :0) Thanks so much. Unfortunately this didn't answer my issue with my microphone so will have to try anutha distro :0)

---

