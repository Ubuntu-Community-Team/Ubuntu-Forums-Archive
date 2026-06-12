---
title: "Unlock encrypted partition and access data"
date: 2018-09-03
forum: Installation &amp; Upgrades
---

### Post by elikopeleg on 2018-09-03
hello                                                 I have 2 hard disks- 128GB SSD, and 1TB. My system drive ( 128gb ssd) encrypted (during Ubuntu 18 installation).
I tried to cancel the encryption, but it's failed, and my second disk (1TB) encrypted to, and my system can't boot. I used the  fsck  to fix- and now it's can only give me a grub command-line.  I have the password of both (the same).  I have used live ubuntu, and here the results:
 [https://i.stack.imgur.com/G8dZI.png](https://i.stack.imgur.com/G8dZI.png)
  I have unlocked the 1TB- but I cant mount it and get access to my data.
[https://i.stack.imgur.com/jRaxH.png](https://i.stack.imgur.com/jRaxH.png)
  and get an error: 
  mount /dev/sda4 /mnt
mount: /mnt: unknown filesystem type 'crypto_LUKS'
  How can I get my data back? 
  Second  128GB SSD drive is locked. I have the password- when I boot  the system (before braked) I can unlock the 128 drive with the same  password.
But now  I can't unlock the drive- here is the error:
 [https://i.stack.imgur.com/GCbpB.png](https://i.stack.imgur.com/GCbpB.png)
  Some pictures of my disks system:
[https://i.stack.imgur.com/QScre.png](https://i.stack.imgur.com/QScre.png)
[https://i.stack.imgur.com/vHLcl.png](https://i.stack.imgur.com/vHLcl.png)
  I have installed win8 on 50GB partition, and try to use librecrypt and Ext2Read. Both cannot help me.
  I'd appreciate help
  
ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT /dev/sda
NAME     SIZE FSTYPE      TYPE MOUNTPOINT

sda    931.5G             disk 
&#9500;&#9472;sda1    62M vfat        part 
&#9500;&#9472;sda2   128M             part 
&#9500;&#9472;sda3  46.5G ntfs        part 
&#9492;&#9472;sda4 884.9G crypto_LUKS part 
ubuntu@ubuntu:~$ lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT /dev/sdb
NAME     SIZE FSTYPE      TYPE MOUNTPOINT
sdb    119.2G             disk 
&#9500;&#9472;sdb1   512M vfat        part 
&#9500;&#9472;sdb2   732M ext4        part 
&#9492;&#9472;sdb3   118G crypto_LUKS part 

'ubuntu@ubuntu:~$ sudo mount /dev/mapper/sda_decrypt /mnt'
'mount: /mnt: unknown filesystem type 'LVM2_member''

try:
  'ubuntu@ubuntu:~$ sudo mount -a /dev/mapper/sda_decrypt /mnt'
   no errors, but /mnt is empty. i cant access my files.

---

### Post by ajgreeny on 2018-09-03
Please do not add large images inline as you did in your post.

You should use the Attachment icon (paperclip) in the toolbar of the New thread or Reply text box which will add a thumbnail of your image as I have done.

Many users still have slow network speeds and limited or expensive bandwidth, and huge images are not comfortably viewed with small screens.

---

### Post by oldfred on 2018-09-03
With full drive encryption you also have to use LVM - logical volumes and then all your volumes are inside the physical partition. And you have to use LVM tools to manage those volumes.

I do not know LVM, but saved some links. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[URL="https://www.howtoforge.com/linux_lvm"]https://www.howtoforge.com/linux_lvm

      [/URL]
 Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line) 
            How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641) 
    [URL="https://www.howtoforge.com/linux_lvm"]
[/URL]

---

