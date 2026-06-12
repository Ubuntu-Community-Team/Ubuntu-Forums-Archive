---
title: "Boot problem"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Erik. on 2008-05-28
Hi,

I have 2 harddiscks one for ubuntu and the other for windows.

Now when i installed ubuntu i asked me if i want to make a dual boot system.

i sayd yes and i get a nice screen whit all operation systems i have.

Now i wanted to run windows but when i try it says starting up ... and i can wait my whole life but it does nothing.

The boot is on the hdd of windows

How can i fix this?

---

### Post by Herman on 2008-05-28
:) Hello Erik.
Are you seeing the words 'Starting up...' on a blue background or on a black background?

Do you have Windows Vista? Windows XP? Windows 98?

Can you boot Ubuntu and open a terminal and run 'sudo fdisk -lu' please. If you can post the output from 'sudo fdisk -lu' here it might give someone a clue about what might be wrong. ```
sudo fdisk -lu
```

---

### Post by Erik. on 2008-05-29
Hello,

I have a black ground and i use windows xp prof.

Yes i am seeing the words starting up...

I am now at school, when i am home i will post the result

---

### Post by Erik. on 2008-05-29
Here it is:

```


Schijf /dev/sda: 203.9 GB, 203928109056 bytes
255 koppen, 63 sectoren/spoor, 24792 cilinders, totaal 398297088 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x625002f9

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1           16065   205776584   102880260    f  W95 Uitgeb. (LBA)
/dev/sda2       205776585   392419754    93321585   83  Linux
/dev/sda3       392419755   398283479     2931862+  82  Linux wisselgeheugen
/dev/sda5           16128   205776584   102880228+   7  HPFS/NTFS

Schijf /dev/sdb: 163.9 GB, 163928604672 bytes
255 koppen, 63 sectoren/spoor, 19929 cilinders, totaal 320173056 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x01992018

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *          63    40981814    20490876    7  HPFS/NTFS
/dev/sdb2        40981815   320159384   139588785    f  W95 Uitgeb. (LBA)
/dev/sdb5        40981878   102446504    30732313+   7  HPFS/NTFS
/dev/sdb6       102446568   163911194    30732313+   7  HPFS/NTFS
/dev/sdb7       163911258   225375884    30732313+   7  HPFS/NTFS
/dev/sdb8       225375948   320159384    47391718+   7  HPFS/NTFS


```

---

### Post by Herman on 2008-05-29
:) Thank you, I can see that your Windows partition is probably /dev/sdb1, which is in your second hard disk, first partition. In GRUB numbering that would be (hd1,0).
Your partition tables look okay at a quick glance.
It is unusual that you have an empty space at the start of your first hard disk between sector number 63 and 16065. That shouldn't matter, but is there a special reason for that? Did you have something there and you deleted it? I'm just curious in case it has something to do with your booting problem, that's all. 

Please check at the bottom of your /boot/grub/menu.lst file now and make sure you have a boot stanza for Windows XP Professional that looks something like this example,
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```The pair of 'map' commands are used for booting Windows in a non-first hard disk without the need for editing boot.ini in Windows. If you have always had this Windows installation in your second hard disk, you might not need the map commands. If Windows was installed in the second hard disk at that time of installation, it would have the correct hard disk number in the boot.ini file already.
SO, if you have the 'map' commands, try hashing them out and boot without them, and if you don't have the pair of 'map' commands, try pasting them in and see if it helps your GRUB to boot Windows for you.

You should also check to make sure Windows XP Professioal has a boot.ini file, an ntldr, and an ntdetect.com file in the root (top level) of its file system. You can do that by mounting your Windows file system in Ubuntu or in the Live CD.
```
sudo mkdir /media/windows
``````
sudo mount /dev/sdb1 /media/windows -t ntfs -o umask=0002,nls=utf8 
```Now take a look and see if Windows has any boot loader, it should look something like this, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting.

Regards, Herman :)
            [SIZE=+1]
      [/SIZE]

---

### Post by Erik. on 2008-05-30
Hi,

i don't know why i have some free space, i dont'have anything in it.

I will take an look if ui can find the boot files into windows.

When there are not there i have an backup in my computer, windows always make an backup when shuting down.

---

### Post by Erik. on 2008-05-31
I have tried your example but is still does not work, now i got some other error i thought error 17 i am not sure

i will post my menu.lst:

```

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.17-12-generic-ccs
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic-ccs root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic-ccs
quiet

