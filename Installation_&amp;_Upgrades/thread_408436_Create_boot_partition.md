---
title: "Create boot partition"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by epiphiny on 2007-04-13
Hi there,

I originally had a FC6 / windows set up.  I then overwrote the FC6 with ubuntu 6.10.  However, In my FC6 install I had set up grub on a seperate partition, so that a) I could easily add other evaluation os's, and b) I could edit menu.lst in windows via a script, meaning i could create scripts to 'reboot to windows' or 'reboot with ubuntu'.

Unfortunately, it sems that ubuntu has switched my boot loader to a sperate partition.

I seem to be having trouble getting the system to read my boot files from the partition.

What ive done already;
My boot partition is on sda3, so in grub it should be hd0,2.  So this is what i'm doing;

```

sudo grub
grub> find /boot/grub/stage1
 (hd0,3)

grub> root (hd0,2)

grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "embed /grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
 Running "install /grub/stage1 (hd0,2) /grub/stage2 p /grub/menu.lst "... succe
eded
Done.


```

As I understand it, grub should now boot from sda3.  However, re-running find /boot/grub/stage1 returns (hd0,3), which is my ubuntu partition.  Also, I edited the menu.lst files on the two locations (sda4 and sda3), and so I know its always booting using ubuntus version.

Sorry if this is a noobish thing, but I've tried everything from deleting the contents of  /boot and mounting sda3 on it, to trying every concievable combination of root (hdx,x), setup (hdx,x).

Any help would be greatly appreciated, many thanks

---

### Post by Herman on 2007-04-13
Hello epiphiny,
I am guessing then that you have Windows in sda1 probably, and sda2 is maybe your extended partition with your swap sda5 in it?
You are trying to set up sda 3 as a grub partition, and finally sda4 is your Ubuntu partition, would that all be right?
It would be better if you can post a copy of your fdisk output, ```
sudo fdisk -lu
```There are a lot of things in your post that don't make any sense. What is it you are really trying to do?
You said you want to be able to 'edit menu.lst in Windows', but Windows doesn't have any such things as a 'menu.lst', it has a file called boot.ini instead.
Did you mean you want to edit menu.lst in Ubuntu to boot Windows? Ubuntu has a menu.lst file in /boot/grub that should have an operating system entry in it already for you to boot Windows with. Normally that is set up automatically, but in maybe around 1% of installations you may need to edit it to correct some small mistake and get it to work properly.

I can help you install Grub to a separate partition if you really want, that is kind of handy if you want to try out more Linux operating systems and multiple boot. If you want to do that you can start with another partition and mount it. Create a new empty /boot directory in it. Then you need to copy your /boot/grub directory to it from your Ubuntu install, so the grub partition will now have /grub in /boot/grub. You can edit the menu.lst in that now, so it will boot Ubuntu and Windows. 
Then you need to install the Grub *from* the grub partition *to your hard disk's* MBR.
That means you need to do 'root (hd0,2)' (to install grub *from* your grub partition), and setup (hd0), to install Grub *to *MBR.
Then you'll be able to boot the new grub partition sda3 and boot Ubuntu or Windows and add and delete other operating systems.
 
You can already do that now from your Ubuntu's grub though. You just need to re-install Grub to MBR after you install another operating system and add it's entry to your menu.lst file in Ubuntu. That would be an easier way of doing things.

Do you realy mean you just need help with your grub in Ubuntu perhaps?

Regards, Herman :D

---

### Post by epiphiny on 2007-04-13
I want to be able to mount my boot partition in either windows (using ex2ifs) or in ubuntu.  Then, I want a bash script in ubuntu which will change the default boot option in grub's menu.lst to windows, and a bat script in windows that will change the deafult to ubuntu.  This is because my computer is an IBM server, and takes about 5 minutes to boot.  I get bored in this time and wander off, and usually have to do another restart to I can catch the grub bootloader.  I definately don't want to make the dealay any longer though!

I don't want to mount my / partition in windows, as it contains some sensitive data that I don't want a virus to get into, should the worst happen.  Therefore, for security I want to minimze the potential risk by only mounting a /boot partition.

In order to do this in need to get grub to read its grub.conf and its menu.lst from /dev/sda3.

As asked, sudo fdisk -lu leaves; 
```

james@boris:~$ sudo fdisk -lu 
Password:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    54878039    27438988+   7  HPFS/NTFS
/dev/sda2        54878040    56837969      979965   82  Linux swap / Solaris
/dev/sda3        60822090    61030934      104422+  83  Linux
/dev/sda4        61030935   160826714    49897890   83  Linux

```
sda1 is windows
sda2 is swap
sda3 is boot
sda4 is ubuntu

I tried copying  all the files in /boot to /mnt/boot (after sudo mount /dev/sda3 /mnt/boot), but it is still booting from sda4, as shown by the deliberate different configurations I've put in there (added 'this is sda3' in the sda3 grub.conf /menu.lst, etc).

Any ideas very welcome, thanks a lot :D

---

