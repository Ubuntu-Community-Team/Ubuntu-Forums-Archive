---
title: "help to install gcc (offline)"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by surendar164 on 2008-07-16
i am new to Ubuntu..i think i am using version 7.0 ubuntu...

i installed it from digit DVD..

i downloaded a gcc-4.0.0-8.i386.rpm package from internet and i want to know how to extract it and use the comiler to run a C program.......

i refered some threads here to install rpm or alien package..i think they r possible only online....

i want to install some package to extract the compiler  offline...

thanks in advance...
:(:(

---

### Post by lisati on 2008-07-16
Presumably you are using 7.04 which is what I use (there wasn't a 7.0)

An internet connection would be useful: in order for me to use the C compiler, I had to enter at the terminal ```
sudo apt-get build-essential
``` - I'm not sure if it's on the CD/DVD, my system downloaded it from the internet. I haven't actually used the RPM file to install gcc.

---

### Post by quantum-positron on 2008-07-16
Well first off you .rpm files are for linux varients such as Fedora Core or openSUSE not ubuntu. For Ubuntu you want .deb packages. The easiest way to install it would be through the terminal.

sudo apt-get install gcc

If you plan to do alot of compiling you will probably end up needing other tools as well in which case i would recomend installing this pakage as well.

sudo apt-get install build-essential

---

### Post by surendar164 on 2008-07-16
thank u for d instant reply friends...

i dont have an internet connection...

i just want to use gcc 4.0.0-8 version to compile my c progams(for SPOJ online programming contest)...after googling i got only an rpm package of that version...

is that easy to install that gcc version offline???
any solution to my prob??its urgent plz...

any idea about Dev-c++(i cudnt compile my C source code)

error is "cannot set GNU make path(not sure)" "cannot find file"

:(

---

### Post by Partyboi2 on 2008-07-16
maybe you could modify [[COLOR=Blue]this how to[/COLOR]]("http://ubuntuforums.org/showthread.php?t=79896") and use these packages instead of the ones provided in the first step
[http://packages.ubuntu.com/gutsy/gcc-4.2-base](http://packages.ubuntu.com/gutsy/gcc-4.2-base)
[http://packages.ubuntu.com/gutsy/gcc-4.2](http://packages.ubuntu.com/gutsy/gcc-4.2)
[http://packages.ubuntu.com/gutsy/cpp-4.2](http://packages.ubuntu.com/gutsy/cpp-4.2)

---

