---
title: "No bootloader in new Ubuntu"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by CptBlack91 on 2010-02-09
Hi,
I have Windows 7 installed, and have just installed Ubuntu 9.10 to the same HD, different partitions, all x64.
When I boot the computer, there are no OS options and it boots straight into Ubuntu.
I have run the command "sudo apt-get install grub2" but this hasn't solved it. Attached are two files which may help (from reading other threads) menu.lst (copied to menucp.txt) and the results from boot_info script.

I think this is very similar to this thread:
[http://ubuntuforums.org/showthread.php?t=1403025](http://ubuntuforums.org/showthread.php?t=1403025)
but I didn't want to hijack his thread so created my own.

Many thanks,
C

---

### Post by gordintoronto on 2010-02-09
It sounds like you installed Ubuntu over top of Windows 7 instead of dual boot.  If you open Accessories/terminal and enter the command :
df -h
what is the result?

---

### Post by CptBlack91 on 2010-02-09
I'm pretty sure I didn't, both my files partition "Data1" (mounted) and 'seven' partition are available.
I did have 2 other OS which I decided to get rid of in this process (Vista x86 and x64) I'm wondering whether the previous bootloader was attached to one of these.

The result from the command "df -h" is:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              46G  2.6G   41G   6% /
udev                  3.0G  256K  3.0G   1% /dev
none                  3.0G  572K  3.0G   1% /dev/shm
none                  3.0G   88K  3.0G   1% /var/run
none                  3.0G     0  3.0G   0% /var/lock
none                  3.0G     0  3.0G   0% /lib/init/rw
/dev/sda3             259G  228G   31G  89% /media/Data1

I have run the 7 install disk to go through the repair option but it cannot locate the HDD driver. However, when I try to find this, C: and D: (seven and Data1) are listed as places to locate the driver and all files are accesible.

Cheers,
C

---

### Post by jocko on 2010-02-10
Of course you have a boot loader, otherwise you would not be able to boot any os. 
But it may be that grub did not detect your windows 7 install, so it did not see the point of activating the boot menu.
Try to regenerate the grub config file by:
```
sudo update-grub
```

---

### Post by CptBlack91 on 2010-02-10
I'm afraid that hasn't worked.

Is there any further information I can give to help clarify things?

I can access a boot menu by pressing f8 during BIOS, 4 options are there (after choosing the HD as the boot device), 2 Ubuntu and 2 memory tests.
I can also mount the windows partition in Ubuntu so it's definitely there.

If the menu is hidden, which is the line that sets this?

Many thanks,
C

Edit:
The output of the update is:
```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```
So I guess it's still not recognising the 7 partition as bootable?


> **jocko said:**
> Of course you have a boot loader, otherwise you would not be able to boot any os. 
But it may be that grub did not detect your windows 7 install, so it did not see the point of activating the boot menu.
Try to regenerate the grub config file by:
```
sudo update-grub
```

---

### Post by Mark Phelps on 2010-02-10
> **CptBlack91 said:**
>  ...I did have 2 other OS which I decided to get rid of in this process (Vista x86 and x64) I'm wondering whether the previous bootloader was attached to one of these.

If Vista was already installed when you installed Win7, it's likely that Win7 installed its new bootloader files to the first NTFS partition it found, in this case, most likely Vista.

When you removed or reformatted that partition, you wiped out your Win7 boot loader and all of its files.

You can restore them by booting from a Win7 DVD and running Startup Repair several times -- may take three passes because it only repairs one thing on each pass.

---

### Post by kansasnoob on 2010-02-10
I think you're missing bootmgr from your Win 7 boot files. You also have mixed legacy grub and grub2 files in Ubuntu.

Look at my posts here:

[http://ubuntuforums.org/showthread.php?t=1403099](http://ubuntuforums.org/showthread.php?t=1403099)

If you need more personalized help send me a brief PM pointing me back to this thread :)

BTW that frequently happens if you move or resize a Win Vista/7 partition using Gparted! Use only Vista and/or 7's own tools to resize 'em!!!

---

