---
title: "How do I add a second Linux installation to my current Ubuntu install to dual boot?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by cantormath on 2007-03-10
I have installed a second Linux installation to my only hardrive on a second partition(hda3).  The filesystem is completely installed and now I would like to add it to grub so that i can dual boot into it.  Does anyone know how to do this?

---

### Post by Herman on 2007-03-10
Hello cantormath,
I would advise making yourself an 'configfile' boot entry at the bottom of your menu.lst file.
You will just need to find out the filepath and filename of your other Linux's grub.conf or menu.lst file. eg: (hd0,2)/boot/grub/menu.lst

An example of a configfile command for the bottom of your /boot/grub/menu.lst would look something like this, 
```
 # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Name Of Other Linux OS Goes Here, configfile (on /dev/hda3)
configfile     (hd0,2)/boot/grub/menu.lst
```If you want to see my new fiesty menu.lst, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst"), at the bottom of that you'll find more examples of configfile boot commands in use.

The configfile commands don't boot the other Linux's kernel, instead they present the other Linux's own grub menu for you. Then you boot your other Linux from its own menu. The advantage of that method is when the other Linux has a kernel update, you don't need to go manually editing your menu.lst file like you would with direct kernel boot entries. The other Linux install will keep it's own menu up to date automagically if it's another debian based operating system. 
I'm not sure about non-debian operating systems, maybe they have some other way of keeping their boot menus up to date.

I also like to add another configfile entry on the other system's boot menu to take me back to my Ubuntu grub menu, just for fun.

Another tip is to install a different [splashimage]("http://users.bigpond.net.au/hermanzone/p15.htm#splash") to each grub menu, that makes dual or multiple booting more than one Linux OS even more pleasant.
 
Regards, Herman. :)

---

### Post by cantormath on 2007-03-13
Thank you, that really helped........

---

### Post by Herman on 2007-03-14
Okay cantormath, good, and thanks for the feedback. The configfile command is probably the most interesting grub command, and with a little imagination it's possible to have a lot of fun with it.
Regards, Herman :)

---

