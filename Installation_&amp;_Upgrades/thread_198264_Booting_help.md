---
title: "Booting help"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by pmpddytim on 2006-06-16
(Ubuntu 5.10) I want to reconfigure GRUB, so windows is first on the list. How do I do this? I've tried going to the command line and typing "sudo nano /boot/grub/menu.lst" but it says unknown command or some such thing.

Also I have Ubunutu installed on a External hardrive and Grub won't come up (it gives an error) unless I have that hard drive plugged in why is that? 

-Tim

---

### Post by mfaheypride on 2006-06-16
as far as the grub boot goes, i believe you must have the external drive plugged in because that is where the actual Grub is located therefore you need it. However I am not sure and I am new to linux, but that makes sense. as far as your other problem I am not sure.

---

### Post by x64Jimbo on 2006-06-16
If it says no such command when you type nano, it probably means that you don't have that program installed. You can apt-get install nano if you wish, or you could use vi. both are great command line ascii editors. Next, once you actually get in to edit the menu.lst file, you'll find a value that says "default=x" where x is the number of the entry that GRUB will choose first. Remember, the first option is 0, the second is 1, the third is 2, and so forth.
Re: the external drive: I'd need to see the error that you're getting to know exactly what's going on. can you post it?

---

