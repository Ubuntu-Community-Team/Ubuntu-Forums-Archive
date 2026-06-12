---
title: "LiveCD Customization - custom kernel"
date: 2008-07-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ramvi on 2008-07-13
I get BusyBox when I try to customize the liveCD. Please help me
```

#Following https://help.ubuntu.com/community/LiveCDCustomization
ramvi@ramvi:~$ cd ~/live
ramvi@ramvi:~/live$ mkdir mnt
ramvi@ramvi:~/live$ sudo mount -o loop ubuntu-8.04.1-desktop-i386.iso mnt
ramvi@ramvi:~/live$ mkdir extract-cd
ramvi@ramvi:~/live$ rsync --exclude=/casper/filesystem.squashfs -a mnt/ extract-cd
ramvi@ramvi:~/live$ mkdir squashfs
ramvi@ramvi:~/live$ sudo mount -t squashfs -o loop mnt/casper/filesystem.squashfs squashfs
ramvi@ramvi:~/live$ mkdir edit
ramvi@ramvi:~/live$ sudo cp -a squashfs/* edit/
ramvi@ramvi:~/live$ sudo cp /etc/resolv.conf edit/etc/
ramvi@ramvi:~/live$ sudo cp /etc/hosts edit/etc/
ramvi@ramvi:~/live$ sudo mount --bind /dev/ edit/dev
ramvi@ramvi:~/live$ sudo chroot edit
root@ramvi:/# mount -t proc none /proc
root@ramvi:/# mount -t sysfs none /sys
root@ramvi:/# export HOME=/root
root@ramvi:/# export LC_ALL=C



#Install custom kernel
root@ramvi:/# wget http://www.array.org/ubuntu/array.list
--16:46:25--  http://www.array.org/ubuntu/array.list
           => `array.list'
Resolving www.array.org... 216.69.172.116
Connecting to www.array.org|216.69.172.116|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44 [text/plain]

100%[==================================================================================================================================================================>] 44            --.--K/s             

16:46:26 (2.43 MB/s) - `array.list' saved [44/44]

root@ramvi:/# sudo mv -v array.list /etc/apt/sources.list.d/
`array.list' -> `/etc/apt/sources.list.d/array.list'
root@ramvi:/# wget http://www.array.org/ubuntu/array-apt-key.asc
--16:46:32--  http://www.array.org/ubuntu/array-apt-key.asc
           => `array-apt-key.asc'
Resolving www.array.org... 216.69.172.116
Connecting to www.array.org|216.69.172.116|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,795 (1.8K) [text/plain]

100%[==================================================================================================================================================================>] 1,795         --.--K/s             

16:46:32 (508.56 KB/s) - `array-apt-key.asc' saved [1795/1795]

