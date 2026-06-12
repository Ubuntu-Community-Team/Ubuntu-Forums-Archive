---
title: "dual booting with fedora"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by ub007 on 2008-11-11
Hello,

I'm trying to dual boot with fedora & ubuntu from **2 separate **hard disks,but unsuccessful so far.
 
I get the screen where I can choose either fedora or ubuntu,Fedora boots OK,but when I try to boot ubuntu I get the error msg
 
error 21:selected disk doesnot exist
 
This is what i tried:

1)installed fedora on the first disk and as the only disk.
2)disconnected the fedora hard disk.
3)installed ubntu on the second disk and as the only disk.
4)Once the Ubuntu install was finished, I moved that disk to slave and re-connected the Fedora disk as master. Booted Fedora and copied the UBuntu boot stanza to the Fedora boot loader. 

This is how I added the boot stanza
 
> mkdir /media/floppy
mount /dev/sdb1 /media/floppy
cd /media/floppy/boot
 
//copied three files -System.map-2.6.9-1.6****,vmlinuz**** and > initrd*** to /boot (/boot of hda)
cp /media/floppy/boot/Sys..... /boot 
cp /media/floppy/boot/vmlinuz..... /boot 
cp /media/floppy/boot/initrd.... /boot 
 
cd /boot/grub (of hda)
vi  menu.lst 
 
> default=0
timeout=15
splashimage=(hd0,0)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.25-14.fc9.i686)
        root (hd0,0)
        kernel /vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=e1922b3b-2a81-430b-96c7-50e6528ae862 rhgb quiet
        initrd /initrd-2.6.25-14.fc9.i686.img

[B]title Ubuntu
        root (hd1,0)
        kernel /vmlinuz-2.6.24-19-generic ro root=LABEL=/
        initrd /initrd.img-2.6.24-19-generic[/B]
 
// highlightened the lines which i added.
 
> #etc/fstab
 
/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
UUID=be72c6c7-6cf6-4a35-8789-0dc60ddee3fe /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0
**/dev/sdb1            /media/floppy  ext3     defaults        0 0**   // added this line,not sure whether this is correct
 
For reference
 
#fdisk -l
 
>    Device Boot      Start         End      Blocks   Id  System
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          25      200781   83  Linux
/dev/sda2              26        2434    19350292+  8e  Linux LVM

/dev/sdb1   *           1        2347    18852246   83  Linux
/dev/sdb2            2348        2434      698827+   5  Extended
/dev/sdb5            2348        2434      698796   82  Linux swap / Solaris
 
Could you plz point out what I'm missing here....
 
Cheers
David

---

### Post by caljohnsmith on 2008-11-11
First off, you don't have to copy all your Ubuntu boot files to your Fedora HDD; Grub can easily boot your Ubuntu entirely from the slave drive. :) I would recommend simply linking to the Ubuntu's menu.lst in your Fedora's menu.lst by doing:
```
title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst
```
That way when you get new kernel upgrades in Ubuntu, the Grub menu for Ubuntu should be automatically be updated, so you won't have to copy over the new boot stanzas to your Fedora partition. How about giving that a shot and letting me know how it goes.

---

### Post by ub007 on 2008-11-12
> title Ubuntu Grub Menu
configfile (hd1,0)/boot/grub/menu.lst

Tried this,but got the error:

> Boting Ubuntu Grub menu'

configfile (hd1,0)/boot/grub/menu.lst
Error 21: selected disk doesnot exist  

---

### Post by caljohnsmith on 2008-11-12
How about posting the following to clarify your setup:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'

