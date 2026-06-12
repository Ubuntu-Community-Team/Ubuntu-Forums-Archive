---
title: "/boot partition is full"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by iissmart on 2010-03-21
I've been updating a remote Ubuntu 8.04 LTS server quite frequently, and ended up filling my /boot partition which is only ~240MB. It looks like there are about 11 different versions of kernel updates on that partition, and I want to remove all but the last few to free up space. My only concern is I want to make sure I do it right because this is a remote server and I *need* it to reboot successfully, heh. Is there a program which will automatically "clean up" the /boot partition, or can you suggest what exactly I can/can't remove (and files I should update, like /boot/grub/menu.lst)?

```
root@numberzero:~# ls -alhR /boot
/boot:
total 204M
drwxr-xr-x  4 root root 5.0K 2010-02-27 17:02 .
drwxr-xr-x 21 root root 4.0K 2010-02-27 17:00 ..
-rw-r--r--  1 root root 417K 2008-04-10 12:55 abi-2.6.24-16-server
-rw-r--r--  1 root root 417K 2008-05-01 14:03 abi-2.6.24-17-server
-rw-r--r--  1 root root 417K 2008-05-28 22:48 abi-2.6.24-18-server
-rw-r--r--  1 root root 417K 2008-08-21 00:50 abi-2.6.24-19-server
-rw-r--r--  1 root root 417K 2008-10-21 23:16 abi-2.6.24-21-server
-rw-r--r--  1 root root 417K 2008-11-24 17:52 abi-2.6.24-22-server
-rw-r--r--  1 root root 417K 2009-04-01 21:21 abi-2.6.24-23-server
-rw-r--r--  1 root root 417K 2009-09-18 16:23 abi-2.6.24-24-server
-rw-r--r--  1 root root 417K 2009-10-20 07:52 abi-2.6.24-25-server
-rw-r--r--  1 root root 417K 2009-12-01 17:59 abi-2.6.24-26-server
-rw-r--r--  1 root root 417K 2010-01-27 23:15 abi-2.6.24-27-server
-rw-r--r--  1 root root  79K 2008-04-10 12:55 config-2.6.24-16-server
-rw-r--r--  1 root root  79K 2008-05-01 14:03 config-2.6.24-17-server
-rw-r--r--  1 root root  79K 2008-05-28 22:48 config-2.6.24-18-server
-rw-r--r--  1 root root  79K 2008-08-21 00:50 config-2.6.24-19-server
-rw-r--r--  1 root root  79K 2008-10-21 23:16 config-2.6.24-21-server
-rw-r--r--  1 root root  79K 2008-11-24 17:52 config-2.6.24-22-server
-rw-r--r--  1 root root  79K 2009-04-01 21:21 config-2.6.24-23-server
-rw-r--r--  1 root root  79K 2009-09-18 16:23 config-2.6.24-24-server
-rw-r--r--  1 root root  79K 2009-10-20 07:52 config-2.6.24-25-server
-rw-r--r--  1 root root  79K 2009-12-01 17:59 config-2.6.24-26-server
-rw-r--r--  1 root root  79K 2010-01-27 23:15 config-2.6.24-27-server
drwxr-xr-x  2 root root 1.0K 2010-02-27 17:03 grub
-rw-r--r--  1 root root 7.6M 2008-05-08 04:25 initrd.img-2.6.24-16-server
-rw-r--r--  1 root root 7.4M 2008-05-08 04:17 initrd.img-2.6.24-16-server.bak
-rw-r--r--  1 root root 7.6M 2008-05-27 19:45 initrd.img-2.6.24-17-server
-rw-r--r--  1 root root 7.6M 2008-05-27 19:44 initrd.img-2.6.24-17-server.bak
-rw-r--r--  1 root root 7.7M 2008-06-09 23:40 initrd.img-2.6.24-18-server
-rw-r--r--  1 root root 7.6M 2008-06-03 18:08 initrd.img-2.6.24-18-server.bak
-rw-r--r--  1 root root 7.7M 2008-08-25 22:15 initrd.img-2.6.24-19-server
-rw-r--r--  1 root root 7.7M 2008-07-16 13:30 initrd.img-2.6.24-19-server.bak
-rw-r--r--  1 root root 7.7M 2008-11-13 11:42 initrd.img-2.6.24-21-server
-rw-r--r--  1 root root 7.7M 2008-10-16 15:56 initrd.img-2.6.24-21-server.bak
-rw-r--r--  1 root root 7.7M 2008-12-16 13:27 initrd.img-2.6.24-22-server
-rw-r--r--  1 root root 7.7M 2008-11-27 18:09 initrd.img-2.6.24-22-server.bak
-rw-r--r--  1 root root 7.7M 2009-04-23 14:27 initrd.img-2.6.24-23-server
-rw-r--r--  1 root root 7.7M 2009-04-23 14:26 initrd.img-2.6.24-23-server.bak
-rw-r--r--  1 root root 7.7M 2009-10-11 23:59 initrd.img-2.6.24-24-server
-rw-r--r--  1 root root 7.7M 2009-10-11 23:59 initrd.img-2.6.24-24-server.bak
-rw-r--r--  1 root root 7.7M 2009-11-08 20:32 initrd.img-2.6.24-25-server
-rw-r--r--  1 root root 7.7M 2009-11-08 20:32 initrd.img-2.6.24-25-server.bak
-rw-r--r--  1 root root 7.7M 2010-02-27 17:01 initrd.img-2.6.24-26-server
-rw-r--r--  1 root root 7.7M 2009-12-07 22:11 initrd.img-2.6.24-26-server.bak
-rw-r--r--  1 root root 7.7M 2010-02-27 17:02 initrd.img-2.6.24-27-server
-rw-r--r--  1 root root 7.7M 2010-02-27 17:00 initrd.img-2.6.24-27-server.bak
drwx------  2 root root  12K 2008-05-08 04:13 lost+found
-rw-r--r--  1 root root 101K 2007-09-28 06:06 memtest86+.bin
-rw-r--r--  1 root root 912K 2008-04-10 12:55 System.map-2.6.24-16-server
-rw-r--r--  1 root root 912K 2008-05-01 14:03 System.map-2.6.24-17-server
-rw-r--r--  1 root root 912K 2008-05-28 22:48 System.map-2.6.24-18-server
-rw-r--r--  1 root root 912K 2008-08-21 00:50 System.map-2.6.24-19-server
-rw-r--r--  1 root root 913K 2008-10-21 23:16 System.map-2.6.24-21-server
-rw-r--r--  1 root root 913K 2008-11-24 17:52 System.map-2.6.24-22-server
-rw-r--r--  1 root root 913K 2009-04-01 21:21 System.map-2.6.24-23-server
-rw-r--r--  1 root root 913K 2009-09-18 16:23 System.map-2.6.24-24-server
-rw-r--r--  1 root root 913K 2009-10-20 07:52 System.map-2.6.24-25-server
-rw-r--r--  1 root root 913K 2009-12-01 17:59 System.map-2.6.24-26-server
-rw-r--r--  1 root root 914K 2010-01-27 23:15 System.map-2.6.24-27-server
-rw-r--r--  1 root root 1.9M 2008-04-10 12:55 vmlinuz-2.6.24-16-server
-rw-r--r--  1 root root 1.9M 2008-05-01 14:03 vmlinuz-2.6.24-17-server
-rw-r--r--  1 root root 1.9M 2008-05-28 22:48 vmlinuz-2.6.24-18-server
-rw-r--r--  1 root root 1.9M 2008-08-21 00:50 vmlinuz-2.6.24-19-server
-rw-r--r--  1 root root 1.9M 2008-10-21 23:16 vmlinuz-2.6.24-21-server
-rw-r--r--  1 root root 1.9M 2008-11-24 17:52 vmlinuz-2.6.24-22-server
-rw-r--r--  1 root root 1.9M 2009-04-01 21:21 vmlinuz-2.6.24-23-server
-rw-r--r--  1 root root 1.9M 2009-09-18 16:23 vmlinuz-2.6.24-24-server
-rw-r--r--  1 root root 1.9M 2009-10-20 07:52 vmlinuz-2.6.24-25-server
-rw-r--r--  1 root root 1.9M 2009-12-01 17:59 vmlinuz-2.6.24-26-server
-rw-r--r--  1 root root 2.0M 2010-01-27 23:15 vmlinuz-2.6.24-27-server

/boot/grub:
total 186K
drwxr-xr-x 2 root root 1.0K 2010-02-27 17:03 .
drwxr-xr-x 4 root root 5.0K 2010-02-27 17:02 ..
-rw-r--r-- 1 root root  197 2008-05-08 04:25 default
-rw-r--r-- 1 root root   15 2008-05-08 04:25 device.map
-rw-r--r-- 1 root root 7.9K 2008-05-08 04:25 e2fs_stage1_5
-rw-r--r-- 1 root root 7.8K 2008-05-08 04:25 fat_stage1_5
-rw-r--r-- 1 root root   16 2008-05-08 04:25 installed-version
-rw-r--r-- 1 root root 8.5K 2008-05-08 04:25 jfs_stage1_5
-rw-r--r-- 1 root root 8.0K 2010-02-27 17:00 menu.lst
-rw-r--r-- 1 root root 7.6K 2010-02-27 17:00 menu.lst~
-rw-r--r-- 1 root root 7.2K 2008-05-08 04:25 minix_stage1_5
-rw-r--r-- 1 root root 9.5K 2008-05-08 04:25 reiserfs_stage1_5
-rw-r--r-- 1 root root  512 2008-05-08 04:25 stage1
-rw-r--r-- 1 root root 106K 2008-05-08 04:25 stage2
-rw-r--r-- 1 root root 9.1K 2008-05-08 04:25 xfs_stage1_5

/boot/lost+found:
total 17K
drwx------ 2 root root  12K 2008-05-08 04:13 .
drwxr-xr-x 4 root root 5.0K 2010-02-27 17:02 ..

```

