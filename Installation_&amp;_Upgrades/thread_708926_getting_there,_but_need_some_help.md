---
title: "getting there, but need some help"
date: 2008-02-26
forum: Installation &amp; Upgrades
---

### Post by Tomana on 2008-02-26
trying to install gnomeSword, here's how far I've gotten


tomana@HAL:~$ cd ~/Desktop
tomana@HAL:~/Desktop$ cd gnomesword-2.1.7
tomana@HAL:~/Desktop/gnomesword-2.1.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GNOME... tomana@HAL:~/Desktop/gnomesword-2.1.7$ make
make: *** No targets specified and no makefile found. Stop.
tomana@HAL:~/Desktop/gnomesword-2.1.7$


why does the MAKE command not work?

---

### Post by taurus on 2008-02-26
> **Tomana said:**
> trying to install gnomeSword, here's how far I've gotten


tomana@HAL:~$ cd ~/Desktop
tomana@HAL:~/Desktop$ cd gnomesword-2.1.7
tomana@HAL:~/Desktop/gnomesword-2.1.7$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
**[COLOR="Blue"]checking for GNOME...[/COLOR]** tomana@HAL:~/Desktop/gnomesword-2.1.7$ make
make: *** No targets specified and no makefile found. Stop.
tomana@HAL:~/Desktop/gnomesword-2.1.7$


why does the MAKE command not work?

Doesn't look like ./configure has finished running so why don't you wait for it to finish first and see if there is any error message.  And if there is not, then run the make command.

---

### Post by Tomana on 2008-02-27
that's as far as it goes, I just tried it and when it gets to

checking for GNOME... tomana@HAL:~/Desktop/gnomesword-2.1.7$

it just sits there, no HDD activity, nada. I waited about 3 minutes.

There's Ubuntu Christian Edition that has sword already installed
but it's version 7.04 and doesn't recognize my HP PSC

---

