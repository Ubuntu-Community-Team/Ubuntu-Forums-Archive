---
title: "Grub for dual booting"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by twoviper on 2008-02-02
Hello, I partitioned my hard drive on my laptop into 2 partitions.  I installed ubuntu first on the second partition and then windows xp on the first partition.  I have booted ubuntu before I installed windows and it works but then of course when I installed windows I lost my grub boot loader.  I installed grub somewhere and when I boot my laptop it goes to the grub boot loader when I turn on the laptop.  It shows that I have ubuntu installed on both partitions and when I select any of them to boot it gives me "Error 17: unable to mount device".
On my second attempt to get the Grub boot loader working these were my results:
root@ubuntu:~# sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9397    75481371    7  HPFS/NTFS
/dev/sda2            9398       18703    74750445   83  Linux
/dev/sda3           18704       19457     6056505    5  Extended
/dev/sda4           19081       19457     3028221   82  Linux swap / Solaris
/dev/sda5           18704       19080     3028189+  82  Linux swap / Solaris
root@ubuntu:~# sudo mount /dev/sda2 /mnt
root@ubuntu:~# sudo grub-install —-root-directory=/mnt /dev/sda
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

Any help to get my OSs to boot?

---

### Post by logos34 on 2008-02-02
check /boot/grub/menu.lst.  ubuntu root should be (hd0,1) and windows (hd0,0).

It might be better to reinstall windows first, then ubuntu.

---

### Post by louieb on 2008-02-02
[INDENT]>  root@ubuntu:~# sudo mount /dev/sda2 /mntMay be a problem here. /mnt usually contains sub directories - Just wondering what you are trying to do here?

[/INDENT]

---

### Post by twoviper on 2008-02-02
> **logos34 said:**
> check /boot/grub/menu.lst.  ubuntu root should be (hd0,1) and windows (hd0,0).

It might be better to reinstall windows first, then ubuntu.

how would I do that?

---

### Post by twoviper on 2008-02-02
O sorry I meant to check the menu.lst not reinstall both of the OSs and btw why would I even have to install windows again wouldn't just reinstalling ubuntu be enough to fix the problem, that would be my last resort though

---

### Post by logos34 on 2008-02-03
louieb is right--you should have created a subdir mount, like:

sudo mkdir /mnt/**ubuntu**
sudo mount -t ext3 /dev/sda2 /mnt/ubuntu

etc...

once it's mounted go to check /boot/grub/menu.lst, but root probably correct if you were able to boot it initially before adding windows.

Sure, try reinstalling just ubuntu.  Or try [reinstalling grub from the shell.]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by twoviper on 2008-02-03
ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo check /boot/grub/menu.lst
sudo: check: command not found

how come I can't check the menu.lst, am i typing it in wrong?

---

### Post by confused57 on 2008-02-03
> **twoviper said:**
> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo check /boot/grub/menu.lst
sudo: check: command not found

how come I can't check the menu.lst, am i typing it in wrong?
Try:
```
gedit /mnt/ubuntu/boot/grub/menu.lst
```

If you want to edit your menu.lst preface the above with gksudo:
```
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

Added:  Sorry logos34, you weren't logged in when I replied.

---

### Post by logos34 on 2008-02-03
> **twoviper said:**
> ubuntu@ubuntu:~$ sudo mkdir /mnt/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /mnt/ubuntu
ubuntu@ubuntu:~$ sudo check /boot/grub/menu.lst
sudo: check: command not found

how come I can't check the menu.lst, am i typing it in wrong?

you took me too literally...and you have to get the path correct.  Try:

sudo gedit /mnt/ubuntu/boot/grub/menu.lst

---

### Post by twoviper on 2008-02-03
> **logos34 said:**
> you took me too literally...and you have to get the path correct.  Try:

sudo gedit /mnt/ubuntu/boot/grub/menu.lst

when I type in sudo gedit /mnt/ubuntu/boot/grub/menu.lst it just gives me an empty menu.lst

O and BTW I followed the instructions for reinstalling grub from shell and it does give me the grub boot loader but when I try to select any of the OSs to boot (which are all Ubuntu, none of them windows) it gives me Error 17: unable to mount selected partition

---

### Post by confused57 on 2008-02-03
> **twoviper said:**
> when I type in sudo gedit /mnt/ubuntu/boot/grub/menu.lst it just gives me an empty menu.lst

O and BTW I followed the instructions for reinstalling grub from shell and it does give me the grub boot loader but when I try to select any of the OSs to boot (which are all Ubuntu, none of them windows) it gives me Error 17: unable to mount selected partition
menu.lst is as in "list", not "first"

Another thing you could try is when you boot your computer, highlight your first Ubuntu entry, press "e", then highlight the line with root, press "e" again, then change root from (hd0,0) to (hd0,1), press "enter", then "b" to boot.

---

### Post by twoviper on 2008-02-03
OMG you don't know how excited I am to see my old desktop and my beloved cube again! Thanks so much confused57!  So to boot windows would I just select the second ubuntu and change the root to hd0,0?

---

### Post by confused57 on 2008-02-03
> **twoviper said:**
> OMG you don't know how excited I am to see my old desktop and my beloved cube again! Thanks so much confused57!  So to boot windows would I just select the second ubuntu and change the root to hd0,0?
Glad it worked, but this method of booting is only temporary...you'll need to edit your menu.lst to make it permanent:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
change ALL your Ubuntu entries in the line with root to (hd0,1)...also, you'll need to change the line with #groot to (hd0,1):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

You'll need to add a separate entry to the very bottom of your menu.lst to boot Windows:
```
title  Windows XP
root  (hd0,0)
makeactive
chainloader +1
```

quit & save

---

### Post by twoviper on 2008-02-03
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b94ddf55-5aea-494a-a667-39135d41680b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=b94ddf55-5aea-494a-a667-39135d41680b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b94ddf55-5aea-494a-a667-39135d41680b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b94ddf55-5aea-494a-a667-39135d41680b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title  Windows XP
root  (hd0,0)
makeactive
chainloader +1
### END DEBIAN AUTOMAGIC KERNELS LIST

would that be right, I would just do it but it just seems like a major change and I don't want to risk losing my OS again.

---

### Post by confused57 on 2008-02-03
Place your Windows entry after the line  ###END DEBIAN AUTOMAGIC KERNELS LIST.

You created a backup of your menu.lst(sudo cp menu.lst menu.lst_backup), which can be restored...but your current entries look OK, as long as you only changed the (hd0,0) to (hd0,1)...it's hard to tell the spacing from your menu.lst and as I mentioned if you just changed the (hd0,1), you should be fine to go.

---

### Post by twoviper on 2008-02-03
Yup both OSs boot like a charm and to think of it I was this close to reinstalling both OSs and all I needed to do was change 5 characters and add 4 lines to my menu.lst.  Thanks again confused57 you really made my day!

---

### Post by confused57 on 2008-02-03
> **twoviper said:**
> Yup both OSs boot like a charm and to think of it I was this close to reinstalling both OSs and all I needed to do was change 5 characters and add 4 lines to my menu.lst.  Thanks again confused57 you really made my day!
I did my share of reinstalling OSes that I couldn't get to boot when I first started using Linux...glad I was able to save you from having to do so.  Enjoy your dual boot.

---

### Post by louieb on 2008-02-03
> **confused57 said:**
> Place your Windows entry after the line  ###END DEBIAN AUTOMAGIC KERNELS LIST.
:guitar:+1 Don't forget. Or your windows entry will disappear the next time there is kernel update.

---

