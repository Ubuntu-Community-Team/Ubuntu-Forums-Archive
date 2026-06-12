---
title: "question on 2'nd hard drive install"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by lahook on 2007-11-07
I'm wanting to add a second sata hard drive to my system. The purpose of this is to install vista for game play. What is the best way to install vista on the 2'nd drive without messing with my Ubuntu? Should I add drive, boot with live cd, format 2'nd drive with ntfs then boot with vista and install? Or should I disconnect the Ubuntu drive before I install vista and then reconnect Ubuntu? Then on boot up select which drive to boot from Bios menu. 
The computer is a Dell E520N.
Any help or suggestions will be appreciated  
Thanx

---

### Post by GrimJack on 2007-11-07
Frankly, I'm amazed. This is *very* close to what I'm planning on doing...

I also have a Dell e520 and have a second SATA HDD on the way as of an hour ago! :cool:

Originally, I'd only thought about moving /home and /swap to the new drive, but the idea of throwing XP on a partition for gameplay or for software that doesn't play right under wine is a Good Idea.

I'm subscribing to this thread.

---

### Post by bulldog on 2007-11-07
I think,to avoid any mistake, disconnect the ubuntu hdd and install Vista.

You can add an entry for Vista into the menu.lst,just search the forum and you'll find how.

---

### Post by lahook on 2007-11-07
If I disconnect the Ubuntu and install vista. Will there be any problem with both hard drives connected later? I'm not sure on how it will work with 2 hd's  and selecting which to boot through Bios. (f12 on startup)

---

### Post by bulldog on 2007-11-07
Should'nt be a problem,sata's are both master by default,so you can choose which one to boot.
You can set the ubuntu hdd as first bootdevice in the BIOS and add  Vista in the menu.lst,so you can choose from grub which one you want to boot.
But the F12 should be sufficient.

---

### Post by lahook on 2007-11-07
I was hoping there wouldn't be a problem, but I don't know much about how sata works. This is my first computer with sata drives. I will put the vista in the grub menu list, I just wanted to make sure I could boot to which drive I want without problems or switching cables.
Thanks for the help

---

### Post by lahook on 2007-11-10
I completed the install. It wasn't as easy as I thought it would be.
Here's how it went.
installed 2'nd drive, turned the drive on in Bios
booted with gparted live cd , and then formated with ntfs.
rebooted ubuntu recognized drive (all fine)
put vista cd in and rebooted
tried to install on new formated drive, vista said not acceptable to install
so I re-formated drive with vista, same error
I had to unplug my ubuntu drive and install with only the new drive plugged in
plugged ubuntu drive back in and added vista to /boot/grub/menu.lst

I hope this helps others who try to install vista on a different drive.

---

### Post by bulldog on 2007-11-10
> **lahook said:**
> I completed the install. It wasn't as easy as I thought it would be.
Here's how it went.
installed 2'nd drive, turned the drive on in Bios
booted with gparted live cd , and then formated with ntfs.
rebooted ubuntu recognized drive (all fine)
put vista cd in and rebooted
tried to install on new formated drive, vista said not acceptable to install
so I re-formated drive with vista, same error
I had to unplug my ubuntu drive and install with only the new drive plugged in
plugged ubuntu drive back in and added vista to /boot/grub/menu.lst

I hope this helps others who try to install vista on a different drive.

Well you did know this already,I told you in post three to disconnect the  ubuntu hdd.:)

---

### Post by GrimJack on 2007-11-13
I'd estimate I'm about 75% done with my second SATA hard drive install on the Dell e520 and I'm posting this to clean out a bunch of tabs in my browser that may be of use to anyone trying to do something similar.

The first thing I did was download and burn the Gparted Live CD:
[htttp://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")
And left it in the optical drive when I powered down.

Following that, I opened the case and physically installed the drive. On the Dell e520, there's an empty plastic chassis in the drive bay that you remove, attach to the drive by matching the inward pointing pins to the screw holes on the drive, then slide back into place. (Curiously, this means the drive will be "upside down", with the bottom of the drive facing upwards, as the first drive is.) Dell provides a power connector with exactly enough slack on the wire to connect to the new drive. Then I connected the bundled SATA cable to a vacant SATA port on the motherboard and to the drive.

Powering back up, I went into the BIOS. By default, Dell does not enable SATA ports not in use from the factory, so I had to enter the BIOS and enable the SATA port I connected the new drive to. I also had to (temporarily) alter the boot sequence to make the optical drive the first boot device, so Gparted would boot instead of Ubuntu. Save, exit, reboot.

GParted did not boot into a GUI on the first attempt. I suspect it had something to do with my Nvidia card. It did boot into a GUI on the second attempt, but didn't look much like the screenshots I saw on the Gparted LiveCD page. No desktop, just the Gparted window, but it was working.

By default, GParted was looking at the first drive, with my current Ubuntu install, /dev/sda. Using the drop-down menu on the right of the window, I changed to /dev/sdb and saw the new drive, with no partitions. I created a 50GB NTFS partition for XP and used all the remaining space to create a ext3 partition. (My full intent is to use the second drive to dual-boot XP and to have a dedicated partition for /home.) I told Gparted to create those partitions, exited and shut down.

With the power off, I disconnected the drive with my Ubuntu install, then booted back into the BIOS. I swapped the GParted LiveCD for the XP install disc, then rebooted. The XP installer found the NTFS partition I created and provided the option to install there instead of creating it's own partitions and reformatting, which I did.

When the XP install forces a reboot, I went back into the BIOS and set the new drive as the primary boot device instead of the optical drive, then finished the XP install. When that was done, I shut down, reconnected the Ubuntu drive, and set the BIOS to use it as the primary boot drive, with the new drive (with XP) as the second. Then booted back into Ubuntu.

Once there, there were two tasks to complete: creating the option in GRUB to select between Ubuntu and XP, and making the XP partition read/writable from Ubuntu.

The first thing I did was change the number of times mounting / forces fchk to examine the drive. I've only had to endure this twice so far, and each time it took at least a half-hour to complete. (I think this has a lot to do with the fact that I download a lot and can assume there's a lot of non-contiguous files in there, which is why I want to move /home to it's own partition.) Doing this was pretty simple and directions can be found here:
[http://ubuntuforums.org/showthread.php?t=539244](http://ubuntuforums.org/showthread.php?t=539244)

To mount and enable read/write to the NTFS XP partition, I installed the NTFS Configuration Tool. Instructions here:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Now to the dual boot. The instructions I found are:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
and
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

And because I don't like adding/changing things without knowing the WHYs of various commands, the manual page for GRUB was also useful:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Even with those pages, I still wound up with an error 13 when I tried to boot into XP. To correct this, I used the GRUB manual and:
[http://ubuntuforums.org/showthread.php?t=601918](http://ubuntuforums.org/showthread.php?t=601918)
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

In the end, I discovered that hard drive numbering starts at 0 (hd0, hd1, etc) partition numbering starts at 1 (/dev/sdb1, /dev/sdb2, etc) and I'd pointed menu.lst to the (empty) ext3 partition by mistake. (I've tended to do things The Hard Way because that's how you learn things, which is useful when Things Go Wrong.)

So, now I can boot to Ubuntu or XP with no issues. I still have to move /home to /dev/sdb2, but probably won't tackle that until the weekend.

Hope this is useful to someone. Cheers!

---

