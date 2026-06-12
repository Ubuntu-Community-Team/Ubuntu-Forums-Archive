---
title: "damn dell dimension don't boot"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Xoctor on 2007-02-20
I just took delivery of a shiny new Dell Dimension 520. Its got a c2d processor, 2Gb RAM and a beautiful 2707WFP LCD. I couldn't talk them into not giving me Vista with it, so I thought I'd give it a go. The horror! It is the biggest leap backwards MS have taken since Windows ME. I could go on for pages, but this post isn't about that. This post is about trying to install Ubuntu as dual boot situation.

I want to leave Vista there, just in case I need some support from Dell, so my plan was to install Ubuntu, and leave a partition to install Windows XP as well, should I need something from the Dark Side.

So, not being a total noob, I used a handy live install CD to shrink the Vista partition to make room for Ubuntu. I didn't make any other changes. Then I grabbed my Ubuntu 6.10 Alt installation CD and ran through the text-mode install process. All seemed to work fine, until it came time to boot up. Grub came up, I selected the default option (Ubuntu), and let her rip. I got the 'Starting Up...', then the graphical 'Ubuntu' splash screen, but then it froze. My only options were to either Alt-F1 (which was fozen on 'Starting Up...') or Ctrl-Alt-Del to reboot.

Any ideas? Googling "dimension 520 ubuntu" doesn't bring up anything of value.

---

### Post by rlmiii on 2007-02-21
how many graphics processors are there on your dell? mine has an integrated intel chip on the motherboard and an aftermarket nvidia card: you?

---

### Post by aberry5555 on 2007-02-21
I'm pretty sure I know what this problem is, if you have an ATI card it's the graphics drivers. If that's so try the following solution:

Edit the grub line before boot and remover "quiet - splash" then insert "break=bottom" at the end of the line. Now, from there, boot up. the splash screen will not appear and it will start running through the boot, stopping about half way. from here type the following:

```
chroot /root nano /etc/X11/xorg.conf
```

This will open up your GUI configuration file (it contains the settings for things like your mouse, keyboard, monitor and graphics card.)

scroll down until you find a heading called "Device", below this should be a sub-heading called "Driver". Depending on the type of Graphics card it is (I'm thinking it's an ATI one) it will say which driver it is using in inverted commas like so:

```
Driver        "ATI"
```

Change the driver name (whether it be "ATI" or something else) to "vesa" (these are the most basic graphics drivers available to linux). Alternatively, although this is untested by me, you could try (if you're on ATI) using the "radeon" drivers as these are the open source drivers designed to work properly for most of their modern cards, if it doesn't work however just use the "vesa" drivers. Once you've done this press ctrl+O and ctrl+X, this will save and exit the text editor, bringing you back to the command line. Now type in "exit" at the command line and Ubuntu will continue to load with the VESA drivers and, hopefully, should boot!

If this has done the trick you may want to consider getting the fglrx drivers (graphics accelerated drivers) for your card, but if it's ATI DON'T use the ones in the synaptic repository as they are broken :S

Good luck!

---

### Post by Xoctor on 2007-02-21
Just the onboard "Integrated Intel® Graphics Media Accelerator 3000".

---

### Post by aberry5555 on 2007-02-21
ok, well you need to boot up in to recovery mode from the grub, then, and install the intel graphics drivers.

hopefully you have a dhcp net connection, that way you can just grab and install the package, firstly choose the console option in the grub, so it doesnt try and load in to the gui then, when it's loaded and you've logged in, type the following:

```
sudo apt-get install xserver-xorg-video-intel
```

then, once that's done do the following

```
sudo startx
```

hopefully that should open the gui, if it doesnt you could try reconfiguring the xorg.conf file with this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and then retry

```
sudo startx
```

if the drivers have installed properly that should bring up the gui interface, and if it does just restart straight away and load back in to normal Ubuntu

hopefully that works

---

### Post by Xoctor on 2007-02-21
Hey, thank you both for your help, but I couldn't even boot up the 'Recover' mode. It seems that when I shrank the Vista partition it FUBAR'd the entire partition table, to the point where the Ubuntu partitioner couldn't cope. I've wiped the whole HD now, and things are on the mend. The Xorg config info will no doubt come in handy.
Cheers!

---

### Post by aberry5555 on 2007-02-21
no problem, good luck!

---

### Post by Xoctor on 2007-02-21
Bummer!

Even though the G965 GMA X3000 has been 'Open Sourced' by Intel, it isn't fully supported under Linux.

Apparently it has the screen modes hard-wired into the BIOS, and they didn't see fit to hard-wire 1920x1200 which is what I need for my screen. There is a workaround for other Intel Chipsets, but it doesn't support the G965 at this point in time :-(

---

### Post by Xoctor on 2007-03-01
Turns out it was the damn disk drive. Dell sent me a new one, and Windows XP installed without a hitch, and now the machine has disk throughput that finally matches the processor's speed.

Very odd type of hardware failure - I've never seen a disk that worked perfectly, except for being very slow before. There were no bad sectors or issues raised by SMART. Just, fyi, the old disk was a Samsung 250GB and the new one is a Seagate 250GB.

---

