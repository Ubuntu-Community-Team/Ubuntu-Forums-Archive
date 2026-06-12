---
title: "Grub in the floopy, HOW???"
date: 2004-12-18
forum: Installation &amp; Upgrades
---

### Post by fuchetj on 2004-12-18
HI
I'm currently trying to install teh 64 bits version. It install without problems, until it comes to install teh grub loader. I have two O.S. installed already, adn I install ubuntu in a partiton on the second HD (i got two).
I want to install the boot loader in a floppy, but I enter "/dev/fd0" in the line provided and it gives me a fatal error  ](*,) 

HOw can I install the the loader onto the floppy???

If I continue the instalation without intalling the loader, it finishes it fine and tell me to enter root=/dev/sdb8 to boot manually, however, I don't know how to do it.

Thanks for your help.

Fuche

---

### Post by kirsche on 2004-12-20
Have a look at this:

[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy](http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy)

Maybe it helps...

---

### Post by fuchetj on 2004-12-20
[QUOTE=kirsche]Have a look at this:

[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy](http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy)

Maybe it helps...[/QUOTE]


Thanks, but I just find out how to do it.
I do not know if was a problem or not, but I explain what I've done.

In the installation menu, I opened a shell and navigated to /target/boot/grub
There I edited the devices.map file (nano devices.map) and add a new line at the end --       (fd0)      /dev/fd0
Save and exit, and in the line for grub installation path I enter /dev/fd0 and thst's it, it worked.

However I got problems with the modem now...... But it is another histoy  8-) 

Fuche

---

