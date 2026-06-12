---
title: "Gimp 2.6 issues with intrepid"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by afalldorf on 2008-10-16
I recently upgraded to the new beta of intrepid and as expected there were many issues but this one seems to actually have something to do with gimp and not ubuntu. So here is what I get when I load gimp in the terminal:
```
adam@ALIENLAPTOPUBUNTU:~$ '/usr/bin/gimp-2.6' 
babl-extension.c:178 babl_extension_load()
	dlopen() failed:
	/usr/lib/babl-0.0/sse-fixups.so: undefined symbol: babl_cpu_accel_get_support
/usr/bin/gimp-2.6: symbol lookup error: /usr/bin/gimp-2.6: undefined symbol: babl_get_version

```
Any Ideas? because I have no idea whats going on. I know other people have had no problem with gimp in intrepid.

---

### Post by gjoellee on 2008-10-16
Yes you get a lot of issues if you don't do a clean install!!! However have you tried loading GIMP from the menu??

---

### Post by afalldorf on 2008-10-16
Yes I have tried running it in every way I could think of. And before you ask I also tried reinstalling it. ;)

---

### Post by jespdj on 2008-10-16
It sounds like you are using the wrong version of the BABL library (one of the libraries used by GIMP 2.6). Did you install the right version of BABL? Did you remove any old versions of the library?

---

### Post by afalldorf on 2008-10-16
A Fresh install is looking better and better... But I would really like to just make it work the way it is... I have been able to solve all of my other issues and this one is the only one left to be dealt with. Any help would be appreciated.

Edit: To the post above. Im not sure what the babel library is but I did install babel in the package manager in a noobish attempt at fixing it.

---

### Post by afalldorf on 2008-10-16
Ok I have looked into it a little more and as far as I can tell I have the newest version of libbabl (0.0.22-1) So unless there is a newer one I don't see that being the problem... maybe it is too new?

---

### Post by afalldorf on 2008-10-16
I have officially given up I am going to do a fresh install. I have found a few other things that are not working like they should and it looks like the upgrade is the cause. So I guess this topic is closed unless I still have this problem after the reset.(Knock on Wood)

---

### Post by afalldorf on 2008-10-16
Ok now everything works! YAY! I downloaded the cd and did a fresh install and then updated the gimp It all appears to be working so it must have been something from the old distro that was causing it to not work.
Thanks!

---