title		Ubuntu 8.04, kernel 2.6.17-12-generic-ccs (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-12-generic-ccs root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro single
initrd		/boot/initrd.img-2.6.17-12-generic-ccs

title		Ubuntu 8.04, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

#title		Microsoft Windows XP Professional
#root		(hd1,0)
#savedefault
#makeactive
#chainloader	+1

```

Now the problem is ubuntu has the same startup as windows, 1,1 and windows 1.0

hope this can help you...
Ubuntu starts good.

I know grub is installed on my second hdd whit is 160 gb and ubuntu is on the 200 gb hdd


My boot.ini:

```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

---

### Post by Pumalite on 2008-05-31
Try changing the boot order of your hard drives in BIOS.

---

### Post by Erik. on 2008-05-31
I already tried but then i got an error from grub

---

### Post by Herman on 2008-05-31
According to your menu.lst file, it looks like GRUB thinks your Windows hard disk is number 1, and your Ubuntu hard disk is number 2 hard disk.
Your fdisk -lu output indicates the opposite.

Try booting Windows as if it's in the first hard disk then maybe, and see if that helps,
```
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```
(You used to have Windows root as (hd1,0), which would have been your number 2 hard disk's extended partition), if we pretend fdisk is wrong and GRUB's idea of your hard disk order is correct.)

---

### Post by Erik. on 2008-06-05
Hi,

That does not work for me.

I have 2 hdd's

1 160 gig there is windows on
1 200 gig there is uuntu on

I had windows installed first

When i installed ubuntu is asked me if i wanted to make an grub startup screen, i sayd yes and it installed grub on my first hdd that's on windows hdd

When i now want to start windows i get the text starting up... but i can wait my whole life but it does nothing...

Hope someone could help me whit this.

---

### Post by lswest on 2008-06-05
below the "root (hd0,0)" lines (or whatever it is for your system) add ```
map (hd0)(hd1)
map (hd1)(hd0)
``` fixed a similar issue for my XP  And also, your entry may need to be ```
root (hd1,0)
``` as i believe GRUB will see Ubuntu's disk as hd0 instead of hd1.

*EDIT* Oh, woops, someone suggested this already.  Sorry for repeating it.

---

### Post by Erik. on 2008-06-05
Hi,

I now get this error:

Error 11: Unrecognized device string

---

### Post by Herman on 2008-06-05
> Error 11: Unrecognized device string      Check for some kind of a small mistake in the commands you used, such as a bracket or a whitespace in the wrong spot or a letter 'O' (owe) where you should have a number '0' (zero) or something like that.

Probably you should try booting Windows with [Super Grub Disk]("http://www.supergrubdisk.org/").
Download one from that site, there are files there for burning to a CD, most people can use that the easiest. 
If you don't have a working CD drive, you can get a files there for making into floppy disk or making the USB version of Super Grub Disk, pick whichever kind you can use.  
That will help to indicate where the problem is, because if Super Grub can boot your Windows, then probably the trouble is in your GRUB settings. The floppy disk and USB versions are more fun because you can edit those if you want.
If Super Grub Disk can't boot your Windows either then maybe we should go looking for trouble in your Windows operating system.

One thing I can see that you could fix is the boot flag in your Ubuntu hard disk. I don't think that's likely to be your problem, because GRUB doesn't need the boot flag to boot Ubuntu, but it might pay to put a boot flag there anyway just to make sure. You can use any partition editor for that or you can use GRUB's 'makeactive' command.
The easiest way might be to just paste the 'makeactive' command into your /boot/grub/menu.lst's boot stanza for Ubuntu, like this,
```
title        Ubuntu 8.04, kernel 2.6.24-17-generic
root        (hd1,1)
makeactive
kernel        /boot/vmlinuz-2.6.24-17-generic root=UUID=34fc8ec0-d70c-46d2-9d76-ab8fa8046e55 ro quiet splash
initrd        /boot/initrd.img-2.6.24-17-generic
quiet
``` The 'makeactive' command should make a boot flag in your first hard disk the first time you boot Ubuntu with it, after that you can delete that command if you want.
I don't think that's your problem, but it won't hurt to put a boot flag there just in case there's something different about your computer's BIOS, but I doubt it.

---

### Post by meierfra. on 2008-06-05
Just to make sure:  

1) You bios are set to boot from the XP drive?
2) The Grub menu appears at boot up?
3) You are able to boot into Ubuntu from the Grub Menu?

