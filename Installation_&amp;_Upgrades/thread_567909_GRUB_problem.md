---
title: "GRUB problem"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by t4ggs on 2007-10-05
Hi, I had ubuntu and then installed XP and wanted to dual boot so i did:
sudo grub
find /boot/grub/stage1
root (hd0,6)
setup (hd0)
quit
exit

then when i reboot i see that grub has been installed and i can get into xp, but when i try booting ubuntu it gives me this error:

error 15: File not found

Any ideas what can i do? please explain everything because i`m still a newbie in linux.
If i have to write commands in the terminal so please help me and explain each step.

---

### Post by dcstar on 2007-10-05
> **t4ggs said:**
> Hi, I had ubuntu and then installed XP and wanted to dual boot so i did:
sudo grub
find /boot/grub/stage1
root (hd0,6)
setup (hd0)
quit
exit

then when i reboot i see that grub has been installed and i can get into xp, but when i try booting ubuntu it gives me this error:

error 15: File not found

Any ideas what can i do? please explain everything because i`m still a newbie in linux.
If i have to write commands in the terminal so please help me and explain each step.

Your /boot/grub/menu.lst file needs the right info, you will have to boot off the Live CD and mount your hard disk to examine this file - do a search for posts with specific steps on how to check - and edit - this file.

What did the Grub "find" command actually return?

---

### Post by t4ggs on 2007-10-05
it returns (hd0,6)

---

### Post by confused57 on 2007-10-05
You might want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by t4ggs on 2007-10-05
I have looked into the menu.lst and there is a mistake it boots in (hd0,8) but it should but in (hd0,6). Now the problem is, i changed it but i cant save it because i have to be logged as root... what should i do?? i'm doing it with the live cd.

---

### Post by Pumalite on 2007-10-05
What about confused57 suggestion?

---

### Post by t4ggs on 2007-10-05
what should i do, just open terminal and write down sudo fdisk -l and then post it???

---

### Post by Pumalite on 2007-10-05
Yes

---

### Post by dcstar on 2007-10-06
> **t4ggs said:**
> I have looked into the menu.lst and there is a mistake it boots in (hd0,8) but it should but in (hd0,6). Now the problem is, i changed it but i cant save it because i have to be logged as root... what should i do?? i'm doing it with the live cd.

In a terminal:
```
gksudo nautilus
```
This will launch a root privileges file browser.

---

### Post by Techno Leper on 2007-10-06
hello this is my first post and im not too computer smart sorry

ok i had this hard drive that i wasnt useing so i thought id put ubuntu on it so i shut down my computer i put the hard drive in my computer as an extra drive witch would become d: then i started up my computer again with the ubuntu CD in and installed it to this extra hard drive after it was finished i shut down the computer out of ubuntu and took the drive out and was all done so i started up my computer to sign back into windowsxp and now it wont start windows but reads insted 

GRUB Loading stage1.5.

GRUB loading please wait...

error 17

i simply would like to just be able to sign back into windowsxp witch is on my main c: drive of course

if that was stupid of me im sorry

---

### Post by t4ggs on 2007-10-06
This is what i get with sudo fdisk -l as u can see my linux boot partion is in sda7, isn it (hd0,6)?? and my windows partition is in the 80Gb Hard disk, sdb1.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       30401   244188000    5  Extended
/dev/sda5               2       17043   136889833+   7  HPFS/NTFS
/dev/sda6           17044       21526    36009666    7  HPFS/NTFS
/dev/sda7   *       21527       22731     9679131   83  Linux
/dev/sda8           22732       22853      979933+  82  Linux swap / Solaris
/dev/sda9           22854       25163    18555043+  83  Linux
/dev/sda10          25164       30401    42074203+  bc  Unknown

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

I used the command gksudo nautilus, it opens a file explorer with root privileges but I cant acces any HD, just one named file system, i guest that this is because of that im using the live CD...

I dont know but when in terminal i used ind /boot/grub/stage1, it returned (hd0,6) and when i open menu.lst this is what i get: 

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fc1e7f34-79a1-44c1-b664-a7929ebb4bc1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fc1e7f34-79a1-44c1-b664-a7929ebb4bc1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fc1e7f34-79a1-44c1-b664-a7929ebb4bc1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=fc1e7f34-79a1-44c1-b664-a7929ebb4bc1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


So I suppose i have to change all the (hd0,8) to (hd0,6), am i right??? and if i do, how can i save the changes???

---

### Post by t4ggs on 2007-10-06
the face with sun glasses should be (hd 0 , 8 )
without the spaces.

---

### Post by Herman on 2007-10-06
Hello t4ggs, The following link should tell you how to mount your Ubuntu hard disk installed operating system in your Live CD.
[Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") rescue your Linux system with a Live CD[COLOR=#666666][COLOR=#000000] 
You will also see at the end of that link how to gain access to some of the vital files that people sometimes need to edit from the LiveCD to get Ubuntu to boot.
That should get your menu.lst file for you and you will be able to edit it and save the changes.:wink:

Regards, Herman :)
[/COLOR][/COLOR]

---

### Post by Herman on 2007-10-06
Techno Leper,
> ok i had this hard drive that i wasnt useing so i thought id put ubuntu on it so i shut down my computer i put the hard drive in my computer as an extra drive witch would become d: then i started up my computer again with the ubuntu CD in and installed it to this extra hard drive after it was finished i shut down the computer out of ubuntu and took the drive out and was all done so i started up my computer to sign back into windowsxp and now it wont start windows but reads insted 

GRUB Loading stage1.5.

GRUB loading please wait...

error 17

i simply would like to just be able to sign back into windowsxp witch is on my main c: drive of course
 You have installed the IPL for GRUB in your MBR (like a pointer to make the MBR of your first hard disk point to Ubuntu instead of Windows).

That won't hurt anything, but for now you can't boot.

You have a choice of three options.
1. Put the hard disk that has Ubuntu in it back in the computer
2. Run FIXMBR from a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm")  (in your Windows Install CD)
3. Download [Super Grub Disk]("http://geocities.com/supergrubdisk/")  and make a CD, USB or floppy disk (depending on what kind of SGD file you download), and boot SGD, and go 'English Super Grub Disk'-->'Windows'-->'Fix Boot of Windows', and it will be fixed. 

Regards, Herman :)

---

### Post by Techno Leper on 2007-10-06
1. you mean by the first option use ubuntu as an OS? ?
2. ok 2nd option sounds ezy i would have tryed that first but i dont have the xp disk readly available erg
3. ok so i can put Super Grub on a CD or a floppy or my usb flash stick and boot from them first ok got yah i hope

yeah i would have googled a way to fix this for a little longer before posting but it was late and i needed to go to bed so thank you by the way

---

### Post by t4ggs on 2007-10-06
Herman thank u for your help, it worked but after some reboots i get the same problem so i boot again from the live CD opened the menu.lst and surprise!! it says again (HD0, 8 ) instead of (HD0,6) it changed alone... why??

---

### Post by confused57 on 2007-10-06
> **t4ggs said:**
> Herman thank u for your help, it worked but after some reboots i get the same problem so i boot again from the live CD opened the menu.lst and surprise!! it says again (HD0, 8 ) instead of (HD0,6) it changed alone... why??

Since Herman's not online right now, when you change your root to (hd0,6), you also need to change the line with groot:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

What happened was that with a kernel update, "update-grub" is run, which uses this line to set the kernel roots(make sure to leave the # in front of groot).

---

