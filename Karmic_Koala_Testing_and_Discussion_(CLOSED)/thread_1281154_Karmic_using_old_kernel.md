---
title: "Karmic using old kernel"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thecow on 2009-10-03
Hello I recently updated to the Karmic beta. When I type uname -r I get the following:

$ uname -r
2.6.30-020630-generic


When using 9.04 I had updated to this kernel version because of some fixes I was looking for. However Karmic uses 2.6.31 so it's odd to me that this isn't the kernel version being used. During bootup if I hit 'esc' during Grub startup I see no entry for 2.6.31. 

Ive already tried the sudo update-grub command and restarted, however it doesn't allow me to use 2.6.31

Any help would be appreciated





I tried to change /boot/grub/menu.lst by adding in the appropriate fields i.e:

## ## End Default Options ##

title	 Ubuntu 9.10, kernel 2.6.31-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.31-11-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro quiet splash 
initrd	 /boot/initrd.img-2.6.31-11-generic
quiet


title	 Ubuntu 9.04, kernel 2.6.30-020630-generic
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.30-020630-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro quiet splash 
initrd	 /boot/initrd.img-2.6.30-020630-generic
quiet

title	 Ubuntu 9.04, kernel 2.6.30-020630-generic (recovery mode)
root	 (hd0,0)
kernel	 /boot/vmlinuz-2.6.30-020630-generic root=UUID=46cb7bd8-65c6-4d3b-8bc9-3536fa175995 ro single
initrd	 /boot/initrd.img-2.6.30-020630-generic




I added in the top one in what I thought was the same format as whats listed below it. However during boot it gives me an error and will not continue

---

### Post by ram2500 on 2009-10-03
It did definitely replace it, but why??? Methinks it's probably because it somehow reverted to what 9.04 uses...I don't know my kernel versions, though. Sadly I don't even know what I use! (without cheating and going to uname, though.

---

### Post by thecow on 2009-10-03
I think its because when installing the beta I didnt opt for the fresh version of menu.lst and went for keep the old one.  

Now it seems to have bitten me fairly hard.  When I boot it first boots into 9.04 style logos, then after that it boots into 9.10.  The process actually takes a decent amount of time, longer than before I upgraded to the beta

---