root@ramvi:/# sudo apt-key add array-apt-key.asc
OK
root@ramvi:/# sudo apt-get update
Get:1 http://security.ubuntu.com hardy-security Release.gpg [189B]
Hit http://archive.ubuntu.com hardy Release.gpg                         
Get:2 http://archive.ubuntu.com hardy-updates Release.gpg [189B]        
Get:3 http://security.ubuntu.com hardy-security Release [58.5kB]        
Hit http://archive.ubuntu.com hardy Release                                                       
Get:4 http://archive.ubuntu.com hardy-updates Release [58.5kB]                                    
Get:5 http://www.array.org hardy Release.gpg [189B]                                                   
Hit http://archive.ubuntu.com hardy/main Packages                                              
Hit http://archive.ubuntu.com hardy/restricted Packages                                                              
Hit http://archive.ubuntu.com hardy/main Sources                                              
Hit http://archive.ubuntu.com hardy/restricted Sources                                        
Get:6 http://security.ubuntu.com hardy-security/main Packages [31.0kB]                        
Get:7 http://archive.ubuntu.com hardy-updates/main Packages [278kB]                           
Get:8 http://security.ubuntu.com hardy-security/restricted Packages [6156B]                      
Get:9 http://security.ubuntu.com hardy-security/main Sources [7805B]                              
Get:10 http://security.ubuntu.com hardy-security/restricted Sources [906B]                             
Get:11 http://www.array.org hardy Release [1546B]                                                
Get:12 http://archive.ubuntu.com hardy-updates/restricted Packages [6636B]
Get:13 http://archive.ubuntu.com hardy-updates/main Sources [79.7kB]                              
Get:14 http://archive.ubuntu.com hardy-updates/restricted Sources [908B]                             
Get:15 http://www.array.org hardy/eeepc Packages [3234B]                                             
Fetched 534kB in 2s (209kB/s)                                               
Reading package lists... Done
root@ramvi:/# sudo apt-get install linux-eeepc linux-headers-eeepc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.24-19-eeepc linux-image-2.6.24-19-eeepc linux-image-eeepc linux-ubuntu-modules-2.6.24-19-eeepc
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-eeepc linux-headers-2.6.24-19-eeepc linux-headers-eeepc linux-image-2.6.24-19-eeepc linux-image-eeepc linux-ubuntu-modules-2.6.24-19-eeepc
0 upgraded, 6 newly installed, 0 to remove and 18 not upgraded.
Need to get 17.3MB of archives.
After this operation, 60.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://www.array.org hardy/eeepc linux-image-2.6.24-19-eeepc 2.6.24-19.34 [12.0MB]
Get:2 http://www.array.org hardy/eeepc linux-ubuntu-modules-2.6.24-19-eeepc 2.6.24-19.28ubuntu6 [4716kB]                                                                                                     
Get:3 http://www.array.org hardy/eeepc linux-image-eeepc 2.6.24.19.21 [26.4kB]                                                                                                                               
Get:4 http://www.array.org hardy/eeepc linux-eeepc 2.6.24.19.21 [26.4kB]                                                                                                                                     
Get:5 http://www.array.org hardy/eeepc linux-headers-2.6.24-19-eeepc 2.6.24-19.34 [557kB]                                                                                                                    
Get:6 http://www.array.org hardy/eeepc linux-headers-eeepc 2.6.24.19.21 [26.4kB]                                                                                                                             
Fetched 17.3MB in 1min3s (272kB/s)                                                                                                                                                                           
Selecting previously deselected package linux-image-2.6.24-19-eeepc.
(Reading database ... 98420 files and directories currently installed.)
Unpacking linux-image-2.6.24-19-eeepc (from .../linux-image-2.6.24-19-eeepc_2.6.24-19.34_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-19-eeepc.
Unpacking linux-ubuntu-modules-2.6.24-19-eeepc (from .../linux-ubuntu-modules-2.6.24-19-eeepc_2.6.24-19.28ubuntu6_i386.deb) ...
Selecting previously deselected package linux-image-eeepc.
Unpacking linux-image-eeepc (from .../linux-image-eeepc_2.6.24.19.21_i386.deb) ...
Selecting previously deselected package linux-eeepc.
Unpacking linux-eeepc (from .../linux-eeepc_2.6.24.19.21_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.24-19-eeepc.
Unpacking linux-headers-2.6.24-19-eeepc (from .../linux-headers-2.6.24-19-eeepc_2.6.24-19.34_i386.deb) ...
Selecting previously deselected package linux-headers-eeepc.
Unpacking linux-headers-eeepc (from .../linux-headers-eeepc_2.6.24.19.21_i386.deb) ...
Setting up linux-image-2.6.24-19-eeepc (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-eeepc
The link /initrd.img is a dangling linkto /boot/initrd.img-2.6.24-19-generic

Setting up linux-ubuntu-modules-2.6.24-19-eeepc (2.6.24-19.28ubuntu6) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-eeepc

Setting up linux-image-eeepc (2.6.24.19.21) ...
Setting up linux-eeepc (2.6.24.19.21) ...
Setting up linux-headers-2.6.24-19-eeepc (2.6.24-19.34) ...
Setting up linux-headers-eeepc (2.6.24.19.21) ...



#Have the liveCD use the custom kernel
root@ramvi:/# exit
exit
ramvi@ramvi:~/live$ sudo cp /boot/vmlinuz-2.6.24-1 extract-cd/casper/vmlinuz
vmlinuz-2.6.24-16-generic  vmlinuz-2.6.24-17-generic  vmlinuz-2.6.24-19-eeepc    vmlinuz-2.6.24-19-generic  
ramvi@ramvi:~/live$ sudo cp /boot/vmlinuz-2.6.24-19-eeepc extract-cd/casper/vmlinuz
ramvi@ramvi:~/live$ sudo cp /boot/initrd.img-2.6.24-19-eeepc extract-cd/casper/initrd.gz
ramvi@ramvi:~/live$ sudo chroot edit
root@ramvi:/# mkinitramfs -o /initrd.gz 2.6.24-19-eeepc
root@ramvi:/# exit
exit
ramvi@ramvi:~/live$ mv edit/initrd.gz extract-cd/casper/
mv: try to overwrite «extract-cd/casper/initrd.gz», overriding mode 0444 (r--r--r--)? y
mv: kan ikke flytte «edit/initrd.gz» til «extract-cd/casper/initrd.gz»: Permission denied
ramvi@ramvi:~/live$ sudo mv edit/initrd.gz extract-cd/casper/



#Cleanup
ramvi@ramvi:~/live$ sudo chroot edit
root@ramvi:/# rm -rf /tmp/*
root@ramvi:/# rm /etc/resolv.conf
root@ramvi:/# apt-get clean
root@ramvi:/# umount /proc
root@ramvi:/# umount /sys
root@ramvi:/# exit
exit
ramvi@ramvi:~/live$ sudo umount edit/dev



#Putting the iso together
ramvi@ramvi:~/live$ chmod +w extract-cd/casper/filesystem.manifest
ramvi@ramvi:~/live$ sudo chroot edit dpkg-query -W --showformat='${Package} ${Version}\n' > extract-cd/casper/filesystem.manifest
ramvi@ramvi:~/live$ sudo cp extract-cd/casper/filesystem.manifest extract-cd/casper/filesystem.manifest-desktop
ramvi@ramvi:~/live$ sudo sed -i '/ubiquity/d' extract-cd/casper/filesystem.manifest-desktop
ramvi@ramvi:~/live$ sudo rm extract-cd/casper/filesystem.squashfs
rm: kan ikke fjerne «extract-cd/casper/filesystem.squashfs»: No such file or directory
ramvi@ramvi:~/live$ sudo mksquashfs edit extract-cd/casper/filesystem.squashfs -nolzma
Parallel mksquashfs: Using 2 processors
Creating little endian 3.1 filesystem on extract-cd/casper/filesystem.squashfs, block size 131072.
[=======================================================================================================================================================================================   ] 89889/90946  98%
Exportable Little endian filesystem, data block size 131072, compressed data, compressed metadata, compressed fragments, duplicates are removed
Filesystem size 711620.64 Kbytes (694.94 Mbytes)
	38.85% of uncompressed filesystem size (1831895.03 Kbytes)
Inode table size 1150704 bytes (1123.73 Kbytes)
	28.36% of uncompressed inode table size (4057634 bytes)
Directory table size 1114547 bytes (1088.42 Kbytes)
	47.37% of uncompressed directory table size (2353017 bytes)
Number of duplicate files found 10384
Number of inodes 117196
Number of files 87175
Number of fragments 6576
Number of symbolic links  17082
Number of device nodes 95
Number of fifo nodes 2
Number of socket nodes 0
Number of directories 12842
Number of uids 13
	root (0)
	klog (102)
	daemon (1)
	dhcp (100)
	man (6)
	gdm (105)
	pulse (106)
	news (9)
	avahi (108)
	avahi-autoipd (104)
	hplip (103)
	nobody (65534)
	ramvi (1000)
Number of gids 30
	ssl-cert (107)
	video (44)
	audio (29)
	tty (5)
	kmem (15)
	disk (6)
	adm (4)
	daemon (1)
	dip (30)
	shadow (42)
	lpadmin (108)
	dialout (20)
	syslog (102)
	mlocate (110)
	crontab (109)
	ssh (111)
	utmp (43)
	avahi-autoipd (112)
	games (60)
	avahi (119)
	mail (8)
	haldaemon (122)
	staff (50)
	dhcp (101)
	src (40)
	pulse (115)
	root (0)
	gdm (113)
	sambashare (114)
	scanner (104)
ramvi@ramvi:~/live$ sudo nano extract-cd/README.diskdefines
ramvi@ramvi:~/live$ sudo -s
root@ramvi:~/live# rm extract-cd/md5sum.txt
root@ramvi:~/live# (cd extract-cd && find . -type f -print0 | xargs -0 md5sum > md5sum.txt)
root@ramvi:~/live# exit
exit
ramvi@ramvi:~/live$ cd extract-cd
ramvi@ramvi:~/live/extract-cd$ sudo mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o ../ubuntu-6.06.2-desktop-i386-custom.iso .
I: -input-charset not specified, using utf-8 (detected in locale settings)
Size of boot image is 4 sectors -> No emulation
  1.36% done, estimate finish Sun Jul 13 19:05:36 2008
  2.73% done, estimate finish Sun Jul 13 19:05:36 2008
  4.09% done, estimate finish Sun Jul 13 19:05:11 2008
  5.45% done, estimate finish Sun Jul 13 19:05:18 2008
  6.81% done, estimate finish Sun Jul 13 19:05:07 2008
  8.17% done, estimate finish Sun Jul 13 19:05:11 2008
  9.53% done, estimate finish Sun Jul 13 19:05:04 2008
 10.90% done, estimate finish Sun Jul 13 19:04:59 2008
 12.25% done, estimate finish Sun Jul 13 19:05:03 2008
 13.62% done, estimate finish Sun Jul 13 19:05:07 2008
 14.98% done, estimate finish Sun Jul 13 19:05:03 2008
 16.34% done, estimate finish Sun Jul 13 19:05:05 2008
 17.70% done, estimate finish Sun Jul 13 19:05:02 2008
 19.06% done, estimate finish Sun Jul 13 19:05:10 2008
 20.42% done, estimate finish Sun Jul 13 19:05:07 2008
 21.79% done, estimate finish Sun Jul 13 19:05:08 2008
 23.15% done, estimate finish Sun Jul 13 19:05:10 2008
 24.51% done, estimate finish Sun Jul 13 19:05:11 2008
 25.87% done, estimate finish Sun Jul 13 19:05:13 2008
 27.23% done, estimate finish Sun Jul 13 19:05:14 2008
 28.59% done, estimate finish Sun Jul 13 19:05:15 2008
 29.96% done, estimate finish Sun Jul 13 19:05:16 2008
 31.32% done, estimate finish Sun Jul 13 19:05:17 2008
 32.68% done, estimate finish Sun Jul 13 19:05:21 2008
 34.04% done, estimate finish Sun Jul 13 19:05:21 2008
 35.40% done, estimate finish Sun Jul 13 19:05:25 2008
 36.76% done, estimate finish Sun Jul 13 19:05:25 2008
 38.12% done, estimate finish Sun Jul 13 19:05:23 2008
 39.48% done, estimate finish Sun Jul 13 19:05:23 2008
 40.85% done, estimate finish Sun Jul 13 19:05:24 2008
 42.21% done, estimate finish Sun Jul 13 19:05:24 2008
 43.57% done, estimate finish Sun Jul 13 19:05:22 2008
 44.93% done, estimate finish Sun Jul 13 19:05:23 2008
 46.29% done, estimate finish Sun Jul 13 19:05:23 2008
 47.65% done, estimate finish Sun Jul 13 19:05:23 2008
 49.02% done, estimate finish Sun Jul 13 19:05:26 2008
 50.38% done, estimate finish Sun Jul 13 19:05:26 2008
 51.74% done, estimate finish Sun Jul 13 19:05:26 2008
 53.10% done, estimate finish Sun Jul 13 19:05:27 2008
 54.46% done, estimate finish Sun Jul 13 19:05:27 2008
 55.82% done, estimate finish Sun Jul 13 19:05:27 2008
 57.19% done, estimate finish Sun Jul 13 19:05:25 2008
 58.54% done, estimate finish Sun Jul 13 19:05:26 2008
 59.91% done, estimate finish Sun Jul 13 19:05:26 2008
 61.27% done, estimate finish Sun Jul 13 19:05:25 2008
 62.63% done, estimate finish Sun Jul 13 19:05:26 2008
 63.99% done, estimate finish Sun Jul 13 19:05:28 2008
 65.35% done, estimate finish Sun Jul 13 19:05:28 2008
 66.71% done, estimate finish Sun Jul 13 19:05:28 2008
 68.08% done, estimate finish Sun Jul 13 19:05:29 2008
 69.44% done, estimate finish Sun Jul 13 19:05:29 2008
 70.80% done, estimate finish Sun Jul 13 19:05:29 2008
 72.16% done, estimate finish Sun Jul 13 19:05:29 2008
 73.52% done, estimate finish Sun Jul 13 19:05:28 2008
 74.88% done, estimate finish Sun Jul 13 19:05:29 2008
 76.25% done, estimate finish Sun Jul 13 19:05:32 2008
 77.61% done, estimate finish Sun Jul 13 19:05:31 2008
 78.97% done, estimate finish Sun Jul 13 19:05:30 2008
 80.33% done, estimate finish Sun Jul 13 19:05:30 2008
 81.69% done, estimate finish Sun Jul 13 19:05:30 2008
 83.05% done, estimate finish Sun Jul 13 19:05:30 2008
 84.41% done, estimate finish Sun Jul 13 19:05:29 2008
 85.77% done, estimate finish Sun Jul 13 19:05:29 2008
 87.14% done, estimate finish Sun Jul 13 19:05:28 2008
 88.50% done, estimate finish Sun Jul 13 19:05:28 2008
 89.86% done, estimate finish Sun Jul 13 19:05:29 2008
 91.22% done, estimate finish Sun Jul 13 19:05:30 2008
 92.58% done, estimate finish Sun Jul 13 19:05:29 2008
 93.94% done, estimate finish Sun Jul 13 19:05:30 2008
 95.31% done, estimate finish Sun Jul 13 19:05:30 2008
 96.67% done, estimate finish Sun Jul 13 19:05:29 2008
 98.03% done, estimate finish Sun Jul 13 19:05:29 2008
 99.39% done, estimate finish Sun Jul 13 19:05:30 2008
Total translation table size: 2048
Total rockridge attributes bytes: 26712
Total directory bytes: 130982
Path table size(bytes): 886
Max brk space used 42000
367249 extents written (717 MB)

```

I test the iso in Virtualbox and get this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=77627&stc=1&d=1215969082[/IMG]

---

### Post by ramvi on 2008-07-15
bump

---

### Post by jocko on 2008-07-15
This is not a very helpful answer, but didn't you post this thread in the wrong part of the forum?

---

### Post by ramvi on 2008-07-15
> **jocko said:**
> This is not a very helpful answer, but didn't you post this thread in the wrong part of the forum?

Ok - sure. Where should it be posted?
I'm really bad at finding the right category of stuff - I keep putting myself in Hunk.

---

### Post by jocko on 2008-07-15
> **ramvi said:**
> Ok - sure. Where should it be posted?
I'm really bad at finding the right category of stuff - I keep putting myself in Hunk.
I'm not sure... but perhaps it could go in the "[General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")" section, at least not in the intrepid testing section, as your question has nothing to do with intrepid.

I'm just saying this because you are more likely to find help on your problem if you post in a more relevant relevant section (the people that know live cd customization don't necessarily look in the intrepid section that often, unless they are testing intrepid, of course)...
I see that you are trying to use a kernel optimized for an eeepc, have you checked the [eeepc forums]("http://forum.eeeuser.com/viewforum.php?id=43")?

---

### Post by ramvi on 2008-07-15
Thanks!
Continued here: [http://ubuntuforums.org/showthread.php?p=5392823](http://ubuntuforums.org/showthread.php?p=5392823)

---

