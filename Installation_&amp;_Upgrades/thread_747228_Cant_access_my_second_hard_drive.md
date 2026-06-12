---
title: "Cant access my second hard drive"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by philipluna66 on 2008-04-06
I have installed Ubuntu 6.06 on my old computer I put in a spare hard drive I had WHich worked OK when windows xp was runing.Now I have wiped off windows and installed Ubuntun 6.06 on my 8 gig hard drive and on the 13 gig slave I was going to store my photos etc but In on my computer it picks it up but will not let me access it any ides??/ Please keep youre replys simple as I am new to Linux

---

### Post by Pumalite on 2008-04-06
Post:
sudo fdisk -lu

---

### Post by philipluna66 on 2008-04-06
> **Pumalite said:**
> Post:
sudo fdisk -lu
Thanks now I know it is there how do I make it accessable to save things to it???

---

### Post by vanadium on 2008-04-06
You must provide the information here if you want help. In addition to the command "sudo fdisk -l" I suggest you also post the output of the command "mount" so that we can see what is mounted and what not. Run both commands, copy the output and then past it here in a message. This way we can see how the system looks and know what might be wrong.

---

### Post by Pumalite on 2008-04-06
Copy and paste the output and I will be able to help you.

---

### Post by philipluna66 on 2008-04-06
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         981     7879851   83  Linux
/dev/hda2             982        1027      369495    5  Extended
/dev/hda5             982        1027      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 13.6 GB, 13672931328 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1662    13349983+   7  HPFS/NTFS
philip@philip-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-51-386/volatile type tmpfs (rw)
philip@philip-desktop:~$
Hope this is what you need Thanks

---

### Post by Pumalite on 2008-04-06
Go to Terminal:
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sdb1 /media/windows

---

### Post by philipluna66 on 2008-04-06
philip@philip-desktop:~$ sudo mkdir /media/windows
mkdir: cannot create directory `/media/windows': File exists
philip@philip-desktop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/windows
mount: unknown filesystem type 'ntfs-3g'
philip@philip-desktop:~$
This was the reply

---

### Post by philipluna66 on 2008-04-06
Can I just format the slave hard drive and start again. There is nothing on there I need

---

### Post by Pumalite on 2008-04-06
Format ext3 with gparted.
sudo aptitude install gparted
At the Terminal:
gparted

---

### Post by philipluna66 on 2008-04-06
gparted.
bash: gparted.: command not found
philip@philip-desktop:~$ sudo aptitude install gparted
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs8 ntfsprogs
The following NEW packages will be installed:
  gparted libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs8 ntfsprogs
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1620kB of archives. After unpacking 5898kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libntfs8 1.12.1-1 [91.0kB]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main libglibmm-2.4-1c2a 2.10.4-0ubuntu1 [125kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libfuse2 2.4.2-0ubuntu3 [41.2kB]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main libgtkmm-2.4-1c2a 1:2.8.8-0ubuntu1 [915kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main ntfsprogs 1.12.1-1 [210kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main gparted 0.1-0ubuntu10 [238kB]
Fetched 1620kB in 57s (28.1kB/s)
Selecting previously deselected package libglibmm-2.4-1c2a.
(Reading database ... 78303 files and directories currently installed.)
Unpacking libglibmm-2.4-1c2a (from .../libglibmm-2.4-1c2a_2.10.4-0ubuntu1_i386.deb) ...
Selecting previously deselected package libgtkmm-2.4-1c2a.
Unpacking libgtkmm-2.4-1c2a (from .../libgtkmm-2.4-1c2a_1%3a2.8.8-0ubuntu1_i386.deb) ...
Selecting previously deselected package gparted.
Unpacking gparted (from .../gparted_0.1-0ubuntu10_i386.deb) ...
Selecting previously deselected package libntfs8.
Unpacking libntfs8 (from .../libntfs8_1.12.1-1_i386.deb) ...
Selecting previously deselected package libfuse2.
Unpacking libfuse2 (from .../libfuse2_2.4.2-0ubuntu3_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_1.12.1-1_i386.deb) ...
Setting up libglibmm-2.4-1c2a (2.10.4-0ubuntu1) ...

Setting up libgtkmm-2.4-1c2a (2.8.8-0ubuntu1) ...

Setting up gparted (0.1-0ubuntu10) ...

Setting up libntfs8 (1.12.1-1) ...

Setting up libfuse2 (2.4.2-0ubuntu3) ...

Setting up ntfsprogs (1.12.1-1) ...
That is what happened But when I go into computer and click on the icon it still says the same 
error: device /dev/hdb1 is not removable

error: could not execute pmount Thanks for all your help

---

### Post by Pumalite on 2008-04-06
You have to fire off your gparted from the Terminal, point to your 2nd drive and format it.

---

### Post by philipluna66 on 2008-04-06
SORRY i didnt understand that this is all new to me being dare I say a windows veteran

---

### Post by Pumalite on 2008-04-06
That's OK. In no time you'll be a Guru.

---

### Post by vanadium on 2008-04-07
It might be easier for you to format the drive using the command line since in the mean time you are used to it anyway. This command will format your hdb1 partition as ext3:

sudo mkfs -t ext3 /dev/hdb1

On your Ubuntu version, write support for ntfs volumes is not available. If you do not need to recover data from that drive, reformatting it in a fully Linux supported filing system is the best you can do.

This will not be the end of the story, though. After the formatting, there will be two further steps: (1) mounting the drive automatically using /etc/fstab and (2) giving yourself permissions to use the drive. Just come back here when you are ready for that: it is only a few more commands at the terminal that we can easily provide.

---

### Post by philipluna66 on 2008-04-07
Thankyou for all you're help BUT in desperation I had an idea to format my slave H/D with the Ubuntu cd but unfortunately it installed Ubuntu on my slave hard drive and now it will not let me access my first hard drive. I have been in the bios and the order it boots is CD then h/d 1 then Slave But my slave hard drive seems to have taken over SORRY for making it worse

---

### Post by vanadium on 2008-04-07
Now, the time to use gparted might have come. In fact, it could all be repaired, but probably would require more experience than you have now. Anyway, it would surprise me that the new install would not automatically have recognized and mounted your other drive under /media. Probably, though, you will not have write permissions on that volume.

---

### Post by philipluna66 on 2008-04-07
Sorry I dont understand gparted I am a little slow you have to explain it to me looked in my Ubuntu for non geeks book and cant find anythin. Iv tried going into bios. removing the slave hard drive and it still wants to boot from the slave. I have been working on the main drive all week but if I have to shpuld I slap in the disk and start again and put it all down to experience.

---

### Post by Pumalite on 2008-04-07
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by philipluna66 on 2008-04-07
Thanks for the reply I will have a go tomorow Its late hear and my brain is dying fast THANKS again

---

