---
title: "Not able to boot , grub error 15 :("
date: 2008-08-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-08-17
Hi all, 
 
 I have grub 2 installed, specifically grub 1.96+20080512-1ubuntu2 . I had 2 disks, one of which I disconnected. I ran the usual updates and upgrades last evening. Everything got updated right. I did the usual shutting down of the machine
 
When I started the machine again, I got the grub error 15. I tried to fix it by giving the following command 
 
```

$ find /boot/grub/stage1

```
 
but to no avail. It gives a "command  not found ". Not what or how should I fix that? 
 
Any help/suggestion for the same is welcome.

---

### Post by Gina on 2008-08-17
Seems to me it's trying to boot from the disk you removed.  You could try reconnecting that drive and see if the problem goes away.

---

### Post by caljohnsmith on 2008-08-17
So you get the Grub error 15 on startup before seeing the Grub menu, or do you get that error after choosing Intrepid from the Grub menu? 

That find command you tried to use should be used in the Grub CLI, not the bash CLI. Try:
```
sudo grub
grub> find /boot/grub/stage1
```

---

### Post by ShirishAg75 on 2008-08-18
I get this error after choosing any of the Intrepid kernels from the GRUB menu. The find command is not there in grub CLI although I will still try again by doing sudo grub on the grub prompt itself. 

Would let you know how it goes from there.

---

### Post by ronacc on 2008-08-18
if you can boot another install on the box or the livecd check the drive designation <hd(?,?)> AND UUID in your menu.lst , there are some reports of intrepids grub installer entering the wrong ones .

---

### Post by ShirishAg75 on 2008-08-18
I would try l8er, some more info. though on the same. 
 
One gets a menu something like this :-
 
Chainload to Grub 2
 
list of kernels
 
 
 
now if I edit and ask for finding stage 1 its able to find it, (hd0,0) but if I try to boot it as given in the some of the stuff, it goes off on reboot. 
 
If I however go to grub2 and then try to edit it, don't know how to edit it , there the info. is not correct, its showing as (hd1.1) when it should be (hd0,0) 
 
how do I correct it? any ideas are welcome.

---

### Post by ronacc on 2008-08-18
I never played with grub2 so I can't help there .

---

### Post by cariboo on 2008-08-18
I was playing with grub2 earlier on, documentation is hard to come by, but I found a page that suggested to run:

```
dpkg-reconfigure grub2
```

This helped me get it working, as I was getting the same errors as you. Of course you have to be able to boot to do this. You should be able to boot from the live cd and then chroot your / directory and then run the command.

Jim

---

### Post by Gina on 2008-08-20
I have no problem with grub - what's the advantage(s) of grub2?

---

### Post by Nullack on 2008-08-20
Its a big rewrite.

ShirishAg75 if your using a non Intrepid build level its better to say that upfront :)

---

### Post by Bodsda on 2008-08-20
Im not sure if grub error 15 is the same as grub 2's error 15 but i have a link to all things grub error related 

[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

check your   menu.lst and your device.map to make sure your getting the drive numbers correct

---

