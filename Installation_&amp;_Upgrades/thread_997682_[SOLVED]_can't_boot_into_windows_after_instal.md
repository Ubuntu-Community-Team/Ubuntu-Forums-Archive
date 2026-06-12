---
title: "[SOLVED] can't boot into windows after instal"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by licksick on 2008-11-30
I had Win XP already installed on a hard drive (dev/sda1 I believe), and now after installing Ubuntu 8.10 onto a separate hard disk (dev/sdc)the grub menu doesn't show my windows installation.  I am a newbie to ubuntu/grub and I just want to find my windows installation rather than reinstall.

I'm not really sure how to find out what EXACTLY I would need to add to grub/menu.lst to make it work.  I have tried several things but none seem to work.

---

### Post by caljohnsmith on 2008-11-30
OK, how about opening a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like so I can help you boot Windows from Grub. :)

---

### Post by licksick on 2008-11-30
**sudo fdisk -lu** returns:

[COLOR="Blue"]disk /dev/sda: 10.2GB, 10242892800 bytes
240 heads, 63 sectors/track, 1323 cylinders, total 20005650 sectors
units = sectors of 1 * 512 = 512 bytes
disk identifier: 0x32513250

Device   Boot   Start       End     Blocks   Id   System
/dev/sda1   *    63     19988639   9994288+   7    HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0c4b2ef

Device   Boot   Start       End     Blocks   Id   System
/dev/sdb1        63     78140159   39070048+   7    HPFS/NTFS
/dev/sdb4   *    0             0          0    0    Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders, total 39876480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

Device   Boot   Start       End     Blocks   Id   System
/dev/sdc1   *     63     38122244   19061091  83   Linux
/dev/sdc2     38122245   39873329     875542+  5  Extended
/dev/sdc5     38122308   39873329     875511  82  Linux swap / Solaris
[/COLOR]

As for **sudo xxd -1 2 -p /dev/sda** I am not able to get any sort of meaningful response for any of the drives or partitions.  It says:

[COLOR="Blue"]Usage:
     xxd [options] [infile [outfile]]
  or
     xxd -r [-s [-]offset] [-c cols] [-ps] [infile [outfile]]
[/COLOR]

and then it lists options (regardless of what I put for /dev/sda).  I have never used the xxd command before and have no idea what it does or what I am doing wrong that I get this message.

Although I am still stuck, I want to throw out a big [COLOR="Red"]THANK YOU[/COLOR] to all (past, present, and future) who are willing to spend their time and expertise helping a nooBie out.

---

### Post by licksick on 2008-11-30
Ok, I just realized that I needed **xxd -l** not **xxd -1**.  They look identical on my computer.  Oops.  Will post results shortly.

---

### Post by licksick on 2008-11-30
The setup I am looking for is WinXp on the 10gig HD (sda), Linux on the 20gig HD (sdc), and the 40gig HD (sdb) as a file system that BOTH windows and ubuntu can read and write to.  Anyway, here's what I found:


sudo xxd  -l  2 -p /dev/sda
[INDENT][COLOR="Blue"]eb48[/COLOR][/INDENT]
sudo xxd -s 1049 -l 2 -p /dev/sda
[INDENT][COLOR="Blue"]0082[/COLOR][/INDENT]

sudo xxd  -l  2 -p /dev/sdb
[INDENT][COLOR="Blue"]33c0[/COLOR][/INDENT]

sudo xxd  -l  2 -p /dev/sdc
[INDENT][COLOR="Blue"]eb48[/COLOR][/INDENT]
sudo xxd -s 1049 -l 2 -p /dev/sda
[INDENT][COLOR="Blue"]00ff[/COLOR][/INDENT]


and the output of fdisk is posted above.  Any help would be greatly appreciated.

---

### Post by caljohnsmith on 2008-11-30
OK, how about first opening your Grub's menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And at the very bottom add:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Then reboot and try each of the two Windows entries in your menu.lst; one should work, but if not, let me know exactly what happens when you try each one. :)

---

### Post by licksick on 2008-11-30
When I try Windows XP (hd1) at boot prompt I get:
[INDENT][COLOR="Blue"]error 13: invalid or unsupported format
Press any key to continue...[/COLOR][/INDENT]

