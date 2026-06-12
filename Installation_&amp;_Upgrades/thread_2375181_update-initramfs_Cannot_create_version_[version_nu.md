---
title: "update-initramfs: Cannot create version [version number]: already exists"
date: 2017-10-22
forum: Installation &amp; Upgrades
---

### Post by debianuser2017 on 2017-10-22
**[SIZE=2][FONT=arial]Re: HOWTO: install and reinstall on an encrypted LUKS/LVM system [/FONT][/SIZE]**

[https://ubuntuforums.org/showthread.php?t=1205372&page=4](https://ubuntuforums.org/showthread.php?t=1205372&page=4)

User rom1v had same issue as I, FYI:

On an OS reinstall (preserving existing encrypted partitions), after copying the crypttab file to /etc, executing 
:~$ update-initramfs -k all -c -v  

results in: 
:~$ cannot create version [version number]: already exists

Solution:

make note of version number in previous result, then

:~$ update-initramfs -k [version number] -d -v                              
# to delete existing file

:~$ update-initramfs -k [version number] -c -v                                   
# to create new file

You then need to chroot into hd and use passwd command to change root password if you formatted /root during reinstall. Once logged in as root within desktop, add previous user (remembering to also include in proper groups). 

Hope it helps

---

