---
title: "lilo is not available"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by paco_espinola on 2011-03-09
This computer is incompatible with grub.

So normally with other linux distros when the installation ask me about grub I click back and the distros give me the lilo option.

But ubuntu-10.04.2-alternate-i386.iso does not give the lilo options. 

I try apt-get install lilo but no success. (shell rescue mode)
the answer is:
Package lilo is no available


So I need a Ubuntu with lilo.
or some way to install lilo in this distro.

Thank you in advance for any clue

---

### Post by oldos2er on 2011-03-09
Try ```
sudo apt-get update && sudo apt-get install lilo
```

What exactly do you mean by saying your computer is incompatible with grub?

---

### Post by oldfred on 2011-03-09
You also have to enable universe as a source of code.

---

### Post by paco_espinola on 2011-03-09
No compatible means that some olders computers are no compatible with grub.
No start does no matter if I reinstall the grub or try other things

But works with lilo.

I try:

sudo apt-get update && sudo apt-get install lilo 
But the command is looking for internet.
Of course internet is no available because I cannot start the computer to install internet.

I need some way to save the lilo in stick usb or cd to install in the computer

---

### Post by Frogs Hair on 2011-03-09
This is the same package I find in 10.10 synaptic package  manager , but the page says it is for 9.10 .
[http://packages.ubuntu.com/karmic/i386/lilo/download](http://packages.ubuntu.com/karmic/i386/lilo/download)

---

### Post by paco_espinola on 2011-03-10
ok I already has lilo22.8-8ubuntul_i386.deb in a stick memory

Is there some instruction to install using the shell?

---

### Post by paco_espinola on 2011-03-10
I try to use 

dpkg -i *.deb

but fail because dependence with mbr

I am looking for some rescue disk lilo.

---

### Post by paco_espinola on 2011-03-22
Finally I solved using the dvd.
I install like text (graphic does not give lilo option)
and when ubuntu ask for install grub I click back and give me the lilo option.

---

