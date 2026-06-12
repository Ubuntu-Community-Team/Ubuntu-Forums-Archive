---
title: "Installation Exits to BusyBox"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by CharmCityCrab on 2008-05-05
When I boot the installation CD, the xubuntu screen with language selection loads, I select english and then go to install CD.  I get the xubuntu logo in blue and a bar moving back and forth.  Then it immediately goes to something called BusyBox v1.1.3 and a command line that begins (initramfs) and the a blinking underscore.

Two questions:

1. Why is this happening?

2. What do I do to install at this point?

---

### Post by CharmCityCrab on 2008-05-05
After hitting install and before the screen with the word Ubuntu in blue comes up, I get the message that "Resource is not an IRQ entry", though I'm not entirely sure what it means.

---

### Post by CharmCityCrab on 2008-05-05
If it helps, it's a very old Compaq Presario laptop.

---

### Post by CharmCityCrab on 2008-05-05
1500t P4...

---

### Post by CharmCityCrab on 2008-05-05
Anyone?

---

### Post by chas3 on 2008-05-05
I am having this trouble of going to a busybox command prompt when trying to load ubuntu 8.04 (desktop i386 iso) as live or as an install.  Kubuntu 8.04 (both 8.04 dvd and cd kde4 versions) will boot up as live just fine.

I tried adding the all_generic_ide floppy=off irqpoll to the end of the F6 boot string with same results.

I downloaded a second copy of the ubuntu cd iso and same thing.  What is interesting, if I try to look at the ubuntu CDs from Windows XP, nothing shows on the CD.  But, looking at the kubuntu CD, WinXP can see a bunch of files.  Could this be a clue to the problem?

---

### Post by chas3 on 2008-05-05
I found my trouble....bad CD burn.
Apparently, the cheap (free on rebate) CD's I got 5 years ago don't want to burn properly in my new laptop at an 8x speed even though the generic CD's are rated at 40x.  I burned the same generic CD using my old win98 machine at 4x and now the ubuntu can be seen on the Cd.
:)

---

### Post by urrybr on 2008-05-05
I have been having this problem with 7.10, as well.  My Ubuntu server crashed, and I cannot get either 7.10 or 8.04 to do more than boot to the initramfs prompt.

---

### Post by CharmCityCrab on 2008-05-05
I did a second download and then made an image of it on a second CD.  Same result -- i.e. IRQ error.

I also tried running both CDs as live CDs on my newer machine -- there I didn't get an IRQ, but I did get a blinking caps lock key and a frozen arrow a light blue screen (with no desktop, words, or icons).

---

