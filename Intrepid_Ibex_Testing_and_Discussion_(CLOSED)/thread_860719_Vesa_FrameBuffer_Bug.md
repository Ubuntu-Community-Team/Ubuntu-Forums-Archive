---
title: "Vesa FrameBuffer Bug"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-07-15
The vesa framebuffer bug has been hanging around since Alpa 1 and hasnt been confirmed as of yet. I reported the bug, and mine was marked as what was an obscure duplicate at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

This is the bug that prevents setting a vga=XYZ code in bootup to get a high res TTY.

Can anyone with privileges please confirm.

---

### Post by stari4ek on 2008-07-16
You can't use "vga=xxx", cause this option is for vesafb, which is not in use anymore. It was replaced with uvesafb.
I've wrote some ideas about it here: [http://ubuntuforums.org/showpost.php?p=5396998&postcount=7](http://ubuntuforums.org/showpost.php?p=5396998&postcount=7)

---

### Post by Nullack on 2008-07-16
Trying video=uvesafb:1280x1024-32 in the boot line has no effect. :confused:

Pre kernel boot I get various unhappy error messages too

---

### Post by thor2002ro on 2008-07-16
i use "vga=0x0323" works just fine

---

### Post by Nullack on 2008-07-16
Is that the lame default resolution?

---

### Post by stari4ek on 2008-07-16
you can try with "vga=ask"
and try to select any of suggested modes.
but hi-res modes don't work. only text-based (which doesn't use vesa, vga only)

---

### Post by Nullack on 2008-07-17
Your "text based" can do 1600 in 24bit colour, I'd call that high res. It doesnt work anyway - weve been through the problem why vga= wont work.

---

### Post by stari4ek on 2008-07-17
i was talking exaclty about text mode, like 80x30, which is supported by VGA
you're talking about VESA modes, which isn't text. and "yes" "vga=" flag works with both.
If you don't see difference, it doesn't mean that there is no one.

---

### Post by Nullack on 2008-07-17
Has anyone got any insight into why "video=uvesafb:1280x1024-32" isnt working. I dont think the uvesafb is happy on boot.

---

### Post by Nullack on 2008-07-17
> **stari4ek said:**
> i was talking exaclty about text mode, like 80x30, which is supported by VGA
you're talking about VESA modes, which isn't text. and "yes" "vga=" flag works with both.
If you don't see difference, it doesn't mean that there is no one.

So are you now claiming that vga=(to a vesa res) works?

---

### Post by stari4ek on 2008-07-17
omfg.
once again.
"vga=" command can select from VGA and VESA modes. Now VGA works well, VESA (through vesafb) - not (no module=no work)

We have uvesafb, which should work in pair with v86d.

Read it: /usr/share/doc/v86d/README.Debian
> First remove any "vga=X" options from your kernel.
Then, if you have uvesafb built as a module, modprobe it like this:
modprobe uvesafb mode=YOURMODE
where YOURMODE is something like 1400x1050 or 1400x1050-16 (or any mode 
you want to use).

---

### Post by Nullack on 2008-07-17
Thanks for the reply - try to stay calm.

/usr/share/doc/v86d/ doesnt exist on my up to date Intrepid install and synaptic reports it as not installed. Ill fiddle with installing and configuring it - does beg the question why its not setup in a default install.

EDIT: Having installed v86d is not working, Ive added comments to:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/189621](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/189621)

---

