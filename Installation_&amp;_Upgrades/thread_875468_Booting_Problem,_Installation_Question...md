---
title: "Booting Problem, Installation Question.."
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by trebllaw on 2008-07-30
First of all Id like to explain how installed Ubuntu on my external hard drive so that the problem would be clear..

I have a Western Digital 160gb external hard drive which was mainly used for backup files on a windows machine.. Now as i was searching the net, i came across a tutorial on how to install Ubuntu 7.10 to an external hard drive so i did just that.. We dont have a net connection at home so updates were not installed..

this is my partition table:

/dev/sda1 - ntfs partition for files
/dev/sda2 - Ubuntu root partition
/dev/sda3 - Ubuntu swap partition

oh i forgot to mention that my internal hard drive was unplugged so the live cd and the external hard drive where the only disks found by ubuntu.. 

Now, when i boot from the external hard drive it gives me "Error 2" which when i searched the net refers to grub not installed properly.. Is my partition table ok? If so how do i fix the "Error 2" problem?

Next question.. Since i do not have a net connection at home, how do i install applications on Ubuntu [provided i fixed the booting problem :) ]. Ive downloaded several .deb packages and tried installing it to a friends computer (Ubuntu 7.10 also, and no net connection) but it gives me dependency errors..

Thanks..

---

### Post by Pumalite on 2008-07-30
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 
Boot a Live CD and post:
sudo fdisk -lu
(with external connected)

---

### Post by trebllaw on 2008-07-30
will post maybe tomorrow. dont have the live cd here with me in the office.. could i PM you so that if i have the result you could help me?

For the installation of packages and updates without internet connection at home, do you have a solution?

---

### Post by trebllaw on 2008-08-04
bump..

now, after reinstalling ubuntu again and grub on the MBR of the external drive, it give me Error 17: Cant mount the selected partition? What am i doing wrong and it wont let me boot from the external drive?

---

