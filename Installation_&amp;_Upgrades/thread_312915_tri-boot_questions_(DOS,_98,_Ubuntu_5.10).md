---
title: "tri-boot questions (DOS, 98, Ubuntu 5.10)"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by tzykid on 2006-12-05
I've been trying to set up a tri-boot with DOS 6.22, Windows 98, and Ubuntu 5.10. I installed DOS 6.22 on a 2GB primary partition then tryed putting windows 98 on an extended partition that spanned the rest of the drive. After 98 fully installed, I did the standard Ubuntu install (useing version 5.10) and resized the windows 98 partition to allow for Ubuntu to install. There was an article on duel-booting Ubuntu with 9.x windows and that's the way it showed me to do this process. 

I finished the install of Ubuntu and restarted, GRUB showed Ubuntu and MS-DOS 6.22. But, what it is showing as DOS 6.22 is actually windows 98, and it wont run saying it can't find command.com, what I think I did was I shouldn't have resized the partiton and just made a Windows 98 partition and an Ubuntu partition seperatly. (correct me if I'm wrong there). Another question I had was about the actuall DOS 6.22 partiton, it's not reading it at all, if I do "sudo fdisk -lu" it shows linx, swap, DOS partition, and unknown space. With only one of the windows OS showing I know I also need to edit GRUB. from what I've read it should look something like:

title      DOS 6.22
hide       (hd0,5)
unhide     (hd0,0)
root       (hd0,0)
savedefault
makeactive
chainloader +1

title    Windows 98
hide     (hd0,0)
unhide   (hd0,5)
root     (hd0,5)
savedefault
makeactive
chainloader +1


From the things I've read that should allow me to boot both windows 98 and DOS. (left DOS root as (hd0,0) and found which partition 98 was on (hd0,5) from the fdisk) <-- think I did that right. It now shows an entry on the menu for both but but neither will boot. Only thing that will boot is Ubuntu. 

If someone could please point out my mistakes in this install it would be greatly appreciated. (I know I've made more than a few) I'm pretty much stuck on what to do to try to get these OS's to cooperate (other than the way I installed Windows 98 ). 

Thank you in advance for any help/tips

---

### Post by amo-ej1 on 2006-12-05
i can be wrong here but if i remember correctly windows only lives happily on a primary partition.

---

### Post by tzykid on 2006-12-05
hmm... didn't think of that, so if I could set up a single primary partition forget the extended stuff, put DOS and Windows 98 on the same partition, should help right?

---

### Post by louieb on 2006-12-05
> **tzykid said:**
> hmm... didn't think of that, so if I could set up a single primary partition forget the extended stuff, put DOS and Windows 98 on the same partition, should help right?

Maybe but I don't know how or if DOS6 and Win98 would work on the same partition. It is my experience that it is easier if each OS has its own partition. 
You can have up to 4 primary partitions.
Try setting up 4 primary. [LIST=1]
[*]Dos 6.22 (fat16 does not need much space my first dos machine had a 20 MG hard drive)
[*]Win 98    (fat32 if I remember right about 2 gig min)
[*]Ubuntu /  (ext3 2 - 3 gig min)
[*]Linux Swap (.25 - .5 gig )[/LIST]Don't quote me but that should work.

---

