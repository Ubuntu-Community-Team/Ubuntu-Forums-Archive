---
title: "Windows wont boot after Lucid install"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bootydancechamp on 2010-04-10
Hello I have a dual boot with Vista and Ubuntu.  Everything was fine until I installed Lucid beta 1.  Lucid works great, however Vista will not boot.  It still shows up on grub but when it is selected the computer reboots.  I share this computer with my wife and I really need to be able to boot windows as well.  

This is what I get from sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       40014   302505808+   7  HPFS/NTFS
/dev/sda3           40015       41345    10062360    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4c3d76f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2            1217       38913   302801121+   5  Extended
/dev/sdb5            1217       38662   300784963+  83  Linux
/dev/sdb6           38663       38913     2016126   82  Linux swap / Solaris

What is my next step?

---

### Post by snip3r8 on 2010-04-10
A bit more information would help,mount all your drives ,run "df" then post the output.

---

### Post by Bootydancechamp on 2010-04-10
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1              9614116   4282092   4843652  47% /
none                   1543692       332   1543360   1% /dev
none                   1547844      1452   1546392   1% /dev/shm
none                   1547844        76   1547768   1% /var/run
none                   1547844         0   1547844   0% /var/lock
none                   1547844         0   1547844   0% /lib/init/rw
/dev/sdb5            296065224  73522872 207503104  27% /home
/dev/sda1            302505808 195294944 107210864  65% /media/HP
/dev/sda3             10062356   9100432    961924  91% /media/FACTORY_IMAGE

---

### Post by clhsharky on 2010-04-10
HI

Lucid has its own section, its till in testing.

Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Sharky

---

### Post by snip3r8 on 2010-04-10
Ok the way your drives are named is confusing me a little,did you use 2 different drives or did you partition to install Lucid?

---

### Post by Bootydancechamp on 2010-04-10
Two different drives.

---

### Post by snip3r8 on 2010-04-10
ok ,im assuming you had both drives plugged into your machine when you installed(my own experience showed me that windows doesnt like this).If you have just your windows drive plugged in ,does windows start?

---

### Post by Bootydancechamp on 2010-04-10
No it doesn't.  It comes up with a grub error, no such device found.  With ubuntu drive only grub comes up and will load ubuntu, but if i choose windows it gives the same error, no such device found.

---

### Post by snip3r8 on 2010-04-10
Thats quite a puzzle,i dont know if this will help you but give it a try :
try running a repair on your windows,i think that's what they are saying in that thread ,and its worked for me before

