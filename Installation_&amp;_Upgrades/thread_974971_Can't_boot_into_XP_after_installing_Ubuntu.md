---
title: "Can't boot into XP after installing Ubuntu"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Chocomochino on 2008-11-08
I get a Missing NTDLR, press CTR ALT DEL to reboot



Here´s what i did: 

formated both Xp and ubuntu partitions, 

installed xp (loads fine)

installed ubuntu (xp kept loading, but without grup, so i had to use the livecd, sudo grub, and use a find /boot/grub/menu.lst, after it told me the partition, i saved the changes and reboot, ubuntu booted fine, but i have not been able to boot windows since. )

Here's my  /boot/grub/menu.lst

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        68d5ae17-5ca2-4f8f-ad67-e6f96f478ef9
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=68d5ae17-5ca2-4f8f-ad67-e6f96f478ef9 ro quiet splash
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        68d5ae17-5ca2-4f8f-ad67-e6f96f478ef9
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=68d5ae17-5ca2-4f8f-ad67-e6f96f478ef9 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        68d5ae17-5ca2-4f8f-ad67-e6f96f478ef9
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional x64 Edition
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
----------------------------------------------------------------
Also here's my:
sudo fdisk -l
------------------------------

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21212120

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6527    52428096    7  HPFS/NTFS
/dev/sda2           30382       38913    68533290    5  Extended
/dev/sda3   *        6528       30381   191607255    7  HPFS/NTFS
/dev/sda5           30382       38559    65689753+  83  Linux
/dev/sda6           38560       38913     2843473+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c064

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23759   190844136    7  HPFS/NTFS
/dev/sdb2           23760       30401    53351865    b  W95 FAT32


From what i just did, XP is installed in
 /dev/sda1  and Ubuntu in: /dev/sda3 

when ubuntu loads in grub, it says: loading hd0,4 (why 4??)


/dev/sda1 contains  boot.ini,NTDETECT.COM ntldr, pagefile.sys, unetbin.exe

 boot.ini is as follows:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(0)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect 



Thanks in advance! Any ideas?

---

### Post by meierfra. on 2008-11-08
> I get a Missing NTDLR, press CTR ALT DEL to reboot


Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

and change your Windows item to:

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1


If that does not work, try

title Windows XP Professional x64 Edition
root (hd0,2)
chainloader +1

> loading hd0,4 (why 4??)

Grub starts counting at zero. (hd0,4) is the fifth partition on the first hard drive.

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

and change your Windows item to:

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1


If that does not work, try

title Windows XP Professional x64 Edition
root (hd0,2)
chainloader +1



Grub starts counting at zero. (hd0,4) is the fifth partition on the first hard drive.
When i tried with (hd0,0)

this appeared: Windows Could not start because the following file is missing or corrupt:

<Windows root>\system32\ntoskrnl.exe
Please re-install a copy of the above file

