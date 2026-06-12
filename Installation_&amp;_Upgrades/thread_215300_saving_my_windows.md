---
title: "saving my windows"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by dee31797 on 2006-07-13
Installed ubuntu on a sata hard seperate from my windows xp hard drive.  after installation and first reboot, ubuntu didnt load.  no error message, it didnt do anything.  i changed boot sequence from the linux harddrive back to windows hard drive in bios and tried booting but all i get is - grub stage 1.5, grub error 17 - then it halts.  Tried loading from xp install cd and performing fixboot and fixmbr with no change.  Im guessing installing linux affects other paritions on other drives aswell?  How can i boot from the xp drive without grub?  If there is a thread on this just link it, but i couldnt find it.

edit:
Moved linux harddrive to a different channel and reinstalled which allows me to boot ubuntu but booting from win xp harddrive still shows "GRUB loading stage1.5 loading please wait... error 17" How can i boot windows (without formating that drive)? please help

---

### Post by Herman on 2006-07-14
It is a good idea to make yourself a GAG Boot Manager CD or floppy disk for booting Windows with before beginning any Linux install. GAG Boot Manager will take away a lot of stress and anxiety on behalf of the user by being able to boot Windows for you (most times) if something goes wrong with your installation (GRUB) until you can get that fixed. For how to download and use GAG Boot Manager, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm").

If you can get the GRUB menu, you should be able to press your 'c' key and boot Ubuntu  using GRUB's command line interface.
Use GRUB to investigate your computer and find the right commands you need to type and then boot Ubuntu with those commands. Write down the commands you use, because as soon as you have Ubuntu booted, you can open /boot/grub/menu.lst and edit the file with the corrections to make GRUB boot your computer properly in the future. For how to use GRUB's Command Line, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").
CLI GRUB will probably boot Windows for you too.

If you need specific help with your problem, there is certian vital information that will be needed by those who want to help you. You may use the 'Desktop' Live/Install CD to find this information and post it here, some other LiveCDs may also work.
The results of the following command are normally indispensable, ```
sudo fdisk -lu
``` Also, if you can mount your Ubuntu partition in the Live CD and open your /boot/grub/menu.lst file in Ubuntu, that would also be extremely useful. Post that here too please, if you can. Maybe all you need is a small correction in this file. For how to do that, [Click Here.]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

You can also see how to mount your Windows partition in the 'Desktop' Live/Install CD so you can see that all your Windows files are still intact and untouched, to see how, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop")

I suspect that all that was wrong originally might have been that GRUB was written to the MBR on the wrong disk, and this can easily be rectified by re-installing GRUB to the one that your BIOS will be looking at, which is whichever one is set up as the first one in your BIOS.
This may or may not be compounded by a small error in your /boot/grub/menu.lst file which should be able to be easily corrected.
In a tiny minority of cases there can be a problem of some kind with BIOS or sata disk geometry mathematics, if it's that then I don't know... you'll need someone better than me. 
Let's try the simplest solutions to begin with and hope we'll be able to fix it easily.
Regards, Herman :D

EDIT: 1
edit:>  Moved linux harddrive to a different channel and reinstalled which allows me to boot ubuntu but booting from win xp harddrive still shows "GRUB loading stage1.5 loading please wait... error 17" How can i boot windows (without formating that drive)? please help Will try to help, but please slow down so I can keep up. :D

Edit 2 : It's good that you can now boot Ubuntu, now you won't need to use the Live CD anymore, just get a sudo fdisk -lu and /grub/boot/menu.lst in Ubuntu and I'll see what you need to fix to get Grub to boot Windows for you.

---

### Post by dee31797 on 2006-07-14
_this is sudo fdisk -lu command:_

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150223814    75111876   83  Linux
/dev/sda2       150223815   156248189     3012187+   5  Extended
/dev/sda5       150223878   156248189     3012156   82  Linux swap / Solaris

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   290423069   145211503+   7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdc doesn't contain a valid partition table
------------------
_****the two 74.3 drives are in a raid0 array and contains windows xp***_

