---
title: "Blank Screen After Install -No Options"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by NoSkill on 2007-04-27
Hi,

          After I install Ubuntu 7.04, from the CD and reboot I get a pure blank with just the underscore line flashing. No options no nothing, just the cursor flashing. The install went fine, I installed it on a sata drive, and am not using dual booting.

Anyone know what's up? I am sure I'm booting from the right device.

Regards

---

### Post by zvacet on 2007-04-28
**ctrl+alt+F1**


[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by NoSkill on 2007-04-28
thing is i cant even see the command line. i see nothing but that cursor. I cant type and that key combo does nothing.

---

### Post by Mrs Harris on 2007-04-28
I'm seeing the same thing with a Sony Vaio desktop which has 2 SATA drives.  I think the problem maybe that the drives are in a RAID config on the motherboard and there's no option to turn that off.

---

### Post by NoSkill on 2007-04-28
well i have a p5b deluxe motherboard, is that my problem ? i have heard of alot of incompatibility issues with this board? would that be the case here?


any fixes?

---

### Post by Loki-uk on 2007-04-28
When your PC starts to boot (and you get some text on screen) keep pressing esc and you should get a boot menu choose safe recovery and then it should boot to a console. Use 'sudo dpkg-reconfigure xserver-xorg' without the quotes at the prompt to reset the xserver and reboot.

This is some infor on resetting the xserver - [http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm](http://www.aotk50.dsl.pipex.com/install-ubuntu-704-x1/install-ubuntu-704-x1.htm)

Loki

---

### Post by Loki-uk on 2007-04-28
I have the P5B and it works flawlessly.

Loki

---

