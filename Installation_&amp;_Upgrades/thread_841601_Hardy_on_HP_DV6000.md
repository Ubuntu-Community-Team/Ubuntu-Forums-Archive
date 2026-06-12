---
title: "Hardy on HP DV6000"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by JohnnyTricksta on 2008-06-26
Hi there,

I'm trying to install Hardy on my HP DV6000. I've been using the live cd, but whenever I try to install this  or boot into live mode it stops at the splash screen (the one with the orange scrolling bar going left and right right after the grub menu). I've tried adding noapic irqpoll noirqdebug to the end of the boot parameters. I've tried adding it before and after the tailing "--" at the end of the default parameters. It still keeps getting stuck. Also, I've tried adding the "break=top" but it still keeps getting stuck at the splash screen. Any ideas?

Thanks!
Jt

---

### Post by niyonk on 2008-06-26
same happens to me
Have you tried pressing F4 and choosing safe graphics mode.

Thats the only option that worked for me :(

---

### Post by Midwest-Linux on 2008-06-26
Also try the alternate install CD.

---

### Post by JohnnyTricksta on 2008-06-26
I found out two new things:

1) When I ran Ubuntu's cd check it found one error. I burned it another time at 1x speed and it still said one file error. However, I downloaded it straight from Ubuntu's website, how could it have an error?

2) I just now noticed that after I choose the install option, but before the splash screen, it shows me this error: "PCI: bios bug #81[00000000] found"

Jt

---

### Post by niyonk on 2008-06-26
try burning it at a speed a little bit lower than the fastest.
I think burning at very low speeds isn't  recommended :)

Edit:totally wrong thread:confused:

---

### Post by JohnnyTricksta on 2008-06-27
I downloaded Ubuntu from another mirror than I originally downloaded from. Works like a charm after I added noapic irqpoll noirqdebug to the boot parameters. I got it installed and everything :)

---

