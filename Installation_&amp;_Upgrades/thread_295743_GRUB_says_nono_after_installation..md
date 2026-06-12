---
title: "GRUB says nono after installation."
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by BeBopDeluxe on 2006-11-08
Hello Ubuntists. I have a rather strange problem that occured    after installation of the new Edgy version. Let me first of all describe my harddrive setup. I have one 250 gb SATA II disk in use as C: (/dev/sda) where i have Windows XP installed, one 200 gb PATA drive as D: (/dev/hda) and one 80 gb PATA drive as E: (/dev/hdc).

I attempted to install Ubuntu on the /dev/hdc which went all fine and dandy using the alternative dvd, and i wanted to put GRUB on /dev/hdc as i didnt wanted to mess up MBR on the SATA drive. All went well, no errors, i restarted the box and hit F8 to choose boot disk and opted for the former E: /dev/hdc, gets a nice Ubuntu boot menu and hits the Ubuntu entry in the menu. And from there, nothing is working. I get an Grub error 17 : Cannot mount selected partition, which explains with: This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

After that, i´m stumped. Checking the Ubuntu entry in the boot menu gives this:

root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

As to my limited knowledge it seems OK, but obviously it is not. What can be done to fix this?

---

### Post by BeBopDeluxe on 2006-11-09
First of all, excuse me for maybe doing something stupid or not allowed here. I just wanted to add the information i got from running sudo fdisk -l from the Live-cd, if that might be of any further help.

Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        9557    76766571   83  Linux
/dev/hdc2            9558        9964     3269227+   5  Extended
/dev/hdc5            9558        9964     3269196   82  Linux swap / Solaris
ubuntu@ubuntu:~$

Maybe someone can point me in the correct direction here?

---

### Post by bulldog on 2006-11-09
> **BeBopDeluxe said:**
> Hello Ubuntists. I have a rather strange problem that occured    after installation of the new Edgy version. Let me first of all describe my harddrive setup. I have one 250 gb SATA II disk in use as C: (/dev/sda) where i have Windows XP installed, one 200 gb PATA drive as D: (/dev/hda) and one 80 gb PATA drive as E: (/dev/hdc).

I attempted to install Ubuntu on the /dev/hdc which went all fine and dandy using the alternative dvd, and i wanted to put GRUB on /dev/hdc as i didnt wanted to mess up MBR on the SATA drive. All went well, no errors, i restarted the box and hit F8 to choose boot disk and opted for the former E: /dev/hdc, gets a nice Ubuntu boot menu and hits the Ubuntu entry in the menu. And from there, nothing is working. I get an Grub error 17 : Cannot mount selected partition, which explains with: This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

After that, i´m stumped. Checking the Ubuntu entry in the boot menu gives this:

root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

As to my limited knowledge it seems OK, but obviously it is not. What can be done to fix this?

Try to make root (hd1.0) (hd2.0)
It's a little tricky,but I think your Sata is boot (hd0),IDE prymary (hd1) and your linux secundary IDE (hd2).
Just give it a try by selecting your Ubuntu in GRUB and hit the e to alter it.
If it works you can change it permanant in menu.lst.

---

### Post by BeBopDeluxe on 2006-11-09
Thats sounds like a good idea, i´ll try that and return with results. Thank you!

---

### Post by BeBopDeluxe on 2006-11-09
Hey, you definitely put me on the right track there, my man! :D 
Changing to (hd2,0) did not help, so i continued to try the other harddrives and came up with a working (hd0,0) instead. Great, i'm now using the all new Ubuntu installation. Thanks a million!!!!

---

### Post by emdeem on 2006-11-09
You may want to take a look at /boot/grub/device.map and see if it's correct.  That's the file that maps BIOS drive names/numbers to OS names/numbers.

---

### Post by BeBopDeluxe on 2006-11-09
> **emdeem said:**
> You may want to take a look at /boot/grub/device.map and see if it's correct.  That's the file that maps BIOS drive names/numbers to OS names/numbers.

Interesting,(good idea btw) the device map does not look like it should according to the way i had to change drive to be able to boot Ubuntu.

(hd0)	/dev/hda (200 gb storage drive)
(hd1)	/dev/hdc (80 gb with Ubuntu installed)
(hd2)	/dev/sda (250 gb SATA II with XP installed)

I changed the Ubuntu boot entry from (hd1,0) to (hd0,0) and for the first time it really worked, but the device.map says something different?

Also the XP boot entry says root (hd2,0) and that corresponds well with device.map, but it does not work booting to XP, says ntldr is missing. So what the device.map says and what GRUB sees seems to be two different things?

---

### Post by napsilan on 2006-11-09
> Also the XP boot entry says root (hd2,0) and that corresponds well with device.map, but it does not work booting to XP, says ntldr is missing. So what the device.map says and what GRUB sees seems to be two different things?

What does the menu.lst item corresponding to windows say?

---

### Post by BeBopDeluxe on 2006-11-09
> **napsilan said:**
> What does the menu.lst item corresponding to windows say?

It says:

root (hd2,0)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

And XP wont boot because of missing ntldr. Might there be an error in the mapping?

---

### Post by napsilan on 2006-11-10
if it says missing ntldr, then it's probably a problem on the windows disk.  You might want to try using the windows install disk to fix that.  I think "fixmbr" might do it from the windows recovery console, but it could end up writing over other bootloaders too, so back up grub before you do it.  You can also try using the "default" windows option in grub, however, I do think the problem is on the windows disk.  

title		Windows 95/98/NT/2000
root		(hd2,0)
makeactive
chainloader	+1

---

### Post by BeBopDeluxe on 2006-11-10
> **napsilan said:**
> if it says missing ntldr, then it's probably a problem on the windows disk.  You might want to try using the windows install disk to fix that.  I think "fixmbr" might do it from the windows recovery console, but it could end up writing over other bootloaders too, so back up grub before you do it.  You can also try using the "default" windows option in grub, however, I do think the problem is on the windows disk.  

title		Windows 95/98/NT/2000
root		(hd2,0)
makeactive
chainloader	+1

No, the problem is most definitely not with the windows disk as i can boot it with no problems at all by using the earlier described method of using F8. And there´s no GRUB on the Windows disk as you might see if you read my previous posts on the subject.

GRUB is on /dev/hdc, same disk as Ubuntu is installed on, MBR is on /dev/sda, same disk as Windows XP is on. The GRUB boot entry for XP points to "root (hd2,0)" which SHOULD be correct according to (hd2) /dev/sda (250 gb SATA II with XP installed) but its not. On the other hand, GRUB boot entry for Ubuntu points to "root (hd1,0)" which ALSO should be correct according to (hd1) /dev/hdc (80 gb with Ubuntu installed)but it is obviously not correct because i have to change the boot entry to "root (hd0,0)" to make Ubuntu start. Btw, hd0, according to device.map is (hd0) /dev/hda (200 gb storage drive). So......my conclusion is that GRUB did a lousy job detecting the correct disks or the device.map is totally fubared. Either way, the boot procedure is not working. 

I have very little experience using Ubuntu, but i have installed and tested several other dists based on Debian aswell as Debian itself, and also Suse, Mandriva, Fedora Core et al. Ubuntu is so far the only one that miserable failed in installing GRUB/LILO correct. Go figure.......](*,)

---

### Post by confused57 on 2006-11-10
Maybe you could try the following entry to boot Windows:
```
title                Windows
rootnoverify    (hd1,0)
savedefault
makeactive
map              (hd0) (hd1)
map              (hd1) (hd0)
chainloader +1
```

---