---

### Post by mikewhatever on 2010-03-22
You'll need to remove the packages named:
linux-image-2.6.24-16-server
linux-image-2.6.24-17-server
linux-image-2.6.24-18-server
linux-image-2.6.24-19-server
linux-image-2.6.24-20-server
linux-image-2.6.24-21-server
linux-image-2.6.24-22-server
linux-image-2.6.24-23-server
linux-image-2.6.24-24-server
linux-image-2.6.24-25-server
linux-image-2.6.24-26-server

The run <sudo apt-get autoremove> to get rid of dependencies.
The latest kernel is linux-image-2.6.24-27-server, so leave it be.

---

### Post by Herman on 2010-03-22
:D  Hello everyone,

This thread seemed interesting and my package management know-how can do with a little improvement so I decided to google and see if I could fine the exact commands, best commands to use for this job.

I came up with the following web page,  [Safely Remove / Delete Old Linux Kernel from a Linux Server]("http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/") - [NixCraft]("http://www.cyberciti.biz/faq/proper-way-to-remove-old-linux-kernels/"), and I tried out the commands there which apply to Ubuntu.
```
uname -r
``````
sudo dpkg --list 'linux-image*'
``````
sudo apt-get remove linux-image-2.6.31-15-generic
```I was a surprised at how well that last command worked, first it told me what it was about to do and how much disk space that would free, and then when I agreed it did the job and also automatically ran update-grub for me! Cool! :D
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.31-15-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 113MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 222390 files and directories currently installed.)
Removing linux-image-2.6.31-15-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: karmic.tga
Adding custom boot entry(s)
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Adding custom boot entry(s)
Adding custom boot entry(s)
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 7.10 (7.10) on /dev/sda1
Found Ubuntu 7.04 (7.04) on /dev/sda2
Found openSUSE 10.3 (X86-64) on /dev/sda4
Found Debian GNU/Linux (4.0) on /dev/sda5
Found Ubuntu 9.04 (9.04) on /dev/sdc2
Found Ubuntu 8.10 (8.10) on /dev/sdc3
Found Ubuntu 8.04.4 LTS (8.04) on /dev/sdc4
done
```Considering the number of times people post in and complain about the length of their boot menus in GRUB2, it's astonishing that this little sequence of commands is not more well known by now. :D

EDIT: We can even uninstall a whole bunch of them at the same time,
```
sudo apt-get remove linux-image-2.6.31-14-generic linux-image-2.6.31-15-generic linux-image-2.6.31-16-generic linux-image-2.6.31-17-generic
```
You guys probably already knew these commands but I thought I'd post them here for the benefit of others who may be looking up something in this thread. :D

---

### Post by iissmart on 2010-03-24
> **mikewhatever said:**
> You'll need to remove the packages named:
linux-image-2.6.24-16-server
linux-image-2.6.24-17-server
linux-image-2.6.24-18-server
linux-image-2.6.24-19-server
linux-image-2.6.24-20-server
linux-image-2.6.24-21-server
linux-image-2.6.24-22-server
linux-image-2.6.24-23-server
linux-image-2.6.24-24-server
linux-image-2.6.24-25-server
linux-image-2.6.24-26-server

The run <sudo apt-get autoremove> to get rid of dependencies.
The latest kernel is linux-image-2.6.24-27-server, so leave it be.
Thanks, I didn't realize just removing the package would clean up and regenerate all the files as well. Seems to be working great!

---

### Post by paran0ia on 2011-03-04
one-liner:
```

dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done

```sophisticated:
```

dpkg --get-selections | \
  grep 'linux-image*' | \
  awk '{print $1}' | \
  egrep -v "linux-image-$(uname -r)|linux-image-generic" | \
  while read n
  do
    apt-get -y remove $n
  done

```

---

### Post by tacom6 on 2011-10-08
> **iissmart said:**
> Thanks, I didn't realize just removing the package would clean up and regenerate all the files as well. Seems to be working great!
Thank you very much for documenting this, as it came VERY handy on my Ubuntu server's boot partition! 
:D All the best!
Nile

---

### Post by ManiacMagee on 2012-08-19
> **paran0ia said:**
> one-liner:
```

dpkg --get-selections|grep 'linux-image*'|awk '{print $1}'|egrep -v "linux-image-$(uname -r)|linux-image-generic" |while read n;do apt-get -y remove $n;done

```sophisticated:
```

dpkg --get-selections | \
  grep 'linux-image*' | \
  awk '{print $1}' | \
  egrep -v "linux-image-$(uname -r)|linux-image-generic" | \
  while read n
  do
    apt-get -y remove $n
  done

```

Thanks.   This is really elegant.   You gave me some new tools here.

---

