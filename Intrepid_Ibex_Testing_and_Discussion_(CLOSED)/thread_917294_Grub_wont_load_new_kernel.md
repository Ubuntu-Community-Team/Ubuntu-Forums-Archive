---
title: "Grub wont load new kernel"
date: 2008-09-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-09-11
I am experiencing problems with grub, I removed 2.6.27-1 kernel but it didn't remove the grub entry! Today I installed 2.6.27-3 kernel (checked in synaptic to be sure properly installed & uninstalled .1) & all is fine. What do I have to do to refresh grub to reflect the changes? 

Also all of my kernels since upgrade to Intrepid bork after the kernel loads & I get constant beeps (like the one you get when you put the wrong ram in your PC) but if I boot in recovery mode & select continue it works fine. Today I removed the quiet entry & rebooted fine, so it seems to be splash (only works occasionally)

I wonder if these are related or if the 2nd is a NVidia issue:confused:


Cary

---

### Post by Slug71 on 2008-09-11
My kernel isnt loading either. Doesnt even appear in the menu yet it is installed. If i enter "uname -r" into terminal it says 2.6.27-2.

---

### Post by ronacc on 2008-09-11
you can always hand edit your /boot/grub/menu.lst , wherever it says 2.6.27-2 just change the -2 to -3  or if you want to keep your -2 as a backup copy and paste it below the stanza you are going to change .

---

### Post by Slug71 on 2008-09-11
That did it for me.

---

### Post by DougieFresh4U on 2008-09-11
I ran the update. I guess I won't be rebooting until another day :)

---

### Post by cariboo on 2008-09-11
Depending on what you tell the post-inst script to do you should be able to boot from the kernel after installation. I pick "use the maintainers configuration", but because grub doesn't detect my drives properly I have to go in and manually edit /boot/grub/menu.lst, to tell it on which drive to look at for menu.lst.

Actually grub does list my drives correctly, its just that the menu.lst that I use in on /dev/sdb1 and grub wants it to be on /dev/sda1. My first drive has 1 patiton for vista and 3 for hardy, the second drive just has 2 partitions for intrepid.

---

