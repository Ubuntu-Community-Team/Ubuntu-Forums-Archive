---
title: "can't find my fat 32 [Resolved]"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by gonzo5680 on 2007-01-21
I partitioned my hard drive for a dual boot with windows and ubuntu. With the remaining space i created a fat 32 partition for both of them to use.  Ubuntu cant find the fat 32 but windows can.  I should also mention that i have tried the fstab command but i could not locate the fat 32 in it.  thanks

---

### Post by taurus on 2007-01-21
The command is 

```
sudo fdisk -l
```

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by aysiu on 2007-01-21
You probably have to add the FAT32 line to the /etc/fstab yourself. It may not be in there already.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) will help.

---

### Post by gonzo5680 on 2007-01-21
i tried to the psychocats page but when i got to the end it didnt work. some how i think i screwed up on the fstab part so i took a picture of what i put down and if anyone can spot the mistake that would be great

---

### Post by aysiu on 2007-01-21
You have commented out the relevant line. The # sign at the beginning of the line basically tells Ubuntu "ignore the rest of this line--pretend it's just a blank line."

So instead of ```
#/dev/hda4 /fat vfat iocharset=utf8,umask=000 0 0
``` the line *should* read ```
/dev/hda4 /fat vfat iocharset=utf8,umask=000 0 0
``` By the way, you can highlight and copy and paste terminal output to posts directly as text. You do not need to take screenshots and upload them.

---

### Post by gonzo5680 on 2007-01-21
took off the # but got this error when putting in the sudo mount -a command

mount: mount point /media/hda3 does not exist

I went back into fstab and put a # in front of hda3.  now when i sudo mount -a it will show nothing and still no fat drive.

---

### Post by aysiu on 2007-01-21
If it says /media/hda3 doesn't exist, you can just create it: ```
sudo mkdir /media/hda3
``` Let's just double-check that everything is as it should be with your FAT drive. Can you post the output of these three commands (no screenshots, please--just copy and paste the exact text)? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by gonzo5680 on 2007-01-21
:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2089    16779861    7  HPFS/NTFS
/dev/hda2            7270        7295      208845   88  Linux plaintext
/dev/hda3            2090        4308    17824117+   5  Extended
/dev/hda4            4309        7269    23784232+   b  W95 FAT32
/dev/hda5            2090        4178    16779861   83  Linux
/dev/hda6            4179        4308     1044193+  82  Linux swap / Solaris

Partition table entries are not in disk order

:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=aeba6994-4b6f-467f-b553-80c18b9684b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=CC1488101487FBA8 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=aac49e1a-80af-46fe-aabf-840e5d4581a7 /media/hda2     ext2    defaults        0       2
# /dev/hda3
#  /dev/hda3 /media/hda3 ntfs defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4 /fat vfat iocharset=utf8,umask=000 0 0
# /dev/hda6
UUID=ed840cc7-5aa8-4fba-b532-52986270f41b none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5              16G  2.4G   13G  16% /
varrun                248M   96K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  231M   7% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1              17G  2.2G   14G  14% /media/hda1
/dev/hda2             198M   13K  188M   1% /media/hda2
/dev/hda4              23G  144K   23G   1% /fat

---

### Post by aysiu on 2007-01-21
Everything looks right. In fact, /dev/hda4 does, in fact, appear to already be mounted at /fat

What happens when you go to the /fat folder? Open up your file browser, press Control-L, and type ```
/fat
``` and hit **Enter**.

---

### Post by gonzo5680 on 2007-01-21
sweet, it worked.  Thanks for the help.

---

