---
title: "copied Ubuntu install from dead hdd to new hdd.now system fails to boot!!!"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by deepclutch on 2008-02-12
[FONT=Garamond][SIZE=3]my old sata hdd went kaput.I had my Ubuntu Gutsy running on that hdd.
I mirror copied whole Ubuntu Gutsy 7.10 to a new partition(ext3) in the new hdd.I edited /etc/fstab to correct the device paths.I chrooted and did a dpkg-reconfigure linux-image-`uname -r`.
Still,Ubuntu fails to boot.grub shows some error code saying fails to read data etc. :(
Please Help

 the (old) drive haven't completely failed.it got stuck sometimes.thats all.already gave for RMA.

the error,I get is grub error:17 cannot be read etc.
while I browsed in grub to point to the correct /boot/vmlinuz&initrd paths and root device is also set correctly.apparently I cant find any reason:confused:
I am cent percent sure,I copied whole Ubuntu Gutsy to this new ext3 partition :S

what went wrong?.:(
[/SIZE][/FONT]

---

### Post by banewman on 2008-02-12
Did you do anything to write grub to the master boot record of the new disk?

---

### Post by deepclutch on 2008-02-12
OK.I dual boot with Debian Sid which I forgot to tell.so the grub is owned by Debian which is installed natively.

---

### Post by deepclutch on 2008-02-12
if I remove the grub from the Ubuntu which I copied from old hdd via chroot,is there any Hope?

---

### Post by deepclutch on 2008-02-14
OK.Finally solved the mess but cant say 100%.you can help other things.
Posting from My Debian Sid ;)
I mounted Debian in Ubuntu as root(sudo su -) :
```
mount /dev/sda10 /mnt
```then,
```
mount -t proc proc /mnt/proc
``````
mount --bind /dev /mnt/dev
``````
chroot /mnt /bin/bash
```then,
I reinstalled grub as:
```
grub>root (hd0,9)
setup (hd0)

```then,
```
grub-install /dev/sda
```that's it.
when rebooted,grub menu is shown.I can boot into Debian and login with my local username.
wait!but from here the menace starts :evil: :D
I CANNOT login via terminal or any virtual terminal as root!
wtf?
So,In panic,I tried resetting password via grub option to kernel(I use upstart in Debian in place of sysVinit) "rw init=/bin/bash"
changed password.
in that root terminal.I modprobed all needed modules manually(pppoe etc)
connected to my adsl pppoe connxn,"apt-get install --reinstall linux-image-`uname -r` grub dpkg bash "

also,I did a :
```
source /etc/profile
```as mkinitrd is complaining LANG etc env variables were missing 

anyways,now I am back in Debian.

Will you all folks help me what should I do to login as root in virtual terminal or terminal via su ?
Thank you All. :)

edit: well,I am trying (my debconf settings is "medium") as root 
```
dpkg-reconfigure --all
```

EDIT:
OK all problems solved :cool: 
I did a:
```
apt-get install --reinstall login libpam-runtime
```
to solve the /bin/su not having suid bit set .
So,Happy times!
Hope this benefits others too :)

---

