---
title: "GCC in $PATH"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by TorQ on 2005-04-23
Hello everyone,

I just installed GCC so that I can compile a program .  When I go to ./configure the software I get "configure: error: no acceptable C compiler found in $PATH".  I'm pretty new to Linux and this whole path thing has got me befuddled!  Where does "$PATH" live and how can I find GCC and add it to the path?  Thanks for your help.


TorQ

---

### Post by diebels on 2005-04-23
my gcc is in /usr/bin/gcc . Try installing build-essential.

$PATH lives in your enviroment. See it with "echo $PATH". It is set by the files /etc/profile and ~/.bash_profile

Locate gcc with "locate gcc" , or find / -name '*gcc*'

---

### Post by Paha Pukki on 2005-04-23
[QUOTE=TorQ]
I just installed GCC so that I can compile a program .  When I go to ./configure the software I get "configure: error: no acceptable C compiler found in $PATH".  I'm pretty new to Linux and this whole path thing has got me befuddled!  Where does "$PATH" live and how can I find GCC and add it to the path?  Thanks for your help.
[/QUOTE]

Don't forget to install the "gcc" package besides the "gcc-3.3" (or "gcc-3.4" or "gcc-4.0") package. Or did you do that already?

---

### Post by TorQ on 2005-04-23
Well, that was it.  I thought that  gcc and gcc3.3 was the same thing.  Now I can't seem to find glib-config...  Arrrggh  must  compile  software..

---

