---
title: "Bootloader"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by jan-90 on 2011-01-15
Hi,
i just installed windows pro and ubuntu and messed up in the booting so im reinstalling everything again.


Can i change the boot loader (with easy BCD maybe),
i need to set up windows as the default i would prefare to use the vista/win7 bootloader rather that the grub or grub 2 [ im not sure which one is installed with 10.10].
can this be done, where do i have to point the easy bcd to find the ubuntu booting option

i have 1 hdd with a 100mb reserved system 2 logical windows and extended linux partitions for swap, root and home

---

### Post by Quackers on 2011-01-15
Grub2 is used by default in 10.10.
Yes you can use EasyBCD to boot if you wish. There is an option in it to boot Linux systems.
You can also change grub so that Windows is the default boot option.
When you say you "messed up in the booting", what do you mean exactly?

---

### Post by jan-90 on 2011-01-15
when using easy bsd i deleted the wrong entry. but that was solved by a complete format
the strange thing now is that after updating ubuntu i have 2 ubuntu options in grub that seem to point as the same thing

---

### Post by dino99 on 2011-01-15
> **jan-90 said:**
> when using easy bsd i deleted the wrong entry. but that was solved by a complete format
the strange thing now is that after updating ubuntu i have 2 ubuntu options in grub that seem to point as the same thing

its normal: for every kernel installed a second line let you boot in recovery mode if the first one fail

---

### Post by jan-90 on 2011-01-15
1 ment 2 each, i have 2 normal and 2 recovery alternating and the windows,
i dont think it will be a problem, i found an tutorial on how to use easy bsd to setup the boot screen as i wanted if that does not work, im sticking to windows only

---

### Post by Pillars of Creation on 2011-01-15
jan-90,

“when using easy bsd i deleted the wrong entry. but that was solved by a complete format
the strange thing now is that after updating ubuntu i have 2 ubuntu options in grub that seem to point as the same thing”

It sounds like you reinstalled Ubuntu over its own partition. 

With Easy BCD boot loader when you add a Ubuntu option to the Easy BCD OS menu, when you select the Ubuntu OS option you then enter the GRUB-2 boot loader menu which belongs to Ubuntu. Because you installed Ubuntu twice you have two listings for Ubuntu.

If you wish you can edit the grub menu to set the startup time equal to zero. This way you won’t see the second menu and you will boot directly into Ubuntu

Applications, accessories, terminal. Then type sudo gedit. Click on file system, select ect, default, grub.

Change GRUB_TIMEOUT=10 TO GRUB_TIMEOUT=0

Back in terminal type “sudo update-grub” to update the GRUB-2 boot loader menu.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Pillars of Creation on 2011-01-15
[URL="http://neosmart.net/wiki/display/EBCD/Ubuntu"]Double Post
[/URL]

---

### Post by Quackers on 2011-01-15
> **jan-90 said:**
> 1 ment 2 each, i have 2 normal and 2 recovery alternating and the windows,
i dont think it will be a problem, i found an tutorial on how to use easy bsd to setup the boot screen as i wanted if that does not work, im sticking to windows only

Do the 2 entries have different kernel numbers?

---

### Post by jan-90 on 2011-01-15
yes the kernel numb are diff
one is 2.3.35-24
the other is  2.3.35-22

is that bad?
ps the extra pair showed up after the mass updates of ~200 updates

---

### Post by Quackers on 2011-01-15
No, it's just a newer kernel. When a new kernel is installed (via updates) you get a new entry (or two) in the grub menu. It's good to have a second kernel to boot in case of a failure.

---

### Post by jan-90 on 2011-01-15
a i see ok,
but how will i know which one is the newer on when using easy bcd?

---

### Post by jan-90 on 2011-01-15
> **Quackers said:**
> No, it's just a newer kernel. When a new kernel  is installed (via updates) you get a new entry (or two) in the grub  menu. It's good to have a second kernel to boot in case of a  failure.

a i see ok,
but how will i know which one is the newer on when using easy bcd?

---

### Post by jan-90 on 2011-01-15
> **Quackers said:**
> No, it's just a newer kernel. When a new kernel  is installed (via updates) you get a new entry (or two) in the grub  menu. It's good to have a second kernel to boot in case of a  failure.

a i see ok,
but how will i know which one is the newer on when using easy bcd?

---

### Post by jan-90 on 2011-01-15
> **Quackers said:**
> No, it's just a newer kernel. When a new kernel  is installed (via updates) you get a new entry (or two) in the grub  menu. It's good to have a second kernel to boot in case of a  failure.

a i see ok,
but how will i know which one is the newer on when using easy bcd?

---

### Post by Pillars of Creation on 2011-01-15
“Can i change the boot loader (with easy BCD maybe),
i need to set up windows as the default i would prefare to use the vista/win7 bootloader rather that the grub or grub 2”

To get the Easy BCD boot loader screen to come up first you need to perform the following procedure in Easy BCD. Then you can set whatever OS you desire to be the one that boots by default.

Under “boot loader setup” click on “right MBR”

Under “BCD backup repair” Select the radio button for “re-create/repair boot files”. Then click on perform action.

“but how will i know which one is the newer on when using easy bcd?”

When you select the Ubuntu option from the Easy BCD boot loader menu you will then boot into the GRUB-2 Ubuntu menu. The choice at the top will be the last Ubuntu you installed. They’ll also be the default boot and will boot automatically if you set time to equal zero.

The order of Linux installations is from most recently installed to oldest going from top to bottom.

---

### Post by jan-90 on 2011-01-16
thanks alot,
sorry for the triple post but i was getting a timeout message i have no idea they got through

---

