---
title: "Dual Video Cards Dual Monitors?"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by amiga2000hd on 2007-03-12
I am currently running Windows XP using the 'extend my Windows desktop
onto this monitor' feature. To get this working I had to install a
second monitor card. Both my monitor cards are older (if that
matters).

At work I was shown Ubuntu OS via a cd boot on a single monitor setup
and really like it. I'm now trying to load the software at home on
different drive than my XP OS.

Now that I am home using the same CD I used to demo the software it
seems stalls out after the first part of the load. It has been
suggested to me that the reason may be do to the dual monitor setup I
have at home.

Can anyone give me any insight or suggestions.

---

### Post by kokiri on 2007-03-13
I also have a dual head setup, actually triple head setup if I was to use all the vga ports

My setup is a intel i845 onboard vga
and a dual head nvidia 5500 pci card

Try booting with only one video card in the computer, do an install and then install the second card, you shouldn't have a problem with it starting with both cards in the computer. Then you'll need to edit your xorg.conf to use both cards and configure xinerama which will do your dual head magic for you. You'll also need the bus id for both the video cards to configure them properly in the xorg.conf. 
You can find these by doing a
```
lspci | grep VGA
```
For me this is:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
01:09.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

```
the 00:02.0 and 01:09.0 are the bus id's just drop the first 0 for the xorg.conf, so then mine would be 0:02:0 and 1:9:0 respectively

The live cd's aren't good at handling multiple video cards but the installed system will be since it will have one configured it'll ignore the second card until it's configured properly.

I know it looks intimidating but it's not too hard, really.

---

