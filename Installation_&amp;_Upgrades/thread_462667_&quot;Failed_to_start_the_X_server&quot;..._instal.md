---
title: "&quot;Failed to start the X server&quot;... installation problem"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by ildopato on 2007-06-02
I'm trying to install the 7.04 version of Ubuntu, but the message "Failed to start the X server" appears. In the detailed info I can see "VESA(0): No matching nodes" and "Screen(s) found, but none have a usable configuration." as relevant messages. Ppl told me I'm having troubles with my graphics card, an ATI Mobility Radeon X1700. I'm trying to install it on two partitions (an ext3 and a swap one, both secondary on an extended one), and my PC is a notebook, and precisely an ASUS G2PC.
After that a shell appears, from which I, with my capabilities with Linux, won't solve anything...
Ask me more info if that wasn't enough. I'm a newbie though.
I'll be waiting for your responses...
Thanks!!!

---

### Post by taurus on 2007-06-02
Try the Feisty alternate CD.

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/feisty/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/feisty/)

---

### Post by ildopato on 2007-06-04
Thanks for the tip... I've downloaded the Alternate version, and tried to install it... but that gets stuck during the installation process, and exactly when it's at 75%, configuring "wvdial". I've found it being due to IRQ issues... :(
I've also tried to install from the normal CD, hitting F6 and adding to the command line "vga=789" (someone told me), but it fails anyway, and for the same problem (unable to start the X server)...
Any idea? I'm getting mad, two tries out of two failed... :(

Thanks!!!

---

### Post by SpeedRazor on 2007-06-21
I had this same problem with an Asus F3JP with x1700 mobility.

The only way I got it to install was to first install Ubuntu 6.06 LTS, upgrade to 6.10 using the instructions here:

[http://www.ubuntu.com/GetUbuntu/releasenotes/610](http://www.ubuntu.com/GetUbuntu/releasenotes/610)

And then finally upgrading to 7.04 using the instructions here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

It's a process but it seems to work.

---

