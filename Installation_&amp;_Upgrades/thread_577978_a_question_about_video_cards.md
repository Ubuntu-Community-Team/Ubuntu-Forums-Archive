---
title: "a question about video cards"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Ewzzy on 2007-10-16
Hi, I don't think this has been asked before.  I recently bought a new computer with Intel onboard video.  I put it my more powerful ATI card into the machine.  On Windows I use the ATI card and I want to use the Intel video under Ubuntu.  I have a monitor that can switch inputs so I'm not worried about having to use two physical video outs.
I wanted to know before I install Gutzy Gibbon if I could use the better supported but weaker Intel onboard video, or if I have to use the poor ATI drivers.

Thanks a bunch,
Ewzzy

---

### Post by Timothy Benton on 2007-10-16
I' not sure, but personally I'd just use the ATI card. It will still perform better than any Intel chip, bad drivers or not. Also, I think there are third party drivers for ATI cards.

---

### Post by magicfab on 2007-10-16
No need to install it to try it... simply use the LiveCD.

---

### Post by Timothy Benton on 2007-10-16
That won't give him great performance. I think he's just asking while he has the opportunity (as in he won't be able to ask for the next couple of hours because he'll be installing Ubuntu).

---

### Post by travm on 2007-10-16
dont waste your time with the intel graphics.  The ATI card will work, bar none.  worst case scenario you use the vesa driver for xorg,  ubuntu will detect which driver will work and it will use it.  The deal with the ATI cards is some of their older cards do not have drivers, But there is an open source driver that works quite well.  Sometimes it needs some configuring to get direct rendering working, but it is generally quite easy and with the help of google anyone can do it.  I am currently using 7.04 on my dell laptop with an "unsupported" radeon mobility 9000,  works like a charm, beryl is working, 3d effects look awesome.  havnt tried any games, but hey, the mobility 9000 is not fast enough for any games really worth playing.
cheers

---

### Post by Timothy Benton on 2007-10-16
I'm sorry, no one answered your question!

I'm assuming you can just unplug the ATI card before Ubuntu loads so it isn't detected. It'll then install the Intel driver. You should be able to put the ATI card back after the Intel chip is configured with Ubuntu.

---

### Post by travm on 2007-10-16
> **Timothy Benton said:**
> I'm sorry, no one answered your question!

I'm assuming you can just unplug the ATI card before Ubuntu loads so it isn't detected. It'll then install the Intel driver. You should be able to put the ATI card back after the Intel chip is configured with Ubuntu.
You should try liquid cooling it in a vat of milk while your at it.
removing your video card over and over again will cause glitches to rear their heads in your bios, windows registry, and possibly damage your motherboard (due to wear).  I have had boards stop working because of repeated reconfiguring (lan party business, often I would reconfigure a box for different reasons).

simply put, what you want to do will work.  install the correct driver, be carful when you set the port of your adapter, it will matter.  I have never tried it but linux generally doesnt get all conflicted about multiple devices like windows sometimes can.  Besides the point.  USE THE ATI CARD THAT IS ALREADY IN YOUR SYSTEM.

---

### Post by Timothy Benton on 2007-10-16
im just trying to help him. i know i hate when people dont directly answer my questions. anyway i dont think taking it out and putting it in one time will break it.

---

### Post by travm on 2007-10-16
no, but for that idea to work you would have to remove the ati card every time you switch from windows to ubuntu, then back again.

---

### Post by Timothy Benton on 2007-10-16
really? i meant to say he could just remove it when ubuntu detects hardware (once, right? during install?) and then put it back when ubuntu installed intel stuff. actually now that i think about it video cards arent installed automaticaally, so he could just download the intel graphics drivers using ubuntu and ignore the ati. drivers, not the os, detect the hardware (i think)

---

### Post by Ewzzy on 2007-10-16
Wow, thanks for my quick replies.  The only reason that I want to try this is because of how bad getting the FGLRX driver to work with Beryl was been. I've been trying every new Ubuntu release since Hoary, and although it has gotten better it isn't perfect yet.  Still, I'm looking forward to trying Gutsy.
-Ewzzy

---

### Post by travm on 2007-10-16
unless your video card is explicitly supported by ati i wouldnt use the fglrx driver, aiglx works for me, and it was quite easy to get working.

---

