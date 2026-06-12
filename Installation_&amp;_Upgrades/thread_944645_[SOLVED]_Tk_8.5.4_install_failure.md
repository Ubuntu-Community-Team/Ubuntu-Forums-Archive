---
title: "[SOLVED] Tk 8.5.4 install failure"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by MRM0607 on 2008-10-11
Dear Ubunutu user community,

I am new to ubuntu(linux) and I am new to Tcl/Tk as well. I need to install Tcl/Tk for another application (before its install). By mistake I uninstalled Tcl/Tk 8.5.4 from my UBUNTU machine. I installed TCL 8.5.4 from its TAR and it seems to working OK. But when I started installing Tk 8.5.4 from its TAR, make failed. I am listing first error it puts out.

mamta@requiem:~/Desktop/tk8.5.4/unix$ make
gcc -c -O2  -pipe  -Wall -Wno-implicit-int -fPIC -I/home/mamta/Desktop/tk8.5.4/unix/../unix -I/home/mamta/Desktop/tk8.5.4/unix/../generic -I/home/mamta/Desktop/tk8.5.4/unix/../bitmaps -I/home/mamta/Desktop/tcl8.5.4/generic -I/home/mamta/Desktop/tcl8.5.4/unix  -DPACKAGE_NAME=\"tk\" -DPACKAGE_TARNAME=\"tk\" -DPACKAGE_VERSION=\"8.5\" -DPACKAGE_STRING=\"tk\ 8.5\" -DPACKAGE_BUGREPORT=\"\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIMITS_H=1 -DMODULE_SCOPE=extern\ __attribute__\(\(__visibility__\(\"hidden\"\)\)\) -DTCL_SHLIB_EXT=\".so\" -DTCL_CFG_OPTIMIZED=1 -DTCL_CFG_DEBUG=1 -D_LARGEFILE64_SOURCE=1 -DTCL_WIDE_INT_TYPE=long\ long -DHAVE_STRUCT_STAT64=1 -DHAVE_OPEN64=1 -DHAVE_LSEEK64=1 -DHAVE_TYPE_OFF64_T=1 -DHAVE_SYS_TIME_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_INTPTR_T=1 -DHAVE_UINTPTR_T=1 -DHAVE_PW_GECOS=1      -DTCL_NO_DEPRECATED  -DUSE_TCL_STUBS  /home/mamta/Desktop/tk8.5.4/unix/../generic/tk3d.c

In file included from /home/mamta/Desktop/tk8.5.4/unix/../generic/tkInt.h:21,
                 from /home/mamta/Desktop/tk8.5.4/unix/../generic/tk3d.c:16:
/home/mamta/Desktop/tk8.5.4/unix/../generic/tk.h:78:23: error: X11/Xlib.h: No such file or directory

after this there is along list of error.

I was wondering if somebody could help me to install Tk and guide me what the error is and how to resolve it.

If this is not the right place to ask this question please let me know where I can post this question.

Thank you.
mrm0607

---

### Post by Partyboi2 on 2008-10-11
You can reinstall tk by searching for it in synaptic package manager (System>Admin>Synaptic Package Manager) or from a terminal
```
sudo apt-get install tk8.5 
```

---

### Post by MRM0607 on 2008-10-13
> **Partyboi2 said:**
> You can reinstall tk by searching for it in synaptic package manager (System>Admin>Synaptic Package Manager) or from a terminal
```
sudo apt-get install tk8.5 
```

Dear ubuntu user,

Thank you for the helpful mail.

Suggested command installed tk8.5

I would understand that by typing tk8.5 on the command line I should be able to invoke tk console but I do not see that.

I thought I shall mention I am new to Tcl/Tk as well.

When I installed Tcl8.5, I could see in /usr/local/bin an executable tclsh8.5 and when I type tclsh8.5 I can see % prompt. But in this case I do not see that.

Could you please suggest what could be the issue. I would appreciate your help.

Thank you.
mrm0607

---

### Post by Partyboi2 on 2008-10-13
If you where wanting to get a tk console I would say you would probably need to install tkcon package as well.
```
sudo apt-get install tkcon
```

You mentioned in your first post that you needed to reinstall tk8.5 and tcl8.5 both of these packages are in the ubuntu repos and can be install by searching with synaptic package manager, however if you are needing to install these packages so that you can compile another program you will need to probably install the development packages tk8.5-dev and tcl8.5-dev which can be done by searching synaptic or from a terminal
```
sudo apt-get install tk8.5-dev tcl8.5-dev
```