```
Next go ahead and reboot, and when you get the Grub menu, press "c" to get the Grub command line, and type:
```
grub> geometry (hd
```
And press TAB for tab-completion. Does that show both (hd0) and (hd1)? If so, do:
```
grub> geometry (hd1)
```
And does that show three partitions or only two?

---

### Post by ub007 on 2008-11-12
[root@localhost ~]# dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
[root@localhost ~]# dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
0000

[root@localhost ~]# dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
[root@localhost ~]# dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff00


> grub> geometry (hd and i press TAB

grub> geometry (hd0,  //doesnt show me hd1

i press one more TAB and it gives

possible partitions are :
Partition num 0,....
Partition num 1
Partition num 2

But it doesnt show me **hd1**

---

### Post by caljohnsmith on 2008-11-12
That's interesting, so on start up Grub is not even seeing your other HDD. From the fdisk output in your first post, I assume that Ubuntu is on sdb? If that is true, on start up Grub is only seeing your sdb drive it looks like, since it is finding three partitions (your sda drive has only two partitions). If you do the geometry command again on start up, it should also show the size of the drive in sectors; if you take that number and multiply it by .000512, you will get the size of the drive in MB. So does that match the size of your sdb drive? Are you sure you are booting the Fedora sda drive on start up? Or do I have that backwards--is Fedora on sdb and Ubuntu on sda?

---

### Post by ub007 on 2008-11-12
Sorry for the confusion.I re-installed fedora yesterday with 3 partitions.Everything else is exactly the same as mentioned in my first post.Only change is i reinstalled both Fedora & Ubuntu with 3 partitions apiece.
So
:
/sda - Fedora (Master hard disk)
/sdb - Ubuntu (Slave disk)

I followed the exact procedure as in 1st post:
> 1)installed fedora on the first disk and as the only disk.
2)disconnected the fedora hard disk.
3)installed ubntu on the second disk and as the only disk.
4)Once the Ubuntu install was finished, I moved that disk to slave and re-connected the Fedora disk as master. Booted Fedora and copied the UBuntu boot stanza to the Fedora boot loader. 


So the 3 partitions spotted by Grub belong to sda (Fedora) and I assume **Grub is not even seeing the other HDD**

---

### Post by caljohnsmith on 2008-11-12
> **ub007 said:**
> 
So the 3 partitions spotted by Grub belong to sda (Fedora) and I assume **Grub is not even seeing the other HDD**
Unfortunately, it looks like that is the bottom line; Grub is not able to detect your second HDD on start up. I would go into your BIOS and try changing any settings you have related to your HDD to see if you can at least get Grub to see the 2nd HDD. I would recommend writing down any BIOS settings that you change so you can revert back if necessary. The BIOS settings for your HDD you would want to look for would be "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. Good luck and let me know how it goes.

EDIT: I just realized, have you checked how you have the jumper cables set on your 2nd HDD? I would think you would want to set it for slave if it isn't all ready.

---

### Post by ub007 on 2008-11-12
Finally,Finally.. got it working!!!!!!!!!!!!!!!! :guitar:


Initially,the jumper settings were -master(Fedora) drive on CS and Ubuntu drive on SLAVE.I set both the jumpers to CS and hd1 was detected by grub!

---

### Post by caljohnsmith on 2008-11-12
That's great news, glad it's finally working. Cheers and have fun in LinuxLand. :)

---

### Post by ub007 on 2008-11-13
i might well ask you this too....One of the reasons i chose to have Fedora & Ubuntu on separate hard disks was,initially when i installed ubuntu on the same disk **after Fedora**,it seemed to overwrite Fedora's grub....

I had
/dev/sda1 - Fedora
/dev/sdab - Fedora
/dev/sda1 - swap (Fedora)
/dev/sda4 -Ubuntu 

It directly boots to Ubuntu as if that were the only OS....there surely must be a way to prevent that....  
What should I do to prevent this happenning...?
Copying fedoras stanza to the Ubuntu grub works,but is there any other way...hows does it over write anyway..?

---

### Post by caljohnsmith on 2008-11-13
You're right, the Ubuntu installer will by default install Grub to the MBR (Master Boot Record) of (hd0), which is the same as /dev/sda, so it will overwrite Fedora's Grub in the MBR. If you want Fedora to handle booting all your OSes, then when you go through the Ubuntu installer, just click the "advanced" button at the end of the installation process, and specify to have Grub installed to /dev/sda4 (sda4 being your Ubuntu partition) instead of (hd0). That way Fedora's Grub in the MBR will still be in charge of booting, and you can boot Ubuntu using the previous "configfile" method I gave, or simply copying over your Ubuntu boot stanzas to your Fedora's menu.lst. 

But you don't have to reinstall Ubuntu/Fedora to correct any booting problems with Grub. If Ubuntu overwrites Grub in the MBR, you can easily reinstall Grub to the MBR and have it point to the Fedora partition instead of the Ubuntu partition for its boot files. Let me know if you would like specifics of how to do that, and if so, please post:
```
sudo fdisk -lu
```
And identify all your partitions. Otherwise let me know how it goes. :)

---

### Post by ub007 on 2008-11-14
Many Thanks

I reinstalled Grub to the MBR and had it point to Fedora partition by

> grub> root (hd0,0)
grub> (hd0)  

This works fine and now I have dual boot between Fedora & Ubuntu on /sda.However you mentioned 'have Grub installed to /dev/sda4 ' from the advanced option.I noticed the same option from fedora -'whether I need grub installed to MBR or the first sector of the partition'.Is there any advantage of having the Ubuntu Grub installed to dev/sda when compared to re-installing MBR with fedora grub & have it point to the Ubuntu kernel image?


Sorry for being a pain...Now that I have ubuntu & fedora on the first drive,i wish to boot to windows XP from the second drive -/hdb.

Well to add more clarity -

I have Fedora on my first hard disk, WindowsXP on the second hard disk. I installed both OS's while their respective drives were the only drives in the computer. I then moved the XP drive to slave while re-installing the Fedora drive as master. Fedora's boot loader takes over because it's the first bootable drive. 

Now The Fedora drive is /dev/sda and the XP drive is /dev/sdb. 

I edited /boot/grub/menu.lst (Fedora grub) to include :

> title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

Now when i reboot & select Windows XP from the menu I get

> Booting Windows XP

rootnoverify (hd1,0)
makeactive
chainloader +1

No error msg,but no signs of bootings either,the screen remains for 5 mins,finally I cold boot it again.What am i doing wring here?

Cheers
David

---

### Post by caljohnsmith on 2008-11-14
> **ub007 said:**
> 
This works fine and now I have dual boot between Fedora & Ubuntu on /sda.However you mentioned 'have Grub installed to /dev/sda4 ' from the advanced option.I noticed the same option from fedora -'whether I need grub installed to MBR or the first sector of the partition'.Is there any advantage of having the Ubuntu Grub installed to dev/sda when compared to re-installing MBR with fedora grub & have it point to the Ubuntu kernel image?
There's really no advantage; it's simply a matter of deciding which distro you want to be in charge of booting, or in other words, which distro has the Grub menu that gets loaded on start up. :)
> **ub007 said:**
> 
Sorry for being a pain...Now that I have ubuntu & fedora on the first drive,i wish to boot to windows XP from the second drive -/hdb.

Well to add more clarity -

I have Fedora on my first hard disk, WindowsXP on the second hard disk. I installed both OS's while their respective drives were the only drives in the computer. I then moved the XP drive to slave while re-installing the Fedora drive as master. Fedora's boot loader takes over because it's the first bootable drive. 

Now The Fedora drive is /dev/sda and the XP drive is /dev/sdb. 

I edited /boot/grub/menu.lst (Fedora grub) to include :
```
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1 
```

OK, I see the problem; Windows insists on being booted from the first boot drive, so if you try and boot it from the second boot drive, you have to use Grub's mapping technique to fool Windows into thinking it is being booted from the first boot drive:
```
title Windows XP
rootnoverify (hd1,0)
[COLOR="Blue"]map  (hd0) (hd1)
map  (hd1) (hd0)[/COLOR]
makeactive
chainloader +1 
```
Give that a shot and let me know how far you get. :)

---

### Post by ub007 on 2008-11-14
> map  (hd0) (hd1)
map  (hd1) (hd0)

Yep,that did the trick.Thanks a ton. :guitar:

---

### Post by caljohnsmith on 2008-11-14
That's great news; cheers and enjoy all your OSes. :)

:popcorn:

---

