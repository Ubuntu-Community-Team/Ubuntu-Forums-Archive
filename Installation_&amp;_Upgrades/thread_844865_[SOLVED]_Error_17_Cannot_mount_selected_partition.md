---
title: "[SOLVED] Error 17: Cannot mount selected partition"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by bonfire89 on 2008-06-30
Hi,

I'm getting

*Error 17: Cannot mount selected partition*

on my first boot.


I have received this with xubuntu, and now currently ubuntu server 8.04

I have a total of 4 hard drives, I know they all work etc as they ran under windows. Furthermore, I have had Linux media center on this exact computer in the past and it ran and all drives were detected etc.


Finally, I had also installed xbuntu with only the one hard drive then attached the others after. xbuntu ran, but I was not able to see the other drives from the installation.


I know how to edit grub and all, and have been trying random drive numbers and partitions. Is there a way to get a list? I should only have one ext3 partition in the computer.
Thanks :)

---

### Post by VMC on 2008-06-30
> **bonfire89 said:**
> Hi,

I'm getting

*Error 17: Cannot mount selected partition*

on my first boot.


I have received this with xubuntu, and now currently ubuntu server 8.04

I have a total of 4 hard drives, I know they all work etc as they ran under windows. Furthermore, I have had Linux media center on this exact computer in the past and it ran and all drives were detected etc.


Finally, I had also installed xbuntu with only the one hard drive then attached the others after. xbuntu ran, but I was not able to see the other drives from the installation.

Thanks :)

In that case we need to be able to identify all your hard drives:

From a Terminal type:

```
sudo fdisk -l
```

copy and paste its entirety back here.

---

### Post by bonfire89 on 2008-06-30
heh, I wassn't able to get a terminal.


buuut!!!


It just started after guessing the drive! I don't remember which worked.. I will have to guess again next time. heh

But thanks!

---

### Post by smo0th on 2008-06-30
> **bonfire89 said:**
> heh, I wassn't able to get a terminal.


buuut!!!


It just started after guessing the drive! I don't remember which worked.. I will have to guess again next time. heh

But thanks!

LOL

well.. if you solved the problem by guessing it's ok I guess(:lolflag:) but if you have the error back somehow, post back here and I'll be able to help you since I got thru it.

---

### Post by bonfire89 on 2008-06-30
heh, well, it just seems like the settings setup by the installer for which drive to boot off was wrong.

So if you have a relatively low number of drives...

hd0,0
hd0,1
hd1,0
hd1,1
hd2,0
hd2,1
hd3,0
hd3,1

in my case since I have 4 drives and the drive linux is installed on has two partitions due to the swap file. The rest of the drives have one partition each.

Good Good. That was frustrating initially.

---

### Post by pooyaplus on 2008-06-30
Howdy guys. I have been trying to solve the "grub loading stage 1.5 error 18" after a power prob. After a googling the error and changing the primary and slave to normal from auto option in the BIOS; I get the error again.

Any helps would be appreciated.

P.S. I could not mount the root partition to reinstall the grub with the gparted app of a live cd. No idea why. By the way, the dmesg gives me a bunch of I/O errors in some sectors of the HD.

Cheers.

---

### Post by pooyaplus on 2008-06-30
Hi guys,
I was just playing around with the BIOS settings, and realised that the normal option of the primary IDE will result in getting the error 17 instead of error 18 that it kept giving me.

---

### Post by pooyaplus on 2008-06-30
And still unable to mount the /dev/sda1 :(

---

### Post by upchucky on 2008-06-30
hey Poo, it looks like the original poster solved his problem and marked the thread as such.

if you are still havin problems then make a different thread as this one will not get much attention since it is solved.

but before you make a new thread, search for the error you mentioned, there are hundreds of threads of these errors and the fixes are already in those threads.

In the future tagging a help onto someones thread is considered hijacking a thread as it can create confusion for the original poster and he may not get the help he asked for.

Just a bit of friendly advice :)

---

### Post by pooyaplus on 2008-06-30
thanks for the advice.
But I have spent almost all my day to search and try the solution in the ubuntuforum and grub man pages.

Making a new theread on and on for every single problem that we may face makes it extremely time consuming for guys to cover them all to find an appropriate solution. And that's the point you may have missed. :)

Thanks for the advice anyway.

---

