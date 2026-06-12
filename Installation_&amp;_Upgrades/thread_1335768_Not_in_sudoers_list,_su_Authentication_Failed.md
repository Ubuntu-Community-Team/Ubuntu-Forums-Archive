---
title: "Not in sudoers list, su: Authentication Failed"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by KiotieII on 2009-11-23
Hello, I'm trying to install Ubuntu (9.04, I think) on a 2G Surf, as described here [http://forum.eeeuser.com/viewtopic.php?pid=467740#p467740](http://forum.eeeuser.com/viewtopic.php?pid=467740#p467740) .

   When I get to the part I need to enter  "sudo nano /etc/apt/sources.list", I get the message "user is not in the sudoers file. This incident will be reported." (My account name is user). So, when I try to login as root using su -, I enter the password I entered during the installation for root, and then it says "su: Authentication failed". I am desperate to get this installed, and I'm pretty much stuck right now, because I need su to add user to the sudoers list, and without sudo, I can't install anything.

Please explain everything, as I am very new to Linux.
Thanks,
KiotieII

---

### Post by jacobs444 on 2009-11-23
I have had this problem before. you may have to use the live disk, boot all the way up then open applications/accesories/terminal type sudo su. Then type mkdir /media/disk1, then mount the disk you installed on to /media/disk1 (usuallyfor first hard disk with ext4 partition: 
mount -t /dev/sda1 ext4 /media/disk1

then type: chroot /media/disk1
then passwd yourusername
and enter new password
you can also: passwd root 
from here, once done reboot and enjoy.

---

### Post by mechro on 2009-11-23
I'll take a wild guess that having a username of "user" is a bad idea and causing conflicts.

---

### Post by KiotieII on 2009-11-23
> **jacobs444 said:**
> I have had this problem before. you may have to use the live disk, boot all the way up then open applications/accesories/terminal type sudo su. Then type mkdir /media/disk1, then mount the disk you installed on to /media/disk1 (usuallyfor first hard disk with ext4 partition: 
mount -t /dev/sda1 ext4 /media/disk1

then type: chroot /media/disk1
then passwd yourusername
and enter new password
you can also: passwd root 
from here, once done reboot and enjoy.

Thanks, I'll try that and report back.

KiotieII

---

### Post by KiotieII on 2009-11-23
> **jacobs444 said:**
> I have had this problem before. you may have to use the live disk, boot all the way up then open applications/accesories/terminal type sudo su. Then type mkdir /media/disk1, then mount the disk you installed on to /media/disk1 (usuallyfor first hard disk with ext4 partition: 
mount -t /dev/sda1 ext4 /media/disk1

then type: chroot /media/disk1
then passwd yourusername
and enter new password
you can also: passwd root 
from here, once done reboot and enjoy.

Ok, I booted into 9.04 via a CD and entered the following codes successfully:

[U]sudo su
root@ubuntu:/home/ubuntu# mkdir /media/disk1[/U]


Then, I entered this code (the file system is ext3) :

_root@ubuntu:/home/ubuntu# Mount -t /dev/sda1 ext3 /media/disk1_

And I got this error:
_mount: unknown filesystem type '/dev/sda1'_

I went ahead and tried chroot /media/disk1 and got the following error:

[U]chroot: cannot run command '/bin/bash': no such file or directory

[/U]Should I reinstall (AGAIN :mad:) and choose a different name, or is this still fixable?

Thanks!
KiotieII

---

### Post by KiotieII on 2009-11-23
> **KiotieII said:**
> Ok, I booted into 9.04 via a CD and entered the following codes successfully:

[U]sudo su
root@ubuntu:/home/ubuntu# mkdir /media/disk1[/U]


Then, I entered this code (the file system is ext3) :

_root@ubuntu:/home/ubuntu# Mount -t /dev/sda1 ext3 /media/disk1_

And I got this error:
_mount: unknown filesystem type '/dev/sda1'_

I went ahead and tried chroot /media/disk1 and got the following error:

[U]chroot: cannot run command '/bin/bash': no such file or directory

[/U]Should I reinstall (AGAIN :mad:) and choose a different name, or is this still fixable?

Thanks!
KiotieII
Ok, I can now at least access root. I did chroot /media/disk and changed the password. I will now look up how to add a user to the sudo file :P 

Thanks for your help!!

KiotieII

---

### Post by GGG121 on 2009-11-23
Hello KiotieII,

Check out the man page to visudo to go about editing the sudoers list.

```
man visudo
```

As root, run visudo and add your user name in the same way root is entered. I had to do this on my own little project running Intrepid, but I think it should still work on Jaunty.

Hope this helps...:)

---

### Post by KiotieII on 2009-11-23
> **GGG121 said:**
> Hello KiotieII,

Check out the man page to visudo to go about editing the sudoers list.

```
man visudo
```As root, run visudo and add your user name in the same way root is entered. I had to do this on my own little project running Intrepid, but I think it should still work on Jaunty.

Hope this helps...:)

Thank you very much!

---

