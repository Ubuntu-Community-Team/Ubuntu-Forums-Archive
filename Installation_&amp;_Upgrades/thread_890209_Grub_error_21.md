---
title: "Grub error 21"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by DuKisa on 2008-08-14
HEllo, on freshly installed  kubuntu on first boot i got error grub 21. I search site but didn't find answer. Do you have suggestions/sollutions ? I`m running msi neo p965, and hdd sata2 maxtor..

---

### Post by rsambuca on 2008-08-14
That error means that the selected disk does not exist.  Did you change hard drives or configurations in bios after installation?

---

### Post by DuKisa on 2008-08-14
no i`m only set up first boot from hdd..

---

### Post by ercferret18 on 2008-08-14
since you just installed it, just reinstall

---

### Post by DuKisa on 2008-08-14
> **ercferret18 said:**
> since you just installed it, just reinstall

try to reinstall but notnihg.. something else. ?

---

### Post by rsambuca on 2008-08-14
How many Hard Drives do you have, and how are they partitioned?

---

### Post by caljohnsmith on 2008-08-14
We need more info to help you... Please boot up the Live CD, open a terminal and do:
```
sudo fdisk -l
```
And post the output of the above command. Your Kubuntu partition will be file system "linux" under the "system" category, look at what device it is, should be of the form /dev/sdaX. Then do:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst
```
And post the output.

---

### Post by DuKisa on 2008-08-15
I have successfully installed Ubuntu 8.04 on a system with an MSI P965 Neo motherboard. It wasn't easy, and I don't recommend it. There may be an easier way to do it: read the forums.
Here is a set of shell commands that mounts my ubuntu root partition as /mnt/ubuntu, then creates a chrooted shell with the hard drive mounted on "/". From this shell, I can use apt-get to install software.
sudo bash
mkdir /mnt/ubuntu
mount /dev/sda1 /mnt/ubuntu
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
cat /etc/resolv.conf >/mnt/ubuntu/etc/resolv.conf
chroot /mnt/ubuntu /bin/bash

The first time I tried this, I didn't update /etc/resolv.conf, and I didn't have working internet access from within the chrooted shell. I could ping my IP gateway, but I couldn't resolve DNS hostnames. The problem is that /etc/resolv.conf didn't exist on the hard drive (because I had never successfully booted from the hard drive).

The first time I tried to install Lilo, I had a problem with /etc/fstab. It contained some lines that confused the Lilo installer:
# /dev/sda1
UUID=5149cd61-ed5a-4234-9db7-a0c9f3502f7c / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5
UUID=e187c4cb-1c4e-4836-a910-6a3494a29a6c none swap sw 0 0

I changed these lines to look like this:
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0

Once in the chrooted shell with a working internet and a corrected /etc/fstab file, I installed Lilo like this:
apt-get update
apt-get install lilo
liloconfig # answer 'yes' or 'ok' to all questions
/sbin/lilo # answer 'yes' or 'ok' to all questions

Then I rebooted, and my system worked.

One consequence of replacing "grub" with "lilo" is that the Ubuntu boot and shutdown progress bars are replaced by lines of scrolling text that show you what the system is doing when it is starting up or shutting down. This is actually preferable, because if something goes wrong during startup, you need to be able to see the error messages so that you can type them into google and find help.

While this kind of thing is fun for some people, in retrospect, I wish I had either purchased a pre-configured Ubuntu system, or consulted the Ubuntu Hardware Support page *before* purchasing the system.

---

