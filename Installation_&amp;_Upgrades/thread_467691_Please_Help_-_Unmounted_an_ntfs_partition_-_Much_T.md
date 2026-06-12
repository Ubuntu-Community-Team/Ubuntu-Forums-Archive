---
title: "Please Help - Unmounted an ntfs partition - Much Trouble Ensues"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by madsquirrel on 2007-06-08
Hi All,

I'm a super noob to Linux and Ubuntu. I fear I may have permanently damaged my computer. I'll try to describe my situation as best I can.

250GB HD
2.66Ghz Intel Processor
512 Memory

Problem: Something went wrong and when the computer rebooted I see a screen with the following error:

Autochk program not found

Then after a few seconds, the computer would reboot and again they were presented with the same error. An unendless loop of the computer rebooting with seemingly no way to solve it.

Background: I tried to dual boot install ubuntu on my desktop. I mistakenly hit unmount on an ntfs partition and now my previously partition functioning WinXP comp won't boot. I had it previously set up as separate partitons for my crucial data, music, programs etc. Now it all shows up as one 231.47gb ntfs partition. I can provide you all the info you need please ask.

Madsquirrel aka Ubuntu Noob in Trouble

---

### Post by cantormath on 2007-06-08
assuming you did the dual boot correctly, you could, if it does not matter, you could reinstall  ubuntu on to the partition that you had originally installed it too without bricking your Windows install on the other partition.

