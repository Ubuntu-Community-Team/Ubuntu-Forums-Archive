---
title: "Hard drive not showing up?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by narutomonkeyfreak on 2008-06-27
Hi, I'm on my dad's Gateway 4535GZ Laptop. It's specs are: Pentium M 735 processor, 512 MB of RAM, and most important in this case I guess would be the hard drive, but I just know it's a 100 GB... not sure beyond that. 

It had Windows installed previously and it hd a many issues with it until it finally refused to boot at all. So I tried installing Hardy off of the LiveCD, but when the install finished and I logged in, all the icons were missing, so I tried rebooting and had the same problem so I tried reinstalling, nd then this time the install would not finish and now it can't detect the primary hard drive at all- the partitions don't show up on gparted or anything and the guided install option just leads me to the partitioner... any advice??? Thanks in advance!

---

### Post by milosz.galazka on 2008-06-27
Hello, 

You could download [ultimate boot cd]("http://www.ultimatebootcd.com/download.html") to check your harddrive

---

### Post by narutomonkeyfreak on 2008-06-27
I looked on the site, and the relevant progrms seem to require the windows environment (they're all exe files)? I don't have a computer running windows right now, just this running off of the live CD and a Toshiba Tecra M4 running Hardy.

---

### Post by VMC on 2008-06-27
Reboot using the "Live cd", then go "Applications-Accessories-Terminal", and open a Terminal and type this:

```
sudo fdisk -l
```

Come back and show us the output of that command

---

### Post by narutomonkeyfreak on 2008-06-27
OK, I rebooted from the LiveCD and fdisk isn't giving any output at all the terminal shows:

```
ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 

```

---

### Post by narutomonkeyfreak on 2008-06-27
If it helps any, when I run gparted, I get an output of 

```

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
ubuntu@ubuntu:~$ 

``` 

Which might be the real problem? I don't mind completely reformatting/losing data, because there isn't any... so is there a way to make this re writable instead of read -only?

---

### Post by narutomonkeyfreak on 2008-06-27
Oh, I got fdisk-l to work- 

```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/scd0
Note: sector size is 2048 (not 512)

Disk /dev/scd0: 733 MB, 733079552 bytes
255 heads, 63 sectors/track, 22 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes
Disk identifier: 0x00000000

Disk /dev/scd0 doesn't contain a valid partition table
ubuntu@ubuntu:~$ 

```

---

### Post by narutomonkeyfreak on 2008-06-27
Anyone? I'd really love for this to be fixed reltively soon, so...

*shameless bump*

---

### Post by VMC on 2008-06-27
That 'fdisk' command you supplied was for the cdrom drive, not the hard drive. It appears it doesn't recognize you hard drive. Can you open the case and check the cables and/or power supply cable?

---

### Post by narutomonkeyfreak on 2008-06-27
I took out the HArd Drive and popped it back in (it's a laptop) and it's still doing the same thing =(

---

