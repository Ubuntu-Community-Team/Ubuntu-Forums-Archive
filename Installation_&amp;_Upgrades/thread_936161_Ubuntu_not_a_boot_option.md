---
title: "Ubuntu not a boot option"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by nlke182 on 2008-10-02
I wanted to upgrade from 7.10 to 8.04 so I reinstalled windows to have a clean install. I tried installing LTS on its own partition (D: on a hard drive which has had problems in the past)and at about 98% it would say grub encountered a fatal error. Then I would click ok and it would finish installing and ask for a reset. When I reset my computer it would load straight into windows and never give me the Ubuntu boot option. So I decided maybe I would try a different partition on another drive. So I installed it on part of my main C Win XP drive and the install finished fine without the error however when it asked for a reset again the same problem it would boot straight to windows without any option. I don't know why I don't get the Ubuntu boot option please help. I never had this problem in the past with Ubuntu its just been with 8.04.

Specs
xp SP 3
amd 3200xp
2gig ram
nvidia 6800GT
160gb ide C: 250gb ide D: E: F: 500gb sata G: H: I: J: all NTFS

---

### Post by ibuclaw on 2008-10-02
You could try setting up grub manually.

Load up the Ubuntu 8.04.1 LiveCD and open a terminal.

Type in:
```
sudo grub
```
to open up the grub prompt.

Then run:
```
find /boot/grub/stage1
```
And you should get an output like so:

** (hd0,0)**
** (hd0,1)**

Each line outputted is the hard-drive number / partition number of where grub is installed.

If you only have one instance of Ubuntu installed on your computer, you should only get one output. (If you don't, tell us and we'll start to worry :))

OK, lets say grub outputted "**(hd0,0)**". To set this up, you have to tell grub where it is installed.
```
root (hd0,0)
```
And lastly, tell grub which MBR (Master Boot Record) to be installed on.

If your BIOS is setup to boot off your master hard-drive, this most likely hd0.
```
setup (hd0)
```

And that is it.
Type:
```
quit
```
And reboot (remove the LiveCD from the CD-Drive if present).

If you get any errors, please post up what you get.

Regards
Iain

---

### Post by nlke182 on 2008-10-02
Thanks for the quick reply. I followed your directions and now my grub works but I can't boot into windows or ubuntu. If I try to log into ubuntu I get error 17 in the grub and if I try windows I get error 12. I only can use the live CD now. Also my ubuntu install drive was hd 1,4 if that matters.

Also when I try to undo changes I get

grub> find /boot/grub/stage1 
 (hd1,4)

grub> root (hd0,0) 

grub> setup (hd0) 

Error 17: Cannot mount selected partition

grub>

---

### Post by caljohnsmith on 2008-10-02
Since you are now able to get the Grub menu on start up, go ahead and reboot, and when you get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it. If X is 1, then change your entry to "root (hd0,Y)"; if X is 0, then change your entry to (hd1,Y). Press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works.

If it works, when you get into Ubuntu, open your menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```
And change all your Ubuntu entries to use the correct (hdX,Y) that worked, and also change the "#groot=(hdX,Y)" to use the same (hdX,Y) that worked to boot Ubuntu. If you run into problems, let me know.

---

### Post by nlke182 on 2008-10-02
Thank you so much for the help I did what you said and my ubuntu grub loads and works now :D . Now I only need to know how to get my XP to work again. I changed the hd from 1,0 to 0,0 and the error message 12 went away for windows and it says starting up. It never starts up though and hangs I don't believe I even leave Ubuntu grub.

---

### Post by caljohnsmith on 2008-10-02
OK, while you are in Ubuntu, please post the output of: 
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Sounds like you might have a problem with Windows and not Grub, but we first need to make sure your Grub menu entry for Windows is correct.

---

### Post by nlke182 on 2008-10-02
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0cb95a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sda5               2       12750   102406311    7  HPFS/NTFS
/dev/sda6           12751       25499   102406311    7  HPFS/NTFS
/dev/sda7           25500       38248   102406311    7  HPFS/NTFS
/dev/sda8           38249       50997   102406311    7  HPFS/NTFS
/dev/sda9           50998       60801    78750598+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5acc5acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13035   104703606    7  HPFS/NTFS
/dev/sdb2           13036       19457    51584715    5  Extended
/dev/sdb5           13036       19189    49431973+  83  Linux
/dev/sdb6           19190       19457     2152678+  82  Linux swap / Solaris

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa13ad289

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdc5               2        5101    40965718+   7  HPFS/NTFS
/dev/sdc6            5102       17850   102406311    7  HPFS/NTFS
/dev/sdc7           17851       30401   100815876    7  HPFS/NTFS

Disk /dev/sdd: 31 MB, 31981568 bytes
4 heads, 32 sectors/track, 488 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0xadfbb797

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         487       31152    4  FAT16 <32M

---

### Post by nlke182 on 2008-10-02
> **caljohnsmith said:**
> OK, while you are in Ubuntu, please post the output of: 
```
sudo fdisk -l
cat /boot/grub/menu.lst
```
Sounds like you might have a problem with Windows and not Grub, but we first need to make sure your Grub menu entry for Windows is correct.

Also I havent changed anything that would effect windows today except for the above mentioned grub settings. Prior to changing grub settings windows was running great since its a fresh install.

---

### Post by nlke182 on 2008-10-02
gksudo gedit /boot/grub/menu.lst 

I had my xp settings wrong in the menu.lst txt. 
I also found this thread [http://ubuntuforums.org/showthread.php?t=668027](http://ubuntuforums.org/showthread.php?t=668027)

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd**1**)
map		(hd**1**) (hd0)
chainloader	+1

needed to be changed to 


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd**0**)
map		(hd**0**) (hd0)
chainloader	+1







 Thanks tinivole and caljohnsmith for all the help. I finally am able to use 8.04 :D

---