A second option is using the Super Grub Disk, [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
this disk will help you fix the MBR(master boot record) and potentially correct whatever error occured.

If you have no idea what Im talking about with the partitions, you may have not done a proper dual boot.  You need to make room on the drive to install the linux os by resized the original drive.  You can use the install disk to do this.

Hope that helps.

---

### Post by madsquirrel on 2007-06-08
Unfortunately I was not able to install ubuntu before the error happened. 

More details of the problem:

I was in Gparted trying to setup the swap partition as well as a root and date partition under ext3. I had finished doing this when I clicked on the supposedly locked ntfs partition and mistakenly hit unmount. Then all my new partitions disappeared and a partition under ntfs for the full hard disk space (250gb) appeared. At this point I canceled the install (which was open at the same time) and tried to start windows xp normally. Then I got the, 'autochk not found - skipping autochk' after the XP splash screen - then the computer reboots itself and enters an endless loop.

The data on the unmounted partiton seems to be intact. How do i ensure it stays this way?

I'll try Super Grub disk tonite when i get back from work  but are you sure it won't harm my data? 

Thanks so much for your help,
Madsquirrel

---

### Post by madsquirrel on 2007-06-08
Looking around the forums I found other with the same problem so here is an update.

I've tried using my windows XP cd and recovery console with both the commands fixboot and fixmbr both did not work. 

Trying to look at menu.lst gets a blank document.

Fdisk shows this:-

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30216   242709988+  83  Linux
/dev/sda2           30217       30401     1486012+   5  Extended
/dev/sda5           30217       30401     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 131 MB, 131072000 bytes
32 heads, 32 sectors/track, 250 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         250      127984    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(250, 31, 32) logical=(249, 31, 32)
ubuntu@ubuntu:

When i do :
ubuntu@ubuntu:~$ gedit /boot/grub/device.map
I get a blank document

Hope that helps,
Madsquirrel

---

### Post by logos34 on 2007-06-08
I'd try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Livecd").  It's included on System Rescue CD and [Ultimate Boot CD]("http://www.ultimatebootcd.com/") 
(the latter has utilities up the wazoo and is a really neat item to have around).

---

### Post by madsquirrel on 2007-06-08
Just so I can document my progress in case this happens to anyone else here is still more attempts and I am no closer to a solution.

I used to pmount (I don't know what that is i just saw a suggestion on a thread) and got this info:

ubuntu@ubuntu:~$ pmount-hal /dev/sda1
libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was not set.
process 8766: Applications must not close shared connections - see dbus_connection_close() docs. This is a bug in the application.
Error: device /dev/sda1 is already mounted to /media/disk
Error: could not execute pmount
ubuntu@ubuntu:~$ 

I know that I labeled one of my partitions media to keep all my music in. However that was just one of many partitions.

C: = Programs 20 Gi
D: = CD Drive
E: Swap file 2 to 5 Gi
F: Data 20 Gi
G: Media - 60 Gi
The rest was unpartioned space.

The total drive space was 250 Gi

Any help any of you could give would be great. I'm running out of threads to read and ideas to try out. :(

---

### Post by confused57 on 2007-06-08
I'm not experienced with the problem you're having, but you might want to try the gparted live cd(approx 45 Mb download):
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
it also has testdisk...you might try something like "set active" for your NTFS partition?

---

### Post by cantormath on 2007-06-09
> **madsquirrel said:**
> 
More details of the problem:
I was in Gparted trying to setup the swap partition as well as a root and date partition under ext3. I had finished doing this when I clicked on the supposedly locked ntfs partition and mistakenly hit unmount. Then all my new partitions disappeared and a partition under ntfs for the full hard disk space (250gb) appeared. At this point I canceled the install (which was open at the same time) and tried to start windows xp normally. 
Madsquirrel


Ok, if you have not installed ubuntu, you probably didnt install grub, so Super Grub isnt gonna help tons.  
How much data do you have stored on this machine?
you have a couple options here.....the first thing I think you should do is fix your XP installation, assuming you still want to dual boot.
What I would do is use the live cd to put the partitions back the way they were.  Just dont format the windows partition.  Then try to use the XP cd to restore the XP file system, recovery, not reinstallation.  Once XP is back to normal,  Use the ubuntu installer to resize the hard drive and just choose the new blank partition for the place you want to install ubuntu.  Go with recommend and it will chop up the new partition into swap and all that stuff for you.

If this does not .....or did not.....work....
You can install ubuntu and , depending on how much data you have, backup your stuff from the xp partition to the linux partition. 

When you install ubuntu, again, let the installer setup the partitions.  What I mean is just make a blank partition with the installer, no need to mess with swap and that stuff, just tell the installer to install to the new  partition, it will divide that blank partition up into the necessary partitions  for ubuntu to run.  You basically are just telling the installer to install to the new partition and to go with the recommended partitioning but only on this new portion of the drive.   When you are resizing the drive with the installer, make the new partition big enough so that you can boot into linux and backup your data onto the ubuntu partition.  You can then reinstall XP to the old windows partition.   

After doing this, XP like to mess your grub boot loader up, sooooo, you use the Super Grub Disk to recover and rewrite your grub config, aka, master boot record.  This will not damage your new XP install or your Ubuntu install.  When you are done, you will see a grub menu when you boot, you might need to hit esc when it asks, and you will be able to choose Ubuntu or XP.  

You should then be able restore your backup data to your window partition.   If you want to restore this data while in windows, you will need to install ext2/ext3 support so that Windows can read the drive.  You can also enlarge the windows partition, again with the live cd and gparted, if you would like the windows partition to be larger.

  Just a note
 Linux does not alway automount windows partitions, at least not in dapper.  You may need to mount the windows partition after install to access it.  If linux does not automount the drive, you can add an entry to you /etc/fstab file so that it will.  To ensure that you have read/write capability to a windows partition, you will need to use NTFS-3g to do this. There are tutorials that make this NTFS-3g very easy.  When using NTFS-3g, you need to actually use a ntfs-3g entry in your fstab instead of what you see in fstab by default.......This sounds all very complicated but it is not.  Once you get the ntfs-3g working right and fstab looking right, linux will mount the windows partition on boot.  I believe Feisty Fawn has ntfs-3g support by default.....But dapper does not. 

In the future, 
Dont cancel installs without expecting potential errors.  Also, before you dual boot something, refrag the drive before you resize the partition, this tends to keep you from loosing data.

I really hope this helps, and if you need links to howtos for some of the things I have recommend, please let me know.

---

### Post by madsquirrel on 2007-06-12
Problem solved.

Problem: So apparently what had happened was that Gparted in the ubuntu live cd had changed the type of my NTFS partition.


Solution:

The solution is stated much better here.
[http://www.pchell.com/support/autochknotfound.shtml](http://www.pchell.com/support/autochknotfound.shtml)

1. Get a boot disk
I created a floppy drive boot disk using a friends WinXP machine. Just Format a floppy disk and it gives you the option. This is your disk #1.
2. Get ptedit.exe and save it to floppy disk
I got ptedit.exe a free download from doing a Google search with "PTEdit download" I knew to get this from reading some of the windows forums I've given you links to below. This is your floppy disk #2.

What i did:
Once i got an a: prompt from disk #1.  I popped disk #2 in and  ran ptedit.exe and found that my ntfs partition was labeled as type 83. It should be type 07 - the bootable partition. I changed the type and saved it.

This got me booting to XP fine but i couldn't see any of my partitioned spaces!

So I ran ptedit.exe from the a: prompt again and there was an option to analyse the hardrive. It found all my old partitions labeled "D" for deleted. I changed them all to "P" for primary (you can only have 4) and now everything is back to normal.

All the took was a couple of stressed filled hours trying to figure out what went wrong and trying to solve the problems. I hope i saved you the reader some time. Thank you ubuntu forums for your help! You've created an ubuntu convert.

These links helped my find the solution

[http://www.suggestafix.com/index.php?showtopic=22539](http://www.suggestafix.com/index.php?showtopic=22539)

[http://www.pchell.com/support/autochknotfound.shtml](http://www.pchell.com/support/autochknotfound.shtml)

[http://www.opentechsupport.net/forums/archive/topic/18798-1.html](http://www.opentechsupport.net/forums/archive/topic/18798-1.html)

---

### Post by Albertfrd on 2008-06-11
Hi all,
This is the solution that I take to solve this autochk error on windows, after doing a partition with Gparted to install UBUNTU 8.04.

I started my partition in UBUNTU and installed testdisk pack.
Then I opened a console and run: sudo testdisk, once testdisk is open you have to go to the option [create]/[proceed]/[intel]/[advanced] is there were you can see the  partitions types that you have, on my case the first partition that would have to be NTFS was Linux (type83) and there's the error.
Only if you are sure, and can identify correctly your windows partition you must to select [type], on the list select the 07 HPFS-NTFS option and then proceed, the system will do a question about the current partition, you must be sure to change this to type 07 and write the new type on the disk.
Then if you reboot the computer with Windows, you can see on the boot a new checkdisk before start, don't worry, this is normal.

---