[http://ubuntuforums.org/showthread.php?t=1447627](http://ubuntuforums.org/showthread.php?t=1447627)

---

### Post by jnmjr on 2010-04-10
> **Bootydancechamp said:**
> No it doesn't.  It comes up with a grub error, no such device found.  With ubuntu drive only grub comes up and will load ubuntu, but if i choose windows it gives the same error, no such device found.

Seems your MBR in win drive is corrupt. From your posting looks like Linux and Grub are installed in SDB drive, assuming Win is on SDA, open your terminal in Linux run this:

sudo grub-install /dev/sda

enter password when asked...... you will not see it when you enter it don't worry
after Grub installs type:

sudo update-grub

You should see all your OS's in the Grub menu.... restart and try Windows. 

 If by chance Grub takes a very long time to boot, go into your BIOS and select   Linux drive as your boot drive, that will correct booting lag.

---

### Post by snip3r8 on 2010-04-11
[http://ubuntuforums.org/showthread.php?t=1451472](http://ubuntuforums.org/showthread.php?t=1451472)

thought this might help . . .

---

### Post by Bootydancechamp on 2010-04-11
> **jnmjr said:**
> Seems your MBR in win drive is corrupt. From your posting looks like Linux and Grub are installed in SDB drive, assuming Win is on SDA, open your terminal in Linux run this:

sudo grub-install /dev/sda

enter password when asked...... you will not see it when you enter it don't worry
after Grub installs type:

sudo update-grub

You should see all your OS's in the Grub menu.... restart and try Windows. 

 If by chance Grub takes a very long time to boot, go into your BIOS and select   Linux drive as your boot drive, that will correct booting lag.


Can I do this from a Live cd?

---

### Post by kansasnoob on 2010-04-11
What you describe sounds rather like this problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

But in order to really troubleshoot this I'd need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Bootydancechamp on 2010-04-11
Well, I have already reinstalled vista on the first drive and now I cant get to Linux.  I tried this 

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but when i tried  
    setup (hd0) 
it said that partition could not be mounted.  So now I am trying to get grub to let me in linux.  When I boot my machine it goes straight into Vista.  Any ideas?

---

### Post by kansasnoob on 2010-04-11
> **Bootydancechamp said:**
> Well, I have already reinstalled vista on the first drive and now I cant get to Linux.  I tried this 

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

but when i tried  
    setup (hd0) 
it said that partition could not be mounted.  So now I am trying to get grub to let me in linux.  When I boot my machine it goes straight into Vista.  Any ideas?

That won't work because it's for legacy grub and Karmic and Lucid both use grub2. You need to follow these instructions:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by Bootydancechamp on 2010-04-12
> **kansasnoob said:**
> That won't work because it's for legacy grub and Karmic and Lucid both use grub2. You need to follow these instructions:

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)


Followed these instructions and installed grub to Linux drive like he says.  Did not work, windows boots.  If I disconnect windows drive grub comes up and will let me boot linux.

---

### Post by Bootydancechamp on 2010-04-12
I downloaded and burned super grub disc.  Would this work to fix my grub?

[Boot with either Super Grub Disk or Super Grub2 Disk your Linux distribution]("http://www.supergrubdisk.org/wiki/Howto_Boot_Linux_only")
# sudo -i # Sudo systems like Ubuntu
# su # Non sudo systems only
# grub-mkconfig
# grub-install /dev/sda # It might be hda in some cases.
# update-grub
# You are done.

---

### Post by bapoumba on 2010-04-12
Moved to Lucid.

---

### Post by kansasnoob on 2010-04-12
> **bootydancechamp said:**
> i downloaded and burned super grub disc.  Would this work to fix my grub?

[boot with either super grub disk or super grub2 disk your linux distribution]("http://www.supergrubdisk.org/wiki/howto_boot_linux_only")
# sudo -i # sudo systems like ubuntu
# su # non sudo systems only
# grub-mkconfig
# grub-install /dev/sda # it might be hda in some cases.
# update-grub
# you are done.

no!

---

### Post by kansasnoob on 2010-04-12
> **Bootydancechamp said:**
> Followed these instructions and installed grub to Linux drive like he says.  Did not work, windows boots.  If I disconnect windows drive grub comes up and will let me boot linux.

You're going to have to be patient. I had to sleep :P

Impatience already caused you to reinstall Windows which was almost certainly not necessary. From what you describe the original problem was probably caused by installing grub to the Windows **partition**!

The current problem would seem to be that you've installed grub to the MBR of /dev/sdb which will only work if the BIOS and/or cabling is set to boot /dev/sdb first.

In this case you should be just fine installing grub to the MBR of the Windows **drive**, in this case /dev/sda.

The reason I highlighted the words "partition" and "drive" is that people make the mistake of installing grub (any version) to a partition (such as sda1, sdb2, etc) instead of to the MBR of the drive itself.

Installing grub to a partition is almost never a good idea, and absolutely never a good idea with a Windows partition!

So, in this case, simply repeat what you did to install grub to /dev/sdb, only install it to /dev/sda. If the info (fdisk -l) in your original post is still correct:

```
sudo mount /dev/sdb1 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

Note: to be sure Lucid is mounted run "lsb_release -a" if you wish.

```
grub-install /dev/sda
```

If that should show any errors run:

```
grub-install --recheck /dev/sda
```

Then just exit and unmount:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Now, if you ever want to restore a Windows readable MBR to /dev/sda that can also be done using an Ubuntu Live CD just by:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Note: If you should do that from an installed Ubuntu you should run "sudo apt-get remove lilo" when you'r done to prevent a possible (though doubtful) conflict with grub.

It's all easy once you know :)

---

### Post by Bootydancechamp on 2010-04-12
Thank you so much Kansasnoob.  You were right on all counts.  I was impatient and reinstalled windows w/o having to (luckily I was able to pull all needed files to Ubuntu drive) and your fix worked.  Again, thank you so much.

---

