---
title: "ctrlaltf1 root already loged in"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by belda on 2005-06-02
I got a fresh 5.04 install with couple of small problems(not working net), but these i solved.
What wories me is that there was no question during install for root passwd, so I've set one by passwd, but still when I switch to console ctrl+alt+f1, the root is already loged in and I can not logout.

The other thing is, that i created more users via the gnome interface and they should be the same as the user created during the install. But when I try to run, loged as one of these, some admin progs, it asx me for a passwd,but none is correct:-)

---

### Post by kvidell on 2005-06-02
[QUOTE=belda]I got a fresh 5.04 install with couple of small problems(not working net), but these i solved.
What wories me is that there was no question during install for root passwd, so I've set one by passwd, but still when I switch to console ctrl+alt+f1, the root is already loged in and I can not logout.

The other thing is, that i created more users via the gnome interface and they should be the same as the user created during the install. But when I try to run, loged as one of these, some admin progs, it asx me for a passwd,but none is correct:-)[/QUOTE]
 That's what you get for meddling :-P

By default there is no "root" access to or in Ubuntu. Everything is done happily via SUDO.
If you add more users and want them to have full access you need to check the sudoers file and make sure it's pointing at %admin
If so, go in to /etc/group and add the aforementioned users to the "admin" group. That should do you nicely.

As for the thing already being logged in... are you sure that's not just the session X is running in? Did you do something silly (other than meddle with the root/admin structure :-P)

If I'm not being specific enough, just say so and I'll try to refine my answer (read: bickering) for you.
- Kev
Edit: Read this: [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

### Post by belda on 2005-06-03
oh,it is so than :-)))) , sudo for everything, seems strange to me, anyway what i did was that my X was not working (black screen), so i ctraltf1 a tried to restart it, which worked (now i know ctrlaltbs:0), i found out,that root is loged in,so i set passwd to it, and thats all,what can be strange about my actions

and the users, well i didnt know about the "sudo for everything", so i gave those people my group,but thats not bothering me, i am woried that anyone who'll come to the terminal can have root

---

### Post by mingus on 2005-06-03
so are you able to login to the Gnome interface (the Ubuntu graphical login screen)?

---

### Post by belda on 2005-06-04
yes, i solved it by adding something like video=734 (or something like that) to grub config

---

### Post by kvidell on 2005-06-04
[QUOTE=belda]oh,it is so than :-)))) , sudo for everything, seems strange to me, anyway what i did was that my X was not working (black screen), so i ctraltf1 a tried to restart it, which worked (now i know ctrlaltbs:0), i found out,that root is loged in,so i set passwd to it, and thats all,what can be strange about my actions

and the users, well i didnt know about the "sudo for everything", so i gave those people my group,but thats not bothering me, i am woried that anyone who'll come to the terminal can have root[/QUOTE]
 Well... not anyone... They still have to guess your password before it'll work :)
There was ~some~ forethought in this whole process, afterall :)

---

### Post by mingus on 2005-06-04
[QUOTE=belda]yes, i solved it by adding something like video=734 (or something like that) to grub config[/QUOTE]

Can be important to be sure about the framebuffer value.  If a value higher than what the monitor (or in particular, a laptop display) can handle, it can be damaged.    GRUB can handle either decimal or hex, lilo now also though older versions only decimal.

    | 640x480  800x600  1024x768 1280x1024
----+-------------------------------------
256 |  0x301    0x303    0x305    0x307
32k |  0x310    0x313    0x316    0x319
64k |  0x311    0x314    0x317    0x31A
16M |  0x312    0x315    0x318    0x31B 


     640x480  800x600 1024x768 1280x1024
256 	769 	771 	   773 	          775
32K 	784 	787 	   790 	          793
64K 	785 	788 	   791   	  794
16M 	786 	789 	  792   	 795

---

### Post by belda on 2005-06-06
maybe it'll help me,when somebody post here his sudoers file, I sense the problem to be in there

---