---

### Post by MRM0607 on 2008-10-14
> **Partyboi2 said:**
> If you where wanting to get a tk console I would say you would probably need to install tkcon package as well.
```
sudo apt-get install tkcon
```

You mentioned in your first post that you needed to reinstall tk8.5 and tcl8.5 both of these packages are in the ubuntu repos and can be install by searching with synaptic package manager, however if you are needing to install these packages so that you can compile another program you will need to probably install the development packages tk8.5-dev and tcl8.5-dev which can be done by searching synaptic or from a terminal
```
sudo apt-get install tk8.5-dev tcl8.5-dev
```

Dear ubuntu user,

How shall I access tcl. from command line

when I type tkcon, I can invoke it but when I type tcl8.5, I get bash error.

Thank you.
mrm0607

---

### Post by Partyboi2 on 2008-10-14
Maybe [[COLOR=Blue]this [/COLOR]]("http://ubuntuprogramming.wikidot.com/tcl")will help

---

### Post by MRM0607 on 2008-10-15
> **Partyboi2 said:**
> Maybe [[COLOR=Blue]this [/COLOR]]("http://ubuntuprogramming.wikidot.com/tcl")will help

Thank you.

I will try.

mrm0607

---

### Post by MRM0607 on 2008-10-16
> **Partyboi2 said:**
> Maybe [[COLOR=Blue]this [/COLOR]]("http://ubuntuprogramming.wikidot.com/tcl")will help

Dear ubuntu user,

Thank you.

Your suggestion worked.

I would like to ask question about the site you mentioned (perhaps it might sound silly to you). Site URL listed below

[http://ubuntuprogramming.wikidot.com](http://ubuntuprogramming.wikidot.com)

Is this a good to register with.

I am new to linux, Tcl and other object oriented languages. I have to use Python, Perl, PHP along with Tcl/Tk and perhaps some shell programming just to do my work.

So I thought I shall ask for your candid advise before joining this site for programming question.

Thank you.
mrm0607

---

### Post by Partyboi2 on 2008-10-16
It really depends on where you are at in the learning curve, best way would be to google around and see what you find, there are lots of free tutorial online for all different levels. Just a matter of finding the right one that you can understand.
Here are a few to get you started.

[http://www.ardenstone.com/projects/seniorsem/tcl/](http://www.ardenstone.com/projects/seniorsem/tcl/)
[http://users.belgacom.net/bruno.champagne/tcl.html](http://users.belgacom.net/bruno.champagne/tcl.html)
[http://www.bin-co.com/tcl/tutorial/contents.php](http://www.bin-co.com/tcl/tutorial/contents.php)
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)
[http://steve-parker.org/sh/philosophy.shtml](http://steve-parker.org/sh/philosophy.shtml)
[http://perl-begin.org/tutorials/](http://perl-begin.org/tutorials/)
[http://www.softwaretrainingtutorials.com/php-beginners.php](http://www.softwaretrainingtutorials.com/php-beginners.php)

---

### Post by MRM0607 on 2008-10-18
> **Partyboi2 said:**
> It really depends on where you are at in the learning curve, best way would be to google around and see what you find, there are lots of free tutorial online for all different levels. Just a matter of finding the right one that you can understand.
Here are a few to get you started.

[http://www.ardenstone.com/projects/seniorsem/tcl/](http://www.ardenstone.com/projects/seniorsem/tcl/)
[http://users.belgacom.net/bruno.champagne/tcl.html](http://users.belgacom.net/bruno.champagne/tcl.html)
[http://www.bin-co.com/tcl/tutorial/contents.php](http://www.bin-co.com/tcl/tutorial/contents.php)
[http://ubuntuforums.org/showthread.php?t=255970](http://ubuntuforums.org/showthread.php?t=255970)
[http://steve-parker.org/sh/philosophy.shtml](http://steve-parker.org/sh/philosophy.shtml)
[http://perl-begin.org/tutorials/](http://perl-begin.org/tutorials/)
[http://www.softwaretrainingtutorials.com/php-beginners.php](http://www.softwaretrainingtutorials.com/php-beginners.php)

Dear Forum user,

I truly appreciate your help.

Thank you.
mrm0607

---