this may be a problem:
_standard@linux-prime:~$ /grub/boot/menu.lst_
bash: /grub/boot/menu.lst: No such file or directory

Ubuntu has been working great, but i only know how to use firefox so far (extreme linux noob).
thank you for the help Herman.

---

### Post by Herman on 2006-07-14
```
sudo gedit /boot/grub/menu.lst
```
Try the above command, I'm sorry, I should have been more specific about that. 
I have no experience with RAID arrays, yes, that could have something to do with it. 
Showing your menu.lst will be a good step to do next, and if I can help at all I will, otherwise I hope someone who knows about GRUB and RAID arrays will come along with some advice maybe.
Regards, Herman :D

---

### Post by dee31797 on 2006-07-14
standard@linux-prime:~$ sudo gedit /boot/grub/menu.lst


title		Ubuntu, kernel 2.6.15-26-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot


I Don't see windows.  Im guessing i have add it manually to this document?  How do I convert sbd1 to (hdX,X)?

---

### Post by scxtt on 2006-07-14
> **dee31797 said:**
> I Don't see windows.  Im guessing i have add it manually to this document?  How do I convert sbd1 to (hdX,X)?i assume you meant sdb1 --

```
title           Ubuntu, kernel 2.6.15-25-386
root            [color=red](hd1,0)[/color]
kernel          /boot/vmlinuz-2.6.15-25-386 root=[color=red]/dev/sdb1[/color] ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot
```

---

### Post by dee31797 on 2006-07-14
Thanks scxtt.  I did mean sdb1 but my _windows xp_ is on that partition.  How do I add that to the /boot/grub/menu.lst file to boot windows xp?

---

### Post by scxtt on 2006-07-14
that was just an example, for windows it'd be:```
title         Windows 95/98/NT/2000
root          (hd1,0)
makeactive
chainloader   +1
```which is listed as an example in /boot/grub/menu.conf ...

---

### Post by Herman on 2006-07-14
```
              ### END DEBIAN AUTOMAGIC KERNELS LIST
                   
             # This is a divider, added to separate the menu items below from the Debian
             # ones.
             title        Other operating systems:
             root
                   
                   
             # This entry automatically added by the Debian installer for a non-linux OS
             # on /dev/sdb1
             title        Microsoft Windows XP 
             root        (hd1,0)
             savedefault
             makeactive
             chainloader    +1
``` Hello,  dee31797, try copying the above and pasting in to the bottom of your menu.lst, I hope it will work!
Regards, Herman :D

---

### Post by dee31797 on 2006-07-14
Thanks all.  I give up booting that partition.  Im gonna break out the back harddrive and install windows on it.  Hopefully that will fix the mbr because the fixboot/fixmbr in windows xp recovery console didnt fix it.  if it doesnt work, i can just backup everything I want from the old xp install then reformat and reload it.  Seems like the fastest solution because this is all french to me (failed french 3 semesters straight in high school).  I want ubuntu as my primary OS but I have to have my 1/4 day dose of counter-strike source and Dawn of War.  Could you point me to the best linux ubuntu for dumbies guide?

---

### Post by Herman on 2006-07-14
Sure, here's a whole handful of them:
[http://www.ee.surrey.ac.uk/Teaching/Unix/  ]("http://www.ee.surrey.ac.uk/Teaching/Unix/")  
   
         [http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User's_Guide]("http://tlug.up.ac.za/wiki/index.php/CS_Student_Linux_User%27s_Guide")
          
         [http://www.linuxcommand.org]("http://www.linuxcommand.org/")        |        [http://www.linux.org/lessons/](http://www.linux.org/lessons/)
          
         [http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[URL="http://rute.2038bug.com/index.html.gz"]
http://rute.2038bug.com/index.html.gz[/URL]

Just pick out one you like. I though the top one was a good one to begin with, but they're all good. I haven't finished any of them myself, (just grasping the bare necessities).
Regards, Herman :D

---

