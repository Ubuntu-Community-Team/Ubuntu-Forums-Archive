---
title: "GRUB Error 2 - When Installing"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Trancegonadz on 2008-11-15
I'm extremely new to the world of linux!! For the last three days I've been spending some times reading up on how to fix errors and good instillation practices, however I still can't figure out how to get rid of a GRUB error. 

I downloaded the Ubuntu .iso for 8.10-desktop, checked the Torrent for integrity, and burnt an Image at a rate of 4x on Roxio Burning program. I can get Ubuntu loaded with Live Sessions. At first the Live sessions would automatically log me in and would just have a basic "harvest orange" background. Then I tried some changes to the GRUB in Terminal. When I start my computer without the Live CD the GRUB gets to 1.5 and then says GRUB error 2. Now that I have played around with the GRUB when I load Ubuntu with the Live CD I get a log in screen (without any login names/passwords enabled) and the stock ubuntu background.

If you have a walkthru or suggestions for fixing a GRUB error 2 I would be happy to try anything on this computer. It's not dual booting anything and has no saved data.

---

### Post by Pumalite on 2008-11-15
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO.

---

### Post by caljohnsmith on 2008-11-15
> **Trancegonadz said:**
> 
I downloaded the Ubuntu .iso for 8.10-desktop, checked the Torrent for integrity, and burnt an Image at a rate of 4x on Roxio Burning program. I can get Ubuntu loaded with Live Sessions. At first the Live sessions would automatically log me in and would just have a basic "harvest orange" background. Then I tried some changes to the GRUB in Terminal. When I start my computer without the Live CD the GRUB gets to 1.5 and then says GRUB error 2. Now that I have played around with the GRUB when I load Ubuntu with the Live CD I get a log in screen (without any login names/passwords enabled) and the stock ubuntu background.

So did you install Intrepid or not? :) How about posting the following so I can get an idea of your setup and how Grub is installed:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by Trancegonadz on 2008-11-15
After I typed fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476343314   238171626   83  Linux
/dev/sda2       476343315   488392064     6024375    5  Extended
/dev/sda5       476343378   488392064     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   476343314   238171626   83  Linux
/dev/sdb2       476343315   488392064     6024375    5  Extended
/dev/sdb5       476343378   488392064     6024343+  82  Linux swap / Solaris

After I typed  sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"

NO CHANGE For any of the patricians (I altered the SDA text to say /dev/sda1 then /dev/sda2 then /dev/sda3)

I hope that is the info you were looking for! 
Thanks again,
Brad

---

### Post by caljohnsmith on 2008-11-15
You have two drives with two linux installations it looks like; what distros are installed on sda and sdb, and which one is Intrepid? Are you getting the Grub error 2 when booting your sda drive or the sdb drive? 

How about posting the full output of the following commands (just copy/paste your terminal session so I can see everything):
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And also do:
```
sudo fdisk /dev/sdb
```
Press "a", then "1" for the partition, "w" to write the change, and finally "q" to quit. That will mark your sdb1 partition as bootable.

---

### Post by Trancegonadz on 2008-11-15
I'm getting the GRUB error 2 from sda. sdb was a recovery harddrive for this computer but since I had the issue with sda I decided to try the same partitioning on sdb. Both of them are currently loaded with Ubuntu 8.10. 

I'll go ahead and enter in the rest of that in terminal and post it here in a minute.

---

### Post by Trancegonadz on 2008-11-15
ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8100

ubuntu@ubuntu:~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
1007

ubuntu@ubuntu:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 30401.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):

---

### Post by caljohnsmith on 2008-11-15
OK, I think I found at least part of the problem; Grub in the MBR of your sda drive is pointing to sdb1 for its Grub files, when it should be using the Grub files you have on sda1. How about posting the output of the following commands:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Then go ahead and reboot, and see if you still get the same Grub error or not when booting the sda drive (hopefully not). :)

---

### Post by Trancegonadz on 2008-11-15
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)       
setup (hd0)
\ Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub>quit
quit
ubuntu@ubuntu:~$ 


Alright, I'm going to try to reboot, should take a few minutes

---

### Post by Trancegonadz on 2008-11-15
After the reboot Ubuntu is working without the Live CD! Anything else I need to do to ensure my operating system is functioning?

Thank you so much.
Brad

---

### Post by caljohnsmith on 2008-11-15
You're welcome, and I'm glad your problem turned out to be relatively easy to fix. I can't think of anything else Grub-related that you would need to worry about. Cheers and have fun with Intrepid. :)

---

