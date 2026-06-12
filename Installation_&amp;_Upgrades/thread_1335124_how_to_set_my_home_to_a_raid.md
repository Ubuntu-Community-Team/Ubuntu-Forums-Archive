---
title: "how to set my /home to a raid?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by machinakias on 2009-11-23
hi everyone!
just need some help please....
i want to do this: install ubuntu as usual but i need to have my /home/username directory installed to a raid (mirror) .....
i want to setup some virual machines and i wanna be sure of my data and work!
hope you understand what i need to do....got any ideas?

---

### Post by darkod on 2009-11-23
Do you want to have only /home on raid or / too?

I haven't used it myself but from reading about LVM and RAID you have to use the Alternate Install ISO, not Desktop. It has text based installer (not GUI) but has more advanced options for lvm and/or raid. After the install is finished the desktop is still GUI, just during the install process it's text based.

Once it recognizes the raid I see no reason not to be able to have /home, / or whatever on a raid array.

---

### Post by i.r.id10t on 2009-11-23
After the fact, assuming you have a single disk and one big / partition, it is easy.

Plug your 2 disks for the raid in, create your raid volume, mount it at /newhome, log out as your user, log into command line as root, copy your /home/* stuff to /newhome, rename /home to /oldhome, unmount /newhome, mkdir /home, mount the volume at /home, edit /etc/fstab

---

### Post by machinakias on 2009-11-23
first of all,thanks for your replies folks!
let me be more specific....
i'm setting up an 8.04 ubuntu server.(i want to set some virtual machines in it)

i have 3 hard disks,one for main operating system and i want to move my /home/username directory to the other two (as a RAID) if possible...
or even better,to set one disk for use with one virtual machine and the other disk for another vm....

does it make any sence? can i do it somehow?

---

### Post by gurak2005 on 2009-11-24
this guide works for me. hope will work for you

[http://kuparinen.org/martti/comp/ubuntu/en/raid.html](http://kuparinen.org/martti/comp/ubuntu/en/raid.html)

---