### Post by Herman on 2007-04-13
> I want to be able to mount my boot partition in either windows (using ex2ifs) or in ubuntu. Okay, I can help you with the Ubuntu side of things. ```
sudo mkdir /media/grubpartition
``` ```
sudo mount -t ext3 /dev/sda3 /media/grubpartition
``` That should mount it for you.

Then if you want to copy your Grub files to it you would use the following commands,```
sudo mkdir /media/grubpartition/boot
``````
sudo cp -r /boot/grub /media/grubpartition/boot/
``` Then you just have to run Grub again and install Grub from the partition to MBR, the way I already explained.

I am thinking about what kind of script you might want to use In Ubuntu to achieve the effect you want. The simplest way I can think of is to make two copies of your menu.lst file, one with Windows as the default and the other with Ubuntu as the default and use the script to overwrite one with the other.

A simpler idea that would work would be to just comment out your timeout line in your menu.lst file so you can wander off and your grub menu will wait for you to come back and select your operating system. That would be a lot better and would be easier. That's how I like mine too. ```
sudo gedit /media/grubpartition/boot/grub/menu.lst
``` and comment out your timer, refer to this link, [Setting the timer]("http://users.bigpond.net.au/hermanzone/p15.htm#timer")

Let me know when you get that far or if there is anything there you need further help with,
Regards, Herman :D

---

### Post by epiphiny on 2007-04-13
Ok, I promise this isn't deliberate, but its still not bloody working!  To go through this methodically, here is what I've just done;

1.  Deleted everything on sda3, and then reformatted it.  Overkill I know, but I'm not taking chances!

2.  Copied everything in /boot to sda3/grub.  To do this, I entered the following commands; ```

james@boris:~$ sudo mkdir /media/grubpartition
james@boris:~$ sudo mount -t ext3 /dev/sda3 /media/grubpartition
james@boris:~$ sudo mkdir /media/grubpartition/boot
james@boris:~$ sudo cp -r /boot/grub /media/grubpartition/boot/

```

I then went into grub, tying sudo grub at the terminal.

Commands then were;

```
grub> root (hd0,2)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```

Then, I used gksudo gedit /media/grubpartition/boot/grub/menu.lst to change it from;

```

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
#password --md5 

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
**	We are living in sda4!	**
	lock
root (hd0,0)
	kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
	initrd /boot/initrd.img-2.6.17-11-generic
	boot

title Ubuntu 6.10 Edgy Eft (2.6.17-10-generic) 
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
        initrd /boot/initrd.img-2.6.17-10-generic
        quiet
        boot

title Microsoft Windows XP
	 lock
	 root (hd0,0)
 	 savedefault
  	 makeactive
   	 chainloader +1

```

TO:

```

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
#password --md5 $1$6BKRq1$.XP/F3fdbmiPFaRvK.0aw/



title Ubuntu 6.10 Edgy Eft (2.6.17-10-generic) 
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
        initrd /boot/initrd.img-2.6.17-10-generic
        quiet
        boot

title Microsoft Windows XP
	 lock
	 root (hd0,0)
 	 savedefault
  	 makeactive
   	 chainloader +1

```

This way, pressing 'e' on the recovery mode should pop up a line telling me which partition im on... right?  Well, after a reboot, I don't get either!  Also, I see the deleted recovery mode!  Thanks for all the advice, i feel like tearing my hair out!

---

### Post by Herman on 2007-04-13
Try this, I commented out your timeout, and your hiddenmenu, so your menu will show up, and it'll remain until such time as you return to your computer (coffee cup in hand?) and make a decision about which OS you want to boot this morning.
Your mew Ubuntu boot entry uses the configfile command. That doesn't boot Ubuntu directly because if you do then you'll need to manually update this grub menu yourself every time there is a kernel update in Ubuntu. This way you will be booting to your Ubuntu grub menu and then you select Ubuntu. Ubuntu maintians its own menu.lst file and keeps it up to date with the debian automagic kernels list.
You should also use the configfile command for any other operating systems you add that boot with grub. If they will boot with Lilo or some other bootlaoder, you should install their bootloader to the first sector of their partition and chainload them like Windows.
```
 # grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=1
#timeout=5
splashimage=(hd0,2)/grub/splash.xpm.gz
#hiddenmenu
#password --md5 $1$6BKRq1$.XP/F3fdbmiPFaRvK.0aw/



title Ubuntu 6.10 Edgy Eft configfile on /dev/sda4
        configfile  (hd0,3)/boot/grub/menu.lst

title Microsoft Windows XP
     lock
     root (hd0,0)
      savedefault
       makeactive
        chainloader +1
``` See if that works okay,
Regards, Herman :D

---

### Post by Herman on 2007-04-13
Actually I just thought of a possible problem here that I'm a bit worried about...
If you're still having problems, try opening your grub shell again (sudo grub), and see if yu can 'see'  where you kernel and initrd.img is, ```
grub> find /vmlinuz
```> grub> find /initrd.img
What does the output from those give you?
Regards, Herman

---

