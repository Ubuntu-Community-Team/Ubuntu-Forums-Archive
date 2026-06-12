---
title: "Problem installing Linux on new PC"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Genesius on 2008-04-02
Been with Ubuntu since 2005, so I'm not a total n00b, but not a guru either.

Finally got rid of my old Athlon 2400+ with the 640MB of PC133, and got a new HP A6410t with a Pentium dual-core E2200, 2 GB of DDR2-800Mhz dual-channel SDRAM, and a Nvidia GeForce 8400. Came with Vista, which works fine, but I'd rather get rid of it & run 100% Linux.

So far, I've tried installing using LiveCDs for Ubuntu 7.04 32bit, 7.10 64bit, OpenGEU 7.10, and Elive 1.0. ON all the installs it's the same thing - the installer drops to a command line with an error about the X server. I've tried running sudo dpkg-reconfigure xserver-xorg. After I finish and run startx I get an error "fatal server error: no screens found". Tried Elive with the nv driver, old Nvidia driver, and new Nvidia driver, no change. All the hardware is detected & working fine in Vista, so I have to assume the hardware is fine.

Any suggestions?

---

### Post by housam on 2008-04-02
I think you have to install the Nvidia driver using this guide :[[COLOR="Red"]_http://www.psychocats.net/ubuntu/nvidia_[/COLOR]]("http://www.psychocats.net/ubuntu/nvidia")

---

### Post by Genesius on 2008-04-02
Things have changed a bit since my first post. I was finally able to get Ubuntu installed by using an alternate install CD & updating. However, I'm still unable to boot into a Live CD. It would be nice to have available in case I blow up my installation & need to get online to find out how to fix it.

---

### Post by dstew on 2008-04-02
When you boot a Live CD, press F6 and try the kernel parameters **vesa=force** or **vga=791**. One of these might get you a desktop. You can also try to boot in Safe Graphics Mode, which I think might be the same as vga=791.

---

