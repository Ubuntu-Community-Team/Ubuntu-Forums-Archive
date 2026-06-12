---
title: "new to linux dont know how to install driver"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by on4now4 on 2008-02-25
i have found the driver that i need to install to make my sound card work but it was not in the synaptic package manger or any other part built into ubuntu.
here is the driver how do i install it

---

### Post by DieB on 2008-02-25
looks like you have to compile it.
 so first unpack it, then open a terminal move via cd [dir] into the newly created dkk...-folder. inside u execute still in the terminal:

> make && sudo make install

that should work, if not try:

> ./configure && make && sudo make install

hope it helps.

---

### Post by lank23 on 2008-02-25
what system you running?  driver looks like it is for Solaris to run with OSS

might want to google "compile ddksample" and read the first link.

---

### Post by on4now4 on 2008-02-25
my sound card is a HT omega claro 
i also have a asus a8n5x mobo
4gb ddr ram
1.3 tb segate hd
socket 939 3400+

as i said i am new to linux and i don't entirely know what you are telling me to do here "then open a terminal move via cd [dir] into the newly created dkk...-folder. inside u execute still in the terminal:"
if u can simplify this any more that would be greatly appreciated

---

