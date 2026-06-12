---
title: "[SOLVED] Grub error, cannot boot Fedora"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by orbital on 2008-05-19
I have Ubuntu 8.04 installed with a boot loader, and now I installed Fedora 9 on another partition, without a boot loader. Now when I boot select Fedora when booting I get "Cannot mount partition" error. Something wrong with the /boot/grub/menu.lst probably? I tried to modify menu.lst but with no success.

---

### Post by tribaal on 2008-05-19
Could you post your /boot/grub/menu.lst file here please? It's probably just a GRUB setup problem.

You can also try reinstalling GRUB ("grub install"), it *should* detect fedora, and add a menu entry for it.

- Trib'

---

### Post by ajgreeny on 2008-05-19
I think this may be a result of Fedora partitioning by default as LVM, which means it could be unreadable unless you have all the lvm modules installed.  This certainly used to be the case.  I had the same problem a couple of years ago and eventually solved it by installing Fedora on pre-made ext3 partitions.  That did the trick, but it took a while to find out what was going on and was very frustrating for a new Linux user.  Incidentally, I didn't like Fedora then and haven't looked at it again since; too slow and unwieldy package management and configuration for me then.

Use gparted, or whatever you have, to make new ext3 partitions for Fedora, and then install to them when the installer gets to that part.  Make sure you let Fedora format the swap partition or it won't be able to use it (that was so then, anyway, it may have changed now).  You should find now that you can add the appropriate entry to grub to boot to Fedora, though you will need to make sure you get the partition naming right by using ```
sudo fdisk -l
``` in Ubuntu, and copying the partition information to menu.lst

Hope that helps.

---

### Post by orbital on 2008-05-19
I tried reinstalling grub but it didn't help. I have Fedora set up like this in menu.lst:

```
title		Fedora 9
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17.f9.i686 root=/dev/sda5 
initrd		/boot/initrd-2.6.24-17.f9.i686.img
savedefault
boot
```

Any ideas?

---

### Post by didac on 2008-05-19
You can try

```
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-17.f9.i686 root=/dev/hda5 ro
initrd /boot/initrd-2.6.24-17.f9.i686.img
savedefault
```


If your root is in your 5th partition, that is the 4th for root. It counts hda1 as 0,0

Notice the change to hda5 instead of sda5. Fedora reserves sda, sdb to SCSI. Ubuntu uses it by default. Also add ro at the end. 

Don't add boot at the end. That's needed only when you are working from the command line.

Another solution is to boot GRUB to a command line and enter those lines one after another to check whether it recognises them

---

### Post by VMC on 2008-05-19
> **ajgreeny said:**
> I think this may be a result of Fedora partitioning by default as LVM, which means it could be unreadable unless you have all the lvm modules installed.  This certainly used to be the case.  I had the same problem a couple of years ago and eventually solved it by installing Fedora on pre-made ext3 partitions.  That did the trick, but it took a while to find out what was going on and was very frustrating for a new Linux user.  Incidentally, I didn't like Fedora then and haven't looked at it again since; too slow and unwieldy package management and configuration for me then.
This is exactly the problem I had and the same reason why I don't like Fedora. 9 doesn't seem all that different than 6. That LVM I don't much like, plus the fact Fedora created another small boot partition for some reason and ignored the /boot/grub partition. Doesn't even search for another grub.

---

### Post by zvacet on 2008-05-19
You have to know on which partition Fedora is installed.If it is on hda5 then in Ubuntu 

```
sudo cp //boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

and you will see 
### END DEBIAN AUTOMAGIC KERNELS LIST

and below it add 

titile       Fedora
rootnoverify (hd0,4)
makeactive
chainloader +1

save file and close.After restart you should be able to choose which OS you want to boot.

---

### Post by orbital on 2008-05-25
> **didac said:**
> You can try

```
root (hd0,4)
kernel /boot/vmlinuz-2.6.24-17.f9.i686 root=/dev/hda5 ro
initrd /boot/initrd-2.6.24-17.f9.i686.img
savedefault
```


If your root is in your 5th partition, that is the 4th for root. It counts hda1 as 0,0

Notice the change to hda5 instead of sda5. Fedora reserves sda, sdb to SCSI. Ubuntu uses it by default. Also add ro at the end. 

Don't add boot at the end. That's needed only when you are working from the command line.

Another solution is to boot GRUB to a command line and enter those lines one after another to check whether it recognises them

I tried this but still get an error (File not found etc.)

---

### Post by orbital on 2008-05-25
> **zvacet said:**
> You have to know on which partition Fedora is installed.If it is on hda5 then in Ubuntu 

```
sudo cp //boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```

and you will see 
### END DEBIAN AUTOMAGIC KERNELS LIST

and below it add 

titile       Fedora
rootnoverify (hd0,4)
makeactive
chainloader +1

save file and close.After restart you should be able to choose which OS you want to boot.

Tried this as well, and got Error 12: Invalid device requested

---

### Post by zvacet on 2008-05-25
You never posted output of **sudo fdisk -l ** but I looked your previous posts and now I see I overlooked something so try this 

titile Fedora
rootnoverify (hd0,5)
makeactive
chainloader +1

---

### Post by meierfra. on 2008-05-25
Leave out the makeactive. Using "makeactive" on a logical partition gives Error 12.

---

### Post by orbital on 2008-05-25
Again I got an error, unrecognized command

My fdisk -l is:

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        5737    20482875   83  Linux
/dev/sda3           11576       14593    24242085    5  Extended
/dev/sda4            5738       11575    46893735   83  Linux
/dev/sda5           11576       14338    22193766   83  Linux
/dev/sda6           14339       14593     2048256   82  Linux swap / Solaris

```

Right now I have a entry:

title 		Fedora 9
rootnoverify 	(hd0,5)
chainloader 	+1

What seems to be the problem here? I've tried with (hd0,4) and with and without the makeactive line.

---

### Post by didac on 2008-05-26
Let's have another try. Type in a terminal:

```
sudo grub
```

You'll get a grub prompt. Then type:

```
find /boot/vmlinuz-2.6.24-17.f9.i686
```

And post the result. We'll take it from there

---

### Post by orbital on 2008-05-26
> **didac said:**
> Let's have another try. Type in a terminal:

```
sudo grub
```

You'll get a grub prompt. Then type:

```
find /boot/vmlinuz-2.6.24-17.f9.i686
```

And post the result. We'll take it from there

Error 15: File not found :confused:

---

### Post by zvacet on 2008-05-26
```
sudo grub
```

**grub> find /boot/grub/stage1**

Post the output of this command here.

---

### Post by orbital on 2008-05-27
I solved this problem by installing grub on the boot folder of the Fedora partition using the F9 installation dvd. Now I can boot to both Ubuntu and Fedora.

---

