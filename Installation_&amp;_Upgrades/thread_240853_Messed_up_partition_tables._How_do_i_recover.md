---
title: "Messed up partition tables. How do i recover?"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by BoomAM on 2006-08-21
Hi.
Yesterday i nuked my XP installation, leaving a 70Gb partition at the beginning of my drive as free space, and the remaining space being Ubuntu, Swap & IBM R&R.
So i install the vista beta. All was fine after redoing grub.
My problem arrised when i used the partition editor in vista to resize its partition to 35Gb, leaving 35Gb of free space. So i formatted that 35Gb of free space, which windows recognises properly, but, now Grub wont boot, it gets stuck on 'loading stage 1.5', and the supergrub disk cant help me either.
I get the impression that Vista made the extended partition that Ubuntu/Swap/IBM was in, so it could fit the extra partition in. Problem is, that even the gparted tool on the LiveCD cant see anything but one large 'unidentifyed' partition & the vista one.
I used supergrub to boot into Vista, remove the extra partition and re-add the free space onto its own partition, restoring the partitions to how it was, but grub, and nothing else, wont have it.

Please dont tell me that ive lost my Ubuntu installation as i had alot of importent data on it.:( 

Thanks in advance all.

---

### Post by aysiu on 2006-08-21
Maybe this?
[http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)

---

### Post by BoomAM on 2006-08-21
How do i install that?

---

### Post by aysiu on 2006-08-21
I have no idea. I just read about it [here](http://geekblog.oneandoneis2.org/index.php?title=triumph_aamp_tragedy&more=1&c=1&tb=1&pb=1).

---

### Post by BoomAM on 2006-08-21
This is how Gparted on a LiveCD sees my partitions:
[http://www.zen111134.zen.co.uk/Screenshot.png](http://www.zen111134.zen.co.uk/Screenshot.png)
The 2nd partition, sda2, shouldnt be one partition.
It should be a 18Gb ext3 partition for Ubuntu, a 2Gb swap partition & a 4.something IBM R&R partition.

---

### Post by BoomAM on 2006-08-21
> **aysiu said:**
> I have no idea. I just read about it [here](http://geekblog.oneandoneis2.org/index.php?title=triumph_aamp_tragedy&more=1&c=1&tb=1&pb=1).
That doesnt explain how to do it. Its just a story?

---

### Post by sacater on 2006-08-21
if you are installing ubuntu 5.10 like i use, the partitions get overwritten whenver you try to install ubuntu, so if i mess up my partions on a drive just reinstall ubuntu on the drive, it overwrites the partitions u made last.
the partiutions should be like....

10g / (filesystem) bootable flag:on ext3 filesys
--g (u say) /home bootable flag:off  ext3
i did 700mb of swap space

---

### Post by BoomAM on 2006-08-21
> **sacater said:**
> if you are installing ubuntu 5.10 like i use, the partitions get overwritten whenver you try to install ubuntu, so if i mess up my partions on a drive just reinstall ubuntu on the drive, it overwrites the partitions u made last.
the partiutions should be like....

10g / (filesystem) bootable flag:on ext3 filesys
--g (u say) /home bootable flag:off  ext3
i did 700mb of swap space


I cant quite see how that helps me. I want to keep my data intact, not overwrite it.

---

### Post by aysiu on 2006-08-21
Well, I searched around these forums, and no one ever explains how to use GPart. Many people seemed to have success with it, though. No one actually says, "This is what I did." They just say things like "Thanks. GPart rocks!"

---

### Post by BoomAM on 2006-08-21
The website that its on is rubbish, no description of how to use it.
Ive tryed the 'make install' command listed in the source download, but the ubuntu live CD says its an unknown command!?

it seems like the ideal application for what i need, but i cant find a guide on how to use it!?

---

### Post by BoomAM on 2006-08-21
The data must still be relativly intact, as Vista sees all the partitions how they should be.

---

### Post by BoomAM on 2006-08-21
Ive managed to find a debian package that installs fine. And it sees all my partitions fine.
Problem now is finding the command for re-writing the partition table.

I'll post exactely how ive done all this when ive fixed it. :)

---

### Post by aysiu on 2006-08-21
> **BoomAM said:**
> 
I'll post exactely how ive done all this when ive fixed it. :) Yes, please do. Then the next time it happens, I can point someone to this thread. Thanks for being responsible!

---

### Post by LKRaider on 2006-08-21
Actually, gpart is in the universe repositories : [http://packages.ubuntu.com/dapper/admin/gpart](http://packages.ubuntu.com/dapper/admin/gpart)

Unfortunatelly I never used it myself, but the man page for it mentions the -W option, which is to write the guessed partition table to a file or device. There is also the -b option that backups the current partition table.

---

### Post by BoomAM on 2006-08-21
Ive managed to get the old grub menu working now, the problem is that it wont boot into anything, keeps erroring saying:
```

Booting 'Ubuntu, kernel 2.6.15-26-686'

root (hd0,2)
  Filesystem type unknown, partition type 0x82
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...

```


The LiveCD can see all my partitions correctly however. Apart from the one Vista was on. Thats just disappeared, leaving 70Gb at the begginning of my drive.

I can mount, with the LiveCD, my Ubuntu partition, but it wont let me doing anything, i cant copy data to back it all up whatsoever!? Ideas?

---

### Post by LKRaider on 2006-08-21
Probably the layout of the partition changed, and your root is now in (hd0,0) or hd(0,1). Edit your menu.lst accordingly.

---

### Post by BoomAM on 2006-08-21
> **LKRaider said:**
> Probably the layout of the partition changed, and your root is now in (hd0,0) or hd(0,1). Edit your menu.lst accordingly.

Ive changed it to what it should be.
And now i get a different error:
```

Booting 'Ubuntu, kernel 2.6.15-26-686'

root (hd0,1)
  Filesystem type unknown, partition type 0x83
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/sda3 ro quiet splash
  [Linux-bzImage, setup=0x1c00, size=0x170956]
initred /boot/initrd.img-2.6.15-26-686
  [Linux-initrd @ 0x1f949000, 0x6a673d bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
mount: Mounting /dev/sda3 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

```

---

### Post by LKRaider on 2006-08-21
Probably your fstab is also wrong now, so boot from a livecd and edit it so it mounts / from the correct device (/dev/sda2 probably).

---

### Post by BoomAM on 2006-08-22
> **LKRaider said:**
> Probably your fstab is also wrong now, so boot from a livecd and edit it so it mounts / from the correct device (/dev/sda2 probably).
Wheres my fstab then?
How do i edit it?

---

### Post by BoomAM on 2006-08-22
I edit fstab so that the right sda was going to the right mount entry in the file, i rebooted, but still get the same error. :(

##EDIT##
I was looking through the menu.lst file and noticed a few sda3 enteries when they should be sda2. So i edited them accordingly, and it appears to be booting fine.
Only problem now is that it wont use my swap partition, and ive got a 70GB NTFS partition at the begginning of my drive that i want to use for Vista again, but im afraid that if i install it and something messes up, that ii'll have to go through all this palarva again.

---

### Post by BoomAM on 2006-08-22
How do i make my install use the linux swap partition again?

---

### Post by BoomAM on 2006-08-22
Here we go:
To use gpart:
This guide asumes that you have access to a usb thumb drive or something similar, and a LiveCD.

Boot the LiveCD. Browse with Mozilla to:
[http://packages.debian.org/unstable/admin/gpart](http://packages.debian.org/unstable/admin/gpart)
And download the gpart deb file. 
Install it.

Now open terminal.
Run the command: 
```

gpart /dev/hdc 

```
Replace 'hdc' with the name of your HDD, in my case, it was sda.

That will make gpart do a scan of the HDD and display the results. Check to see if the partitions it lists seems correct.

Now, run this command:
```

gpart -W /dev/hdc /dev/hdc

```
This will do the same as the previous command, but will write the partition table to the HDD.

Reboot your computer.
Go back into the LiveCD, and check to see if Gparted sees the partitions correctly, if not, try the above a second time (i did), and it should get the missing partitions right this time.

All done. :)

Resources i used:
This thread. :p
Gpart Homepage: [http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)
Gpart Manual: [http://www.math.ucla.edu/computing/docindex/gpart-man-1.html](http://www.math.ucla.edu/computing/docindex/gpart-man-1.html)
Gpart Download: [http://packages.debian.org/unstable/admin/gpart](http://packages.debian.org/unstable/admin/gpart)
ExtremeTech Article: [http://www.extremetech.com/article2/0,1697,1928207,00.asp](http://www.extremetech.com/article2/0,1697,1928207,00.asp)

Hope this helps someone. :)

---

### Post by LKRaider on 2006-08-22
> **BoomAM said:**
> How do i make my install use the linux swap partition again?

Go to your fstab and edit the line that looks like this:
```
/dev/hda4     none            swap            sw                               0       0
```

Make sure the /dev/hda4 points to your swap partition.
Save fstab and on the terminal write:
```
sudo swapon -a
```
This will activate the use of the swap listed on fstab (like mount does for filesystems).

---

### Post by BoomAM on 2006-08-22
Doesnt matter now.

Problem im having now is that Ubuntu & Vista are installed, both work, but Grub wont 
A) display the list of OS's
&
B) according to the menu.lst file, doesnt see Vista.

Ideas?

---

### Post by LKRaider on 2006-08-22
Add something like this to the menu.lst (taken directly from [Wiki:Recovering Grub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) :

```
title  Microsoft Windows XP Home #An entry for a Windows installation
#If you're reading this guide, you probably want this
root   (hd0,0)
makeactive
chainloader +1
```
Edit as appropriate.

---

### Post by BoomAM on 2006-08-23
Ive added that and put in the relevent information, but it wont boot windows, instead windows errors, saying that winboot.exe isnt a recognised boot file, and it still doesnt display the menu?

I deleted the extended partition i was gonna use as storage and made it a primary, and Vista then boots fine, but still, i dont get the grub menu coming up at all?

---

### Post by LKRaider on 2006-08-23
Is your grub installed to the MBR ? Are you booting through grub right now and just missing the menu or are you booting through something else?

Read the RecoveringGrub wiki, it will be of help. What you are aiming for is to have Grub on the MBR with a menu timeout > 0 ;)

---

### Post by BoomAM on 2006-08-23
> **LKRaider said:**
> Is your grub installed to the MBR ? Are you booting through grub right now and just missing the menu or are you booting through something else?
Im not sure where grub is installed two.
I get about 5 seconds to hit 'esc' to bring up grub, which is fine, because everything works, but i want it so that it was as it was before, where grub booted, shows the menu, and then gave me 30 seconds to choose an OS before it picked the default.

---

### Post by LKRaider on 2006-08-23
Well, then it is just a matter of correctly configuring Grub's menu.lst.

Hmm, let me see...

googling for "grub menu.lst" I found these:
[http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst](http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst)
[http://www.gnu.org/software/grub/manual/grub.html#Menu-interface](http://www.gnu.org/software/grub/manual/grub.html#Menu-interface)

So, what you want to tweak are the "**hiddenmenu**" and "**timeout**" settings.

On the wiki, I found this:
[GrubHowTo::Increasing the GRUB timeout](https://help.ubuntu.com/community/GrubHowto?highlight=%28hiddenmenu%29%7C%28timeout%29#head-886bfff34ca6689ca0fbd206bc34b28c2244cc7e)

Check out also how to add a bootsplash image to the Grub menu on that same page ;)

---