When I try Windows XP (hd2) at boot prompt I get:
[INDENT][COLOR="Blue"]Starting up ...
NTLDR is missing
Press Ctrl+Alt+Del to restart[/COLOR][/INDENT]

Does this mean I will need to reinstall Windows & Ubuntu?

---

### Post by caljohnsmith on 2008-11-30
OK, I think I see what happened; you are actually booting the Windows sda drive on start up when I thought you were booting the Ubuntu drive. In other words, you actually have Grub installed to the MBR (Master Boot Record) of both your Windows sda drive and your Ubuntu sdc drive according to the output of those previous xxd commands you did, so booting your Windows sda drive could give you the Grub menu. Can you change your BIOS to boot the sdc drive instead? If so, one of those two Windows entries for Grub in my previous post should work to boot Windows. I should mention that it is not as ideal to have Grub installed to your Windows drive while Grub's boot files are on your Ubuntu drive, because then your drives are dependent on each other; if anything happens to one of your drives, you most likely won't be able to boot either Windows or Ubuntu. It would be much better if you can boot the Ubuntu drive directly on start up. So if you can, how about booting your Ubuntu drive on start up and let me know what happens.

---

### Post by licksick on 2008-12-01
Ok, I tried going into the BIOS setup screen and changing the boot device priority so that the Ubuntu drive would boot first.  However, nothing changed, I still get the same error messages as posted above.  I should note that my current setup is as follows:

10gig w/ Win XP - **Primary Master**
40gig empty (will use for BOTH windows and Linux) - **Primary Slave**
20gig w/ Ubuntu - **Secondary Slave**
DVD-Rom - **Secondary Master**

Is this a bad setup?  Should I rearrange the hardware?

I even tried adding this to the grub menu:
 
