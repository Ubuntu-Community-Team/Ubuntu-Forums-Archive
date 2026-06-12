---
title: "Laptops"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by akshay2000 on 2010-06-21
Hi.
I am currently using the Ubuntu 10.04 LTS on my desktop computer. It works fine. But, when I tried the Ubuntu desktop Live CD on one of the Compaq wide screen laptops, there were horizontal strips on the display. The display was in the form of strips. Also, a vertical strip, which should be on the right side (the one containing power button) was appearing on the left side and the whole screen image was shifted rightwards. When I moved the mouse pointer out of screen from right side, it appeared from left side.
What's wrong? Am I  supposed to use the Netbook version?

---

### Post by dino99 on 2010-06-21
that mean a chipset is not well recognized and give video issue: try to boot with [COLOR="Blue"]nomodeset or/and acpi=off, irqpoll, lapic=off, apic=off[/COLOR] or video=vesa

---

### Post by akshay2000 on 2010-06-22
> **dino99 said:**
> that mean a chipset is not well recognized and give video issue: try to boot with [COLOR=Blue]nomodeset or/and acpi=off, irqpoll, lapic=off, apic=off[/COLOR] or video=vesa
Its a bit foolish, but what do you mean by that? Where do I enter those things. Only thing I know is go to BIOS and command it to boot from CD. Will you write detailed steps? Thanks in advance.
One more thing, am I right in using Desktop version with laptops? If yes, then what is NetBook version meant for?

---

### Post by Rubi1200 on 2010-06-22
What type of graphics card do you have on the laptops?
Intel ATI Nvidia?

Depending on your answer, I may have a solution for you.

On another note:

[http://en.wikipedia.org/wiki/Netbook](http://en.wikipedia.org/wiki/Netbook)

[http://en.wikipedia.org/wiki/Notebook_computer#Notebook](http://en.wikipedia.org/wiki/Notebook_computer#Notebook)

> One more thing, am I right in using Desktop version with laptops?

Answer=yes

---

### Post by lisati on 2010-06-22
akshay2000: please use the default font for your posts, and save the larger size for highlighting something.

---

### Post by akshay2000 on 2010-06-23
> **Rubi1200 said:**
> What type of graphics card do you have on the laptops?
Intel ATI Nvidia?
[FONT=Arial]I have Nvidia and a [/FONT]wide screen.

---

### Post by Rubi1200 on 2010-06-23
Ok, so you could try this:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04

---