If the answer is yes  to all three questions, then the correct entry for XP should be

```
title     Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```


I know you already tried this, but you only said
> 
That does not work for me.

Could you elaborate?  Do you still get the  "Starting up"  error?

> have an empty space at the start of your first hard disk 

Did you delete any partitions when you installed Ubuntu? (That partition might have contained the boot information for XP)

It also could be that you  Windows Boot sector is corrupt. To fix that,
 boot from the Windows CD,  Press "r" to get into the repair console.  Type

```
fixboot X:
```

 (X is your XP drive letter. It is probably "C:", you can find out the drive letter, by typing  "diskpart")


If fixboot overwrites Grub, you  have to reinstall grub. Boot from the Ubuntu Live CD, open a terminal and type

```
sudo grub
```

and at the grub prompt:

```
find /boot/grub/stage2
```
(this  should  return (hd1,1), if not come back here and asked for help)
Then (still at the grub prompt) 

```
root (hd1,1)
setup (hd0)
quit
```

---

### Post by Erik. on 2008-06-05
> **meierfra. said:**
> Just to make sure:  

1) You bios are set to boot from the XP drive?
2) The Grub menu appears at boot up?
3) You are able to boot into Ubuntu from the Grub Menu?

If the answer is yes  to all three questions, then the correct entry for XP should be

```
title     Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

```
**Al already tries this, it was my first setup, it says starting up but it does nothing at all**


I know you already tried this, but you only said


Could you elaborate?  Do you still get the  "Starting up"  error?



Did you delete any partitions when you installed Ubuntu? (That partition might have contained the boot information for XP)

**I dit not delete anything when i installed ubuntu**

It also could be that you  Windows Boot sector is corrupt. To fix that,
 boot from the Windows CD,  Press "r" to get into the repair console.  Type

```
fixboot X:
```

 (X is your XP drive letter. It is probably "C:", you can find out the drive letter, by typing  "diskpart")

**i will try this now, hope it works **

If fixboot overwrites Grub, you  have to reinstall grub. Boot from the Ubuntu Live CD, open a terminal and type

```
sudo grub
```

and at the grub prompt:

```
find /boot/grub/stage2
```
(this  should  return (hd1,1), if not come back here and asked for help)
Then (still at the grub prompt) 

```
root (hd1,1)
setup (hd0)
quit
```

Thanks for helping me now!

---

### Post by Erik. on 2008-06-06
Hello :lolflag:

I know what my problem was....

I have 4 sata slots in my computer.

I whole time ago my 200 gig hdd did not startup so i put it in another sata slot and then windows did not work anymore...

now i got the good slots back and now it works again.

Sorry, i forgot that :P:-\"

---

### Post by Herman on 2008-06-06
:) Thank you very much Erik, by sharing this error message and it's solution you may be helping other people. 
If anyone gets this GRUB error again and looks it up here in Ubuntu Web Forums then they'll be able to find your solution and that might help them solve their problem. 

Also , since this is an error message I didn't have recorded yet, I have added it and your solution to my index of [Common Booting Errors and Some Possible Cures]("http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible"), in the [GRUB Error]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_Errors") section, exactly here, [Starting up...]("http://users.bigpond.net.au/hermanzone/p15.htm#Starting_up...")
I hope people helping others with GRUB Errors will be able to find it again there someday when it is needed.

Regards, Herman

---

### Post by Erik. on 2008-06-06
lol, no problem.

It was an stupid problem, i forgot that i had switched the sata cables... 
That cost many time from you all,sorry for that!

I want to thank you all for the time and help!

---