```
title Microsoft Windows Xp (hd0)
root (hd0,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

in addition to the two entries suggested above.  None of them worked.  The first 2 windows entires, (hd0) & (hd1), give me error 13 and the last (hd2) gives me missing NTLDR.

I am now considering reinstalling BOTH Windows and Ubuntu, but I am curious if there is something else worth trying first?  Or is there a better way to install?  Am I going about this all wrong?

---

### Post by caljohnsmith on 2008-12-01
OK, if you can only boot the Windows drive on start up, then how about trying the following entry to boot Windows: 
```
title Microsoft Windows Xp (hd0)
root (hd0,0)
chainloader +1
```
In other words, you don't have to use Grub's mapping trick when Windows is on the first boot drive, because that's where Windows wants to be. How about giving that a shot and let me know exactly what happens when you try it from the Grub menu.

---

### Post by licksick on 2008-12-01
> **caljohnsmith said:**
> OK, if you can only boot the Windows drive on start up, then how about trying the following entry to boot Windows: 
```
title Microsoft Windows Xp (hd0)
root (hd0,0)
chainloader +1
```


I tried that before I ever even posted to this forum (and again just now), but it still gave me error 13.

However, I noticed something.  I go into BIOS setup and change the order of the boot device priority, then save changes and exit.  But the very next time I go into BIOS its changed back.  In other words the 10 gig drive (Primary Master, windows OS, sda) is always at the bottom of the list.  I can change it to the top of the list but next time I enter BIOS it will be back on the bottom of the list again.

I don't know much about hardware configurations.  I do know that none of the hard drives are SATA drives.  I am begining to wonder if I might just be better off reinstalling both operating systems, but if that's the case, how should I set up my system so I don't encounter the same problems over again?  Or am I jumping the gun?

---

### Post by caljohnsmith on 2008-12-01
I think it is worth trying to troubleshoot this a little further, because I think we are close to sorting out your problem. If you reinstall everything, you might face a different set of problems. How about doing the following first: on start up when you get the Grub menu, press "c" to get the command line, and do:
```
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
```
That will tell you each drive's size in sectors and list its partitions. Note that if you take the sectors and multiply it by 512, you will get the drive size in bytes. So the bottom line, using the above output, please let me know which drive is (hd0), (hd1), and (hd2) on start up. 

And lastly, please post the output of:
```
sudo mkdir /mnt/sdb1 /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sda1 /mnt/sdb1
cat /mnt/sda1/boot.ini /mnt/sdb1/boot.ini
```
I think with all the above info, we can nail down what the problem is about booting Windows. Let me know how it goes.

---

### Post by licksick on 2008-12-02
Thanks again for seeing me through this far.

[COLOR="Blue"]_HD0_
drive 0x80: C/H/S = 1023/240/63, The number of sectors = 39876480, LBA
Partition num:0, Filesystem type is ext2fs, partition type 0x83
Partition num:4, Filesystem type unknown, partition type 0x82

_HD1_
drive 0x81: C/H/S = 1023/240/63, The number of sectors = 78165360, LBA
Partition num:0, Filesystem type unknown, partition type 0x7

_HD2_
drive 0x82: C/H/S = 1023/240/63, The number of sectors = 20005650, LBA
Partition num:0, Filesystem type unknown, partition type 0x7[/COLOR]

Now when I get to the line "sudo mount /dev/sdb1 mnt/sdb1" I get:
[INDENT][COLOR="Red"]mount:you must specify the filesystem type[/COLOR][/INDENT]

ls -l /mnt/sda1 mnt/sdb1 gets me this:
[INDENT][COLOR="Blue"]/mnt/sda1:
total 1953836
drwxrwxrwx 1 root root       4096 2008-11-29 11:00 Documents and Settings
-rwxrwxrwx 1 root root 2000683008 2008-11-29 12:21 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-11-29 11:00 Program Files
drwxrwxrwx 1 root root       4096 2008-11-29 12:21 System Volume Information
drwxrwxrwx 1 root root      32768 2008-11-29 12:24 WINDOWS

/mnt/sdb1:
total 0
[/COLOR][/INDENT]

And lastly "cat /mnt/sda1/boot.ini /mnt/sdb1/boot.ini" gets me this:
[INDENT][COLOR="Blue"]cat: /mnt/sda1/boot.ini: No such file or directory
cat: /mnt/sdb1/boot.ini: No such file or directory[/COLOR][/INDENT]

---

### Post by caljohnsmith on 2008-12-02
[QUOTE=licksick]Thanks again for seeing me through this far.[/QUOTE]You're welcome, and let's hope we can get your setup working without too much trouble. :) That info you provided clears things up quite a bit; you are booting the Linux HDD on start up, the sdb drive is second in the BIOS boot order, and the sda Windows drive is third in the BIOS boot order. Unfortunately though, Windows is missing its three necessary boot files (boot.ini, ntldr, NTDETECT.COM), so that would explain why previously you got that "NTLDR missing" error when booting Windows on (hd2), which is the third boot drive; that agrees with the "geometry" results that showed your Windows drive was the third boot drive, so that all makes perfect sense now. 

You mentioned before that your 40 GB data drive is empty? Because I haven't mentioned up until this point (I thought it might not be an issue), but your sdb drive partition table is at least slightly corrupt since it shows sdb4 as an empty partition. And since you had problems mounting the sdb1 partition, it's obviously an issue. If that drive is empty, I would recommend using gparted (System > Admin > Partition Editor) to wipe it clean and recreate whichever partitions you want. 

Anyway, probably all you need to do to get Windows booting will be to simply replace its missing boot files. Since I also have Windows XP, to make it easy I'm attaching the three files you need to this post; just download the "WinXP_boot_files.zip" file to your Ubuntu desktop and do:
```
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
cd ~/Desktop
unzip WinXP_boot_files.zip
sudo mv boot.ini ntldr NTDETECT.COM /mnt
```
Don't worry if the first command returns a "not mounted" error, it is only to make sure. Also make sure you still have the (hd2) Windows entry in your menu.lst that I gave in post #6, because that should be the correct one to boot Windows. After you've done everything above, reboot, try Windows (hd2) from the Grub menu, and let me know exactly what happens. :)

---

### Post by licksick on 2008-12-02
You were right.  Replacing the windows boot files and using the (hd2) grub entry worked.  Thanks a ton.  I have no idea how the files went missing in the first place, but it worked.:p

---

### Post by caljohnsmith on 2008-12-02
Glad it worked; cheers and have fun with Windows and Ubuntu. :)

---

