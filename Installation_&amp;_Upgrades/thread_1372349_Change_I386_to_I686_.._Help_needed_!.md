---
title: "Change I386 to I686 .. Help needed !"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by NawafLol on 2010-01-04
Hey Ubuntu User's !

After by mistake changing my kernel to i386 (wish was a bad idea )

the case here is with every new kernel update e.g : linux-kernel-2.6.31-17 ... isn't for i686 ,it just updates the 386 kernel !

Well my point here that i want to drop the support for i386 and get back to good old i686 ! 


Other then that my kernel is 2.6.31-15-generic (as you can see not the newest ) 

OS :Ubuntu 9.10 Karmic Koala 

Keep on Ubuntuing =D !

---

### Post by snowpine on 2010-01-04
Ubuntu does not support i686, so I think i386 is correct. :)

---

### Post by NawafLol on 2010-01-04
Noo i'm sure that's it was i686 

This is the out put of uname -m : i686 

I have been using i686 for how long i remember then i switched to i386 and messed everything up !

I also have Intel Core 2 Due !

but Thanks Snowpine =D !

---

### Post by jocko on 2010-01-04
> **NawafLol said:**
> Hey Ubuntu User's !

After by mistake changing my kernel to i386 (wish was a bad idea )

the case here is with every new kernel update e.g : linux-kernel-2.6.31-17 ... isn't for i686 ,it just updates the 386 kernel !

Well my point here that i want to drop the support for i386 and get back to good old i686 ! 


Other then that my kernel is 2.6.31-15-generic (as you can see not the newest )
Not exactly sure what you mean. Do you mean you have accidentally installed a -386 kernel?
First make sure you have the generic kernel:
```
sudo apt-get update
sudo apt-get install linux-generic linux-header-generic
```
Then uninstall the -386 kernel (search for "-386" in synaptic and uninstall any installed packages whose name starts with "linux").

---

### Post by rccrandall on 2011-10-26
Hello Everyone! So Trying to find i686 a distro/download of, for example, Ubuntu Studio is fruitless at this point in time?

---

