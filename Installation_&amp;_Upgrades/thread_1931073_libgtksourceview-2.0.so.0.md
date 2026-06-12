---
title: "libgtksourceview-2.0.so.0?"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by dkdDarKeneDdkd on 2012-02-24
After trying to run a program through the terminal, I initially got an error saying I needed to have libgtksourceview-1.0.so.0. No big deal, installed it, great, but then after trying to run that same program again, I got this message:
[HTML]./RC: error while loading shared libraries: libgtksourceview-2.0.so.0: cannot open shared object file: No such file or directory[/HTML]
I've been looking around all day trying to find something that is compatible with Ubuntu 11.10 x64 (What I'm running), but I've had no luck. I have both libgtksourceview-1.0.so.0 and libgtksourceview-3.0.so.0, but no libgtksourceview-2.0.so.0, the one I need. I'm new to Ubuntu and Linux in general, so I apologize if this is actually a very easy fix.
Thanks in advance!

---

### Post by azmyth on 2012-02-24
sudo apt-get install libgtksourceview-2.0-0

---

### Post by dkdDarKeneDdkd on 2012-02-24
[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtksourceview-2.0-0
E: Couldn't find any package by regex 'libgtksourceview-2.0-0'[/HTML]

No dice. :(

---

### Post by oldos2er on 2012-02-24
Which version of Ubuntu are you running? What is the program you're trying to run? Did you install it from the repositories, or ?

---

### Post by dkdDarKeneDdkd on 2012-02-24
> **oldos2er said:**
> Which version of Ubuntu are you running? What is the program you're trying to run? Did you install it from the repositories, or ?

As posted in the original post, I'm running Ubuntu 11.10 64 bit; the program is just an extension to a game; I know others that are able to use it on the same version of Ubuntu, so I know it isn't just me. It's just an executable; doesn't require any installation.

If there's any way to get libgtksourceview-2.0.so.0 / libgtksourceview-2.0-0 or which ever one it is, I believe it will fix the problem, but I've been online all day and have found nothing.

---

### Post by azmyth on 2012-02-24
You have synaptic installed? Open synaptic then Settings - Repositories on the first tab ubuntu software  make sure the second one down is checked (universe) then reload then try installing the package in my previous post.

---

### Post by dkdDarKeneDdkd on 2012-02-24
> **azmyth said:**
> You have synaptic installed? Open synaptic then Settings - Repositories on the first tab ubuntu software  make sure the second one down is checked (universe) then reload then try installing the package in my previous post.

Trying now, I'll update this with results

---

### Post by azmyth on 2012-02-24
How did you install this, libgtksourceview-1.0.so.0? It's not on my system nor is there a package as I'm running the same rev as you. I suspect this has broken your system.

---

### Post by dkdDarKeneDdkd on 2012-02-24
> **azmyth said:**
> How did you install this, libgtksourceview-1.0.so.0? It's not on my system nor is there a package as I'm running the same rev as you. I suspect this has broken your system.

I had to remove libgtksourceview-1.0-0 as synaptic wouldn't install when it was on my system, but after viewing my repositories, the second option down IS in fact checked, and I still get this result:
[HTML]alex@alex-TA790GX-128M:~$ sudo apt-get install libgtksourceview-2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtksourceview-2.0-0
E: Couldn't find any package by regex 'libgtksourceview-2.0-0'[/HTML]


EDIT:: Problem solved... I installed the packages by using synaptic, not terminal. It seemed to do the trick.

Thanks for all of the help!

---

