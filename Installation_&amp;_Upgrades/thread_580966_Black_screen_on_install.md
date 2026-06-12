---
title: "Black screen on install"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by ElbertF on 2007-10-19
I decided to try Linux for the first time and downloaded Ubuntu. I burned the CD at low speed, restarted my computer and tried to boot from the CD.

I am prompted with the Ubuntu logo and several options, choose install (or another option), see a progress bar and then everything just stops. The CD stops spinning, no disk activity, just a black screen with a blinking cursor.

[INDENT]Asus A6 (WinXP Home)
Inter Celeron M CPU
1.87 GHz
1.5 GB Ram
ATI RADEAON XPRESS 200M Series[/INDENT]

[http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-desktop-i386.iso)

I checked the MD5 checksum after I burned the CD. I tried Kubuntu as well, same result.. It says "Uncompressing Linux.. Ok, booting the kernel." and then it just stops. I also tried the alternate CD. Pressing Alt+F4 shows nothing.

I am a newbie, so any help would be appreciated. It seems Linux just won't run with my hardware configuration.

Thanks.

---

### Post by ElbertF on 2007-10-20
I was told that perhaps the framebuffer is failing, I removed the quiet option and added this: fb=false debian-installer/framebuffer=false. Now I get some output, but it still dies:

[IMG]http://img178.imageshack.us/img178/3564/bootfx9.gif[/IMG]

Any ideas? It's greek to me. :)

---

### Post by ElbertF on 2007-10-20
hpet=disable

That solved it.

---

