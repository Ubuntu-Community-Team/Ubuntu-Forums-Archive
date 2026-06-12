---
title: "Affix installation"
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by mozz on 2005-07-23
Hi,

I want to use bemused and therefore I tried to install Affix but - surprise, surprise - I can't make it work...maybe someone of you could help me :)

So I downloaded affix and the affix source with synaptic and installed it...affix didn't start
I found this doc [Affix install](http://affix.sourceforge.net/affix-doc/a1489.html) - ./Configure worked 
(Script asked for linux source path [/usr/src/linux], but there was none, so I downloaded the linux-headers...hope that was right)

but the 'make all' command gave this output:

> Checking kernel checksum ...
make[1]: Going to directory »/usr/src/modules/affix«
Compiling driver and control programs
make[2]: Going to directory »/usr/src/modules/affix/btcore«
make[2]: *** No rules available, to create target »affix.ko«,
  required by »all«.  End.
make[2]: Leaving directory »/usr/src/modules/affix/btcore«
make[1]: *** [build] Error 2
make[1]: Leaving directory »/usr/src/modules/affix«
make: *** [all] Error 2 

(Sry, had to translate it to english, so it might not sound *exactly* as the english error messages)

Hope someone knows what to do, I would really appreciate it!

---

