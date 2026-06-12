---
title: "Reboot in other partition"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Dsky on 2007-01-28
Hi at all... i want to apologize for my english :KS 

My question is if it's possible (as suse) to reboot ubuntu so that at the boot it starts automatically the other partition

thanks...

---

### Post by Dsky on 2007-01-28
up

---

### Post by Dsky on 2007-01-29
please...

---

### Post by housam on 2007-01-29
You mean that you want to boot both suse and ubuntu at the same time from a different partitions?

---

### Post by Dsky on 2007-01-29
no... i've 2 partitions... windows and linux ubuntu... 

when i'm in ubuntu it is possible to reboot automatically in windows?

because i can't control the boot cause i control the pc in remote...

do you understand?

---

### Post by housam on 2007-01-29
You can do it if you changed the boot sequence from the grub/menu.lst and allaw windows to be the first boot insted of ubuntu. [Read this thread]("http://www.ubuntuforums.org/showthread.php?t=304074&highlight=boot+sequence")

---

### Post by Dsky on 2007-01-30
i don't want to change the default partition on boot... but only on reboot...

can you understand me?

i tried to write   grub-reboot 6  (6 is the position of windows in the menu.lst) then i reboot.. but it starts always the first as default...

edit: i read on google... that is a bug...

someone knows how to make it work?

i don't understand if this link can help me

[http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=254475](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=254475)

---

### Post by Dsky on 2007-01-31
i changed  

> default 0 
in
> default saved

now it works :D

---

