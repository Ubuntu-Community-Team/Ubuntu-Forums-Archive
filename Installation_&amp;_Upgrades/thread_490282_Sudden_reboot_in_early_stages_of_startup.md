---
title: "Sudden reboot in early stages of startup"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by WebAsh on 2007-07-02
Hey,

I recently installed Dapper Drake on an old Compaq Armada 1550T that I picked up off my nana (lol). It's 133MHz with 48MB of RAM and a 6GB HDD.


Anyway, did a server install (which loads in low memory mode), but on boot after installation is complete and now on every boot, it gets as far as you can see in the image attached and then just instantly reboots the machine without any errors or anything.


What would this be and how can I fix it?



If you need some more information just ask :)







Cheers

---

### Post by WebAsh on 2007-07-02
By the way, sorry about the quality of the image, took it with my cellphone.

---

### Post by snakeman on 2007-07-02
I have the same issue with an old K6-3 400 with no acpi in the bios.  Machine installed fine.  We were going to use it as a server.  I tried to edit the boot string with acpi=off but no luck.  I have 320 megs off ram installed.



TIA,



snakeman

---

### Post by confused57 on 2007-07-02
You can use the alternate cd for a server install:
[http://ubuntuforums.org/showthread.php?t=290903&page=2](http://ubuntuforums.org/showthread.php?t=290903&page=2)

Another possiblity:
[http://ubuntuforums.org/showpost.php?p=2371357&postcount=5](http://ubuntuforums.org/showpost.php?p=2371357&postcount=5)

---

### Post by WebAsh on 2007-07-02
The alternate server cd is what i used to install, so I'll give the other possibility a go. Thanks :)

I'll give them a go soon or tonight and report back.


Quite odd that it's able to switch itself to low memory mode in setup, but not to run/load the right kernel? Would be nice for the option at least somewhere.

---

### Post by confused57 on 2007-07-02
> **WebAsh said:**
> The alternate server cd is what i used to install, so I'll give the other possibility a go. Thanks :)

I'll give them a go soon or tonight and report back.


Quite odd that it's able to switch itself to low memory mode in setup, but not to run/load the right kernel? Would be nice for the option at least somewhere.
The server install cd(approx. 480 Mb) is not the same thing as the alternate install cd(698 Mb)...just in case you used the former.  You would select "Command Line Install", using the alternate install cd, to install a server.

---

### Post by WebAsh on 2007-07-03
Swapping out the server kernel and replacing with the 386 one worked the trick. :)

---

