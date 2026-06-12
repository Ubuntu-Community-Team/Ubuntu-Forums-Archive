---
title: "warty&gt;hoary&gt;breezy &quot;no space left on device&quot;"
date: 2006-05-19
forum: Installation &amp; Upgrades
---

### Post by norv on 2006-05-19
Hi,
I have just done a Warty install from an old Ubuntu CD, upgraded to Hoary and then Breezy via apt-get dist-upgrade.
I have had to manually remove old kernel stuff from /boot and /lib/modules to get around "no space left on device" messages.
Now I have Breezy mostly working but a few packages are still stuck.
Here is my df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             250M  222M   16M  94% /
tmpfs                 216M  4.0K  216M   1% /dev/shm
tmpfs                 216M   14M  203M   7% /lib/modules/2.6.12-10-amd64-generic/volatile
/dev/sda14            8.7G   61M  8.2G   1% /home
/dev/sda13            361M  8.1M  334M   3% /tmp
/dev/sda10            4.6G  1.5G  2.9G  34% /usr
/dev/sda11            2.8G  762M  1.9G  29% /var

(This is a dual-boot AMD64 box)
You can see my / partition is almost full.

This my /lib/modules and uname -a:

norbunto@ubuntu64:/ $ ls /lib/modules
2.6.12-10-amd64-generic  2.6.12-10-amd64-k8
norbunto@ubuntu64:/ $ uname -a
Linux ubuntu64 2.6.12-10-amd64-generic #1 Fri Apr 28 13:18:42 UTC 2006 x86_64 GNU/Linux
norbunto@ubuntu64:/ $ ls /boot
abi-2.6.12-10-amd64-generic     initrd.img                          vmlinuz
abi-2.6.12-10-amd64-k8          initrd.img-2.6.12-10-amd64-generic  vmlinuz-2.6.12-10-amd64-generic
config-2.6.12-10-amd64-generic  memtest86+.bin                      vmlinuz-2.6.12-10-amd64-k8
config-2.6.12-10-amd64-k8       System.map-2.6.12-10-amd64-generic
grub 

Where could I make some space in / partition to complete building of -k8 kernel and install remaining packages?
Thanx to Ubuntu team for a great distro
Norv

---

### Post by Sef on 2006-05-19
Try this:

sudo apt-get clean

sudo apt-get autoclean

if you can download baobab

From the about: A graphical tool to analyse directory trees.

You can delete what you don't need.

---

### Post by norv on 2006-05-19
Thanks Sef. I tried apt-get clean, autoclean but the problem persists. Can't get baobab coz apt-get is blocked by the blocked linux-image pkg that won't install due to no disk space.
Maybe I should download a Breezy install Cd and start from scratch?

Some dirs in my / partition are
/bin 5.2MB
/boot 10.8MB
/etc 37.2MB
/lib 154MB
/proc 512MB
/sbin 10.6MB
/srv 15.5MB
/sys 183MB
/tmp 18.2KB 
 Some of these seem very high for a / partition that is only 250MB.
Where could I make some space? Clearing /tmp would only save 18KB.

---

### Post by norv on 2006-05-20
Just had a thought - the kernel directories in /lib/modules take up around 50MB of space each.
If I am running kernel 2.6.12-10-amd64-generic, can I delete the corresponding directory from /lib/modules?
ie is that directory used for just building the kernel or for running it as well?

---

### Post by norv on 2006-05-23
I solved all this by downloading a Breeezy 5.10 install cd image and installing Breezy from scratch into one partition.

---

### Post by MiniJames on 2006-05-24
[QUOTE=Sef]Try this:

sudo apt-get clean

sudo apt-get autoclean

if you can download baobab

From the about: A graphical tool to analyse directory trees.

You can delete what you don't need.[/QUOTE]

Thanks :)

---

