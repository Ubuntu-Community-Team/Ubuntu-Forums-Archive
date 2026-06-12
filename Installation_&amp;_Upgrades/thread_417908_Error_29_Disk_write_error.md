---
title: "Error 29: Disk write error"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by zend on 2007-04-22
I had successfully installed Ubuntu 6.10 earlier this week.  Then I saw that 7.04 came out.

I did a clean install of Ubuntu Desktop 7.04 and everything went fine, 

When the computer reboots it brings up grub and then says: Error 29: Disk write error.

I can get into recovery just fine.  Any ideas?

---

### Post by ecionci on 2007-04-22
Could you clarify a bit? Does the grub menu come up or just "grub>".

If so, do:
grub> find /boot/grub/stage1
then after it answers--grub>root (hd0,X)  X being your partition.
and then: grub>setup (hd0)
it should read out that it is setting up grub, i.e., Checking, etc. It will then install grub menu.
Type quit and reboot.
Hope that helps

**I forgot to mention that if you have been experiencing disk errors you could have a
problem with memory. Hope not.

---

### Post by zend on 2007-04-22
Sorry.  I can get the grub menu.  When I select the normal kernel, I get the error.  If I select recovery option then I can get in as root.

---

### Post by audiobahn on 2007-04-30
Hey ppl this is my first post so I hope it helps.

I got the same problem (ERROR 29: Disk write error) after I installed ubuntu feisty to dual boot with  Windows XP Professional. I tried all advice from above but nothing worked.  After a lot of work I finally made it work!!!

Here is how:

Find out on WHICH hd and WHICH partition windows is installed on (usually hd0,0) then edit the /boot/grub/menu.lst file by using sudo gedit /boot/grub/menu.lst

find the part were it says (or equivalent) : 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional

and then enter the following:

rootnoverify (hd0,0)
chainloader +1

NOTE : REPLACE the number of the windows partition at rootnoverify (hd0,0). For example if your windows is installed on hd1,0 change it to rootnoverify (hd1,0).
Normally grub would find the correct partition but put root (hd"correct partition for windows") so you only really need to change it from root to rootnoverify

DO NOT!!! leave the makeactive command. That is the main reason we get the error! Linux tries to write on the disk to set is as active but it cannot write on an NTFS disk (M$ sucks...)

Also after you boot in windows it might run chdisk leave it run until it finishes. It only runs once don't worry nothing important just windows being a smart *** ;)

HOPE it works for you :)

---

### Post by zend on 2007-05-05
My system is not dual booting.  I'm really not sure what is causing this.  I'll try a reinstall.

---

### Post by knobblysnail on 2007-06-04
Did you ever solve this grub disk write error?

I have the same problem where I can only boot into recovery mode. I am wondering if it has something to do with the HD not being on the first disk controller (hde).

cheers

---

### Post by mamnmamn on 2007-06-11
Hi,

I also have this error. I am no grub expert, or linux to that matter. If I boot to the recovery console then it will boot.

I am currently booting the box via the super grub disk. (worth a look if you need to boot the box.)

Please can anyone help as I would love to get this sorted. 

I am running Edgy Eft (6.10). I have tried the commands above and it commpletes successfully but still will not boot.

Cheers

---

### Post by mamnmamn on 2007-08-26
I had to return top this issue tonight as I could noot boot the server from the super grub disk. The clue was in thepost about the dual boot system. My system is a single boot linux system. Reading the dualboot post I realised that I should be looking for something in my grub menu.lst that was trying to write to the drive and failing. This was savedefault. I should really try to figure out why it could not write but I just scommented out this line as I do not need it. 

It worked and For the first time since install this box can now boot. Cheers all for the clues.

---

### Post by bazard89 on 2007-09-15
:( im getting the error too and now i cant boot xp either 

i tried what he said but aparently /boot/grub doesnt exist when i put that in terminal

i can go to the file and find menu.list but i cant save any changes

also im not sure how to find out which hd is which i have xp on one and ubuntu on the other

the one ubuntu is on is external and the smaller of the two

please help asap

---

### Post by bazard89 on 2007-09-15
ok i finally did it for some reason the file was in /media/disk/boot/grub?

but now that i made the changes at start up it just says
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
loading stage 1.5
.....
over n over n over >:( 
i can only run off the live cd right now

---

### Post by bazard89 on 2007-09-15
$%& ok i reinstalled ubuntu and the same thing is happening
i did the rootnoverify and the rest n now i dont get the repeated message but it still just stuck at error 29:disk write error :( please help i cant get on either OS only on the live cd

---

### Post by irishoddjob on 2007-10-25
I got this error today. Built a server, had it all ready to pack up and bring to the datacenter, and decided just for the hell of it that I'd test it booting without a keyboard and mouse (the way it would be down at the datacenter), sanity check, and voilla, Error 29: Disk write error

Putting back in the keyboard didn't fix it
Putting back in the keyboard and mouse allowed it to boot
Didn't try mouse on its own.

Followed the post that said to edit grub's menu.1st and look for something there that tries to write, namely savedefault, commented it out, and voilla it boots without the mouse.

Clearly a bios issue, but posting this anyway so that it might just help someone else.

---

### Post by eschramm on 2008-05-07
> **audiobahn said:**
> Hey ppl this is my first post so I hope it helps.

I got the same problem (ERROR 29: Disk write error) after I installed ubuntu feisty to dual boot with  Windows XP Professional. I tried all advice from above but nothing worked.  After a lot of work I finally made it work!!!

Here is how:

Find out on WHICH hd and WHICH partition windows is installed on (usually hd0,0) then edit the /boot/grub/menu.lst file by using sudo gedit /boot/grub/menu.lst

find the part were it says (or equivalent) : 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional

and then enter the following:

rootnoverify (hd0,0)
chainloader +1

NOTE : REPLACE the number of the windows partition at rootnoverify (hd0,0). For example if your windows is installed on hd1,0 change it to rootnoverify (hd1,0).
Normally grub would find the correct partition but put root (hd"correct partition for windows") so you only really need to change it from root to rootnoverify

DO NOT!!! leave the makeactive command. That is the main reason we get the error! Linux tries to write on the disk to set is as active but it cannot write on an NTFS disk (M$ sucks...)

Also after you boot in windows it might run chdisk leave it run until it finishes. It only runs once don't worry nothing important just windows being a smart *** ;)

HOPE it works for you :)

Just wanted to thank you for the fix you posted! It worked like a charm!

---