*(just copying from the install cd will do right? the problem is that ubuntu wont mount it

---

### Post by Chocomochino on 2008-11-08
> **Chocomochino said:**
> When i tried with (hd0,0)

this appeared: Windows Could not start because the following file is missing or corrupt:

<Windows root>\system32\ntoskrnl.exe
Please re-install a copy of the above file

*(just copying from the install cd will do right? the problem is that ubuntu wont mount it
*I was able to mount it with mac os

but  in the cd, in AMD64/ i just found NTOSKRNL.EX_

not the exe one, and looking it from ubuntu it says 4.2 mb not 1.6~ like in the cd.

---

### Post by meierfra. on 2008-11-08
Since you were able to boot XP just a little while ago, it is very unlikely that "ntoskrnl.exe" is missing or corrupt.  I have seen this error in some other threads,  it seems to be a bug in Grub. I would like to read through  those threads  before giving you further advice. In the meantime could you try:


title Windows XP Professional x64 Edition
rootnoverify (hd0,0)
makeactive
chainloader +1


and

title Windows XP Professional x64 Edition
rootnoverify (hd0,2)
makeactive
chainloader +1

I don't think any of those will work, but I just want to make sure we don't overlook an easy fix.

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> Since you were able to boot XP just a little while ago, it is very unlikely that "ntoskrnl.exe" is missing or corrupt.  I have seen this error in some other threads,  it seems to be a bug in Grub. I would like to read through  those threads  before giving you further advice. In the meantime could you try:


title Windows XP Professional x64 Edition
rootnoverify (hd0,0)
makeactive
chainloader +1


and

title Windows XP Professional x64 Edition
rootnoverify (hd0,2)
makeactive
chainloader +1

I don't think any of those will work, but I just want to make sure we don't overlook an easy fix.

Nope,

title Windows XP Professional x64 Edition
rootnoverify (hd0,0)
makeactive
chainloader +1

shows the same error,

and

title Windows XP Professional x64 Edition
rootnoverify (hd0,2)
makeactive
chainloader +1


shows: BOOTMGR is missing press Ctrl+Alt+Del to restart, 

(same with root (hd0,2) with no makeactive)
i could try from the recovery console in windows 
expand d:\i386\ntoskrnl.ex_ c:\windows\system32 
and see what happens anyway

---

### Post by meierfra. on 2008-11-08
Could you post the output of

```
cd /mnt
sudo mkdir sda1 sda3
sudo mount /dev/sda1 sda1
sudo mount /dev/sda3 sda3
ls sda1 sda3
cat sda1/boot.ini
cat sda3/boot.ini

```

one of  last two  commands probably will give "file not found". That's expected.

---

### Post by meierfra. on 2008-11-08
> BOOTMGR is missing press Ctrl+Alt+Del to restart

Strange. Do you have  Vista installed on /dev/sda3?  Or had Vista  in the past?


> i could try from the recovery console in windows
expand d:\i386\ntoskrnl.ex_ c:\windows\system32
and see what happens anyway

Thats's fine.

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> Strange. Do you have  Vista installed on /dev/sda3?  Or had Vista  in the past?



Thankfully, i've never had vista installed in that computer.


Here's the output

mochino@Anne:/mnt$ ls sda1 sda3
sda1:
boot.ini                ntldr          Program Files (x86)        WINDOWS
boot.ini~               NVIDIA         RECYCLER
Documents and Settings  pagefile.sys   System Volume Information
NTDETECT.COM            Program Files  unetbtin.exe

sda3:
boot.ini                ntldr          Program Files (x86)        WINDOWS
boot.ini~               NVIDIA         RECYCLER
Documents and Settings  pagefile.sys   System Volume Information
NTDETECT.COM            Program Files  unetbtin.exe

mochino@Anne:/mnt$ cat sda1/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(0)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect
mochino@Anne:/mnt$ cat sda3/boot.ini
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(0)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(0)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

Should i do the expand d:\i386\ntoskrnl.ex_ c:\windows\system32
or should i wait?

---

### Post by meierfra. on 2008-11-08
How come that sda1 and sda3 have the same files?  What is supposed to be on sda3?  Or did you make a mistake in 

sudo mount /dev/sda1 sda1
sudo mount /dev/sda3 sda3

> Should i do the expand d:\i386\ntoskrnl.ex_ c:\windows\system32
or should i wait? 


I would wait.

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> How come that sda1 and sda3 have the same files?  What is supposed to be on sda3?  Or did you make a mistake in 

sudo mount /dev/sda1 sda1
sudo mount /dev/sda3 sda3



I would wait.

it was my mistake sda3 contains nothing but 4 directories i used to share between windows and linux

Anime Ds PSP System Volume Information

---

### Post by meierfra. on 2008-11-08
OK. I think you won't be able to use Grub as your primary boot loader. Instead let's add Ubuntu to the XP boot loader:


Step 1 Install Grub to the boot sector of the Ubuntu Partition and set the boot flag to /dev/sda1


```
sudo grub
```

and at the grub prompt:

```
root (hd0,4)

setup (hd0,4)

root (hd0,0)

makeactive

quit

```

Step 2 Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sda1 /mnt/sda1
```
(ignore any "is already mounted messages)


```
sudo dd if=/dev/sda5 of=/mnt/sda1/ubuntu.bin count=1
```
(be very careful with the "dd" command)

Step 3 Edit boot.ini:

```
sudo nano /mnt/sda1/boot.ini
```

Change "timeout=?" to "timeout=10"

Add this to the end of the file (start a new line, but to not leave a blank line):

C:\ubuntu.bin="Ubuntu"

Save the file.

Step 4 :  

Run "fixmbr" from the repair console of the  Windows CD. 

Reboot:  You should now get a boot menu allowing you do choose between "windows" and "ubuntu"

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> OK. I think you won't be able to use Grub as your primary boot loader. Instead let's add Ubuntu to the XP boot loader:


Step 1 Install Grub to the boot sector of the Ubuntu Partition and set the boot flag to /dev/sda1


```
sudo grub
```

and at the grub prompt:

```
root (hd0,4)

setup (hd0,4)

root (hd0,0)

makeactive

quit

```

Step 2 Copy the Ubuntu boot sector to a file on your Windows partition:

```
sudo mount /dev/sda1 /mnt/sda1
```
(ignore any "is already mounted messages)


```
sudo dd if=/dev/sda5 of=/mnt/sda1/ubuntu.bin count=1
```
(be very careful with the "dd" command)

Step 3 Edit boot.ini:

```
sudo nano /mnt/sda1/boot.ini
```

Change "timeout=?" to "timeout=10"

Add this to the end of the file (start a new line, but to not leave a blank line):

C:\ubuntu.bin="Ubuntu"

Save the file.

Step 4 :  

Run "fixmbr" from the repair console of the  Windows CD. 

Reboot:  You should now get a boot menu allowing you do choose between "windows" and "ubuntu"


ok, im currently at the fixmbr, give me a couple of min plz,

thanks for your help and hard work!

Also i've used since 7.04 ubuntu with win64,just recently at 8.10 grub started giving me problems, this is really strange to me.

---

### Post by Chocomochino on 2008-11-08
> **meierfra. said:**
> OK. I think you won't be able to use Grub as your primary boot loader. Instead let's add Ubuntu to the XP boot loader:

Run "fixmbr" from the repair console of the  Windows CD. 

Reboot:  You should now get a boot menu allowing you do choose between "windows" and "ubuntu"

Well i used the fixmbr, and instead of the menu i got the>

Windows could not start because the following file is missing or corrupt:

 <Windows root>\system32\ntoskrnl.exe

should i try my chances reinstalling xp64, and ubuntu 8.04?

---

### Post by meierfra. on 2008-11-08
Sorry, my guess that it was Grub's fault seems to be wrong.  Must be a windows problem.  


> should i try my chances reinstalling xp64, and ubuntu 8.04? 

I don't see any reason to reinstall Ubuntu.  Reinstalling xp64 might be the fasted way to fix xp. But I suggested to  try

```
expand d:\i386\ntoskrnl.ex_ c:\windows\system32
```

first. I would also run "fixboot".

---

### Post by meierfra. on 2008-11-08
You might also try this procedure:

[http://www.analogduck.com/main/node/294]("http://www.analogduck.com/main/node/294")

---

### Post by Chocomochino on 2008-11-08
let me try that.


What happens when ubuntu's kernel's updates, will windows point to the new kernel by default?

---

### Post by Chocomochino on 2008-11-08
i'm starting to doubt my Xp cd, right now it has frozen 2 times during the initial setup, i might have to get another one tomorrow so i can try fixing this

i'll be sure to let you know what happens,
thanks a lot for your help and hard work Meierfra you rock!

---

### Post by meierfra. on 2008-11-08
> What happens when ubuntu's kernel's updates, will windows point to the new kernel by default?

Yes.  But once you fixed XP or if you want to get back into Ubuntu, you can just  reinstall grub to the MBR:

Boot from the Ubuntu Live CD and

```
sudo grub
```
and at the grub prompt:

```
root (hd0,4)
setup (hd0)
quit

```

---

### Post by Chocomochino on 2008-11-08
okay, i was able to run the expand comand, but the same error is displaying, i don't know what else to try, :(

---

### Post by meierfra. on 2008-11-08
I just  figured out what  is wrong. I should have noticed this a long time ago:

your boot.ini needs to say:

timeout=1
default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]1[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR="Red"]1[/COLOR])\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect

To fix this:

Reinstall grub to the MBR (see my last post)

Boot into Ubuntu. Open  "boot.ini" as before.

Change the two "0" to "1".


Use 

title Windows XP Professional x64 Edition
root (hd0,0)
chainloader +1

in menu.lst and you should be all set.


(Runnning "bootcfg /rebuild" from the XP CD should also cure the problem)

---

### Post by Chocomochino on 2008-11-08
looks like i'm back at stage one, before looking at your current post, i reinstalled windows, and everthing booted up, then i tried reinstalling ubuntu and again, grub was not installed


howeve this time i tried supergrub and everything was working, when i thought i was ready to move on, i used:
sudo grub 


root (hd1,4)
setup (hd1)
.... the other command


i rebooted and now i'm getting the NTDLR missing error again when loading windows.



ubuntu boots though, i wonder why is 8.10 giving me problems that 8.04 did not.


however, when ubuntu loads it says> loading from (hd0,4)

wtf, hd0 again? the livecd told me ubuntu was on hd1,4 when i used the find /boot/grub/menu.lst

---

### Post by Chocomochino on 2008-11-08
well i don't know if this is a bug or me doing the things wrong, i might as well try with 8.04 again and see the outcome, i've tried playing with my partitions numbers and that did not help, that's it. i'm done with this for the morning.

I'm thinking this might be a boot.ini problem.

---

### Post by Chocomochino on 2008-11-08
Okay this is what i did 

I disconnected the second hard drive which does not have any O.s.

edited grub pointed to hd0,0
in the windows partition
*took out the map hd1 hd0 ..etc


i was able to log into windows, and into ubuntu
now i just need to find out how to connect the second hard drive

because i just found it also has Grub installed somehow.!

---

### Post by meierfra. on 2008-11-08
> now i just need to find out how to connect the second hard drive

Just connect the second hard drive, but make sure that the bios are set to boot from the first hard drive.
> 
because i just found it also has Grub installed somehow.!

That should not matter, if you boot from the first drive.

---

### Post by Chocomochino on 2008-11-09
> **meierfra. said:**
> Just connect the second hard drive, but make sure that the bios are set to boot from the first hard drive.


That should not matter, if you boot from the first drive.


yep, it's fixed now, thanks a lot for the hard work man!

---

