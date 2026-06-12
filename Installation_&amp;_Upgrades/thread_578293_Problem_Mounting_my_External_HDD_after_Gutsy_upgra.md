---
title: "Problem Mounting my External HDD after Gutsy upgrade"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by StanBlast on 2007-10-17
Dear  All, 

After upgrading to Gutsy, I have a problem with mounting my 320G external HD. I didn't use to have this problem running on Feisty. 

Below is the error message that I got and I appreciate any help that I can get here

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda5 /media/sda5/ -o force

Or add the option to the relevant row in the /etc/fstab file:

/dev/sda1 /media/sda5/ ntfs-3g defaults,force 0 0

I have tried force mounting from the terminal and it didn't work. Tried to add that command line in my /etc/fstab file but I couldn't save it cos' I didn't have the permission to. Please help! Thanks!


Stan

---

### Post by chunchengch on 2007-10-17
If you did not shut down Windows normally, then ntfs-3g will not recognize any NTFS partition of the hard drive where Windows is installed, so the only way is to reboot your Windows and then shut it down correctly.

---

### Post by StanBlast on 2007-10-17
Hi Chuncheng, thanks for  responding. I have tried rebooting to Windows and shut it down cleanly and reboot to Ubuntu again...still, I can't mount my HD. I get the same error message. Any more possible solutions? Thanks! :)

---

### Post by logos34 on 2007-10-17
> **StanBlast said:**
> I have tried force mounting from the terminal and it didn't work. Tried to add that command line in my /etc/fstab file but I couldn't save it cos' I didn't have the permission to.

use sudo

i.e.:

**sudo **mount -t ntfs-3g /dev/sda5 /media/sda5/ -o force


to edit and save changes to fstab, open it as root:
[B]
gksudo gedit /etc/fstab[/B]


You might try running from windows a filesystem check with repair option (**chkdsk**) on the usb partition.  Maybe that will fix things

---

### Post by chunchengch on 2007-10-17
I have another Ubuntu 7.10 installed on a external USB HDD which is split into three partitions,NTFS ,reiserfs and linuxswap, here is the /etc/fstab looks like

# Entry for /dev/sdb2 :
UUID=d86f501d-c3f9-4947-93eb-d11bf86deada / reiserfs defaults 0 1
# Entry for /dev/sdb1 :
UUID=2BB39E2759740B1C /media/sdb1 ntfs-3g defaults,locale=zh_TW.UTF-8 0 1
# Entry for /dev/sdb3 :
UUID=ba565480-68a4-425f-a7ce-bc0d5a62e1fa none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,noauto,iocharset=utf8 0 0


I recommend you to check the UUID of all the partitions of your external HDD with the command:

$ sudo vol_id /dev/sdb1

---

### Post by bobhenz on 2007-10-24
I am having the same problem. I upgraded and now my extra hard drive as well as the separate partition where I used to keep all my user files is not mounted.

When I try to mount them manually it says that they are already mounted or the directory is busy.

Also I noticed that the disk-management tool that used to be under System->Administration has disappeared so I have no way of seeing that my hard drive is partitioned.

Can anyone help?

---

### Post by jpmswiss on 2007-10-26
Somewhat a similar story here. I have taken my "media" HDD out of my XP machine and put it in my kubuntu machine. This internal HDD has only data (music/video/photo) files on it. Long story short - i cannot mount it - even with several different mounting options...nft, fat32, ext3, etc, etc..

I have a back up copy on an external HDD so actually i am prepared to re-format the disk and re-store from back up.

Any tips welcome!

Cheers
John

---

### Post by lryer on 2007-11-02
I'm having a similar problem with an internal hd after gutsy upgrade. When I try to mount manually I get:
```
mount: /dev/sdb1 already mounted or /home/lryer/download busy
```
umount tells me it's not mounted.

Still looking for clues...

---

