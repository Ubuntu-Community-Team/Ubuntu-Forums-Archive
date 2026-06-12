---
title: "No longer boots! Says OS Not found.. Please help.."
date: 2015-09-13
forum: Installation &amp; Upgrades
---

### Post by kyo3 on 2015-09-13
Hello, I am in need of some help. I am pretty sure i messed something up really well. lol 
I am running Lubuntu on a older HP Laptop.

Laptop  lost power and shut down during update, when power was returned I  started the laptop and was presented with the grub recovery. 

Followed  some crap online i am sure made it worse ( sorry i forget the link to  artical ) rebooted like i was told and am now presented with OS not  found. I have a lot of data i need to recover so reinstalling is not a  option. 

Thinking  I screwed up grub I downloaded the boot repair disc image and installed  it to a usb and ran it ( first time i think i mistankenly selected  repair MBR under advance options ) told me to reboot i did same  problem. 

so  I tried to manually reinstall grub  via the chroot methed with the live  usb i used to install lubuntu on the laptop . Starting with  the first  cmd. 
( sudo mount -t ext4 /dev/sda1 /mnt/ )  I am given the error "Stale file handle" and can not contnue.



So  I Rebooted from the usb boot repair disc and ran it again So I could  ask for help. Here is the url it gave me for your review. It told me boot repaird restart. I did and still no os found..
[http://paste.ubuntu.com/12401942/](http://paste.ubuntu.com/12401942/)


If  I can not save this install, I at the very lest want to get my files  off the drive. I threw the harddrive into my windows desktop machine and it  picked it up in disk management but did not asign a drive letter and would  not let me assign one. So I was unable to copy my files off the drive  like that

I am at a loss and look forward to any help you can offer. 
Thanks

edit: when i try to acess my files to back up them up, while within the live usb I get a error saying 

"Error mounting /dev/sda1 at /media/lubuntu/b7a521f6-b740-40a7-a4e7-aa0ab7ab64e6: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/lubuntu/b7a521f6-b740-40a7-a4e7-aa0ab7ab64e6"' exited with non-zero exit status 32: mount: Stale file handle"

edit2: This is what GParted shows me.
[IMG]http://projects.patiencecorner.org/wp-content/uploads/2015/09/IMG_20150913_165948_905-1024x768.jpg[/IMG]

---

### Post by tgalati4 on 2015-09-14
Boot a LiveUSB of any Linux distro that will boot.  Connect your laptop with an ethernet cable. Open a terminal:

```
sudo fdisk -l
```

Install *testdisk* to RAM and then run it.  It will attempt to repair your directory tables so that the disk at least mounts correctly.

```
sudo apt-get install testdisk
man testdisk
sudo testdisk /dev/sda
```

Read about data recovery:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by oldfred on 2015-09-14
I might also try fsck.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

