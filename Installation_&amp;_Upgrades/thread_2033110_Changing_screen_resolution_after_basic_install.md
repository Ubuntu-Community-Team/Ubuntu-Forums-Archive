---
title: "Changing screen resolution after basic install"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by MikeS999 on 2012-07-25
I wonder if anyone can help please?

I have a strange 'combination' PC which is basically a combined monitor and PC, like a 'laptop on a stand'. This is badged as a  Vulcan 4021 for John Lewis and also has a manufacturer's code LP200SC.

It has a 1GHz processor with 256 Mb of RAM, plus a 1024 x 768 LCD screen & the display adaptor is an SIS630.

Any attempt to run Xubuntu 9 either via a LiveCD or install using the default options resulted in the screen not being identified and a poorly timed partial desktop appearing in a 2" stripe down the LHS.

However using the second on-screen option for a basic installation, all went well.

So my question: Is there a way I can edit anything to permit the display to be changed from 800 x 600 to 1024 x 768? Currently the only screen option is a single 800 x 600.

If it helps, I have tried a variety of smaller Linux installations and with the exception of DSL, they all come up with a warning about the SIS630,

"SIS630 comp. bus not detected, module not inserted.".

Can anyone please advise? Many thanks for reading this!

---

### Post by dino99 on 2012-07-25
well googling around SIS chipset with linux, let you know about some issues. That said:

- the driver you need: xserver-xorg-video-sis
- the distro you need: something light like Lubuntu or puppy (as you dont have much ram)
- forget about 3D (compiz/unity)
- not sure about the best kernel to use: maybe one from Hardy
- inside xorg.conf : set sis instead of vga

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)

---

### Post by MikeS999 on 2012-08-02
No luck, I'm afraid.

The Package Manager confirmed that the drivers 'xserver-xorg-video-sis' were already installed.

Modifying xorg.conf from 'vesa' to 'sis' resulted in a return to the same old problem of a 2" wide strip on the LHS of the screen. Correct resolution, but fuzzy, flickering and shooting off the LHS of the display!

Does this mean we are stuck with a dreadful 800 x 600 display on a 1024 screen because of hardware limitations?

What is strange is that DSL doesn't have a problem - and is the only one that works. I don't really want to use that because the PC is intended for a female and Xubuntu has a very nice visual. DSL is wonderfully functional but pretty it aint!


I take your point re small memory, but for just browsing and occasional email, speed seems very acceptable - better than XP!

---

