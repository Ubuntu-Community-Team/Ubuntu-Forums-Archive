---
title: "Ubuntu Server 22.04 LTS blackscreen on installation"
date: 2022-06-19
forum: Installation &amp; Upgrades
---

### Post by cakestory on 2022-06-19
Hello,
we´re trying to install Ubuntu Server 22.04 LTS on our old server hardware.
For now I can tell this about the hardware (I´ll try to find the exact specs, if required, but accessing the hardware is not that easy):
- SuperMicro Server Motherboard
- Intel Xeon E5-2640

The installation from USB Stick will start normally. After pressing Enter for "Try/Install Ubuntu..." the console outputs a bunch of lines (as usual) and then the screen goes black and has no signal anymore.
We tested with different sticks and checked images, no difference.
A test with Debian installs fine however.
We also tried installing on an even older server hardware (unknown specs) and the installation instead of giving a black screen got to the point of printing lines and then froze.

Is the hardware too old and not supported anymore? Do we need a special version with some different packages?

Greetings

Cakestory

---

### Post by MAFoElffen on 2022-06-22
I have a SuperMicro server board in my main workstation. I do Development Version testing on that machine, so I have both 20.04 and 22.04 on that (natively on metal)).

The onboard graphics GPU on mine is Matrox Systems MGA G200eW. Yes, my SuperMicro motherboard is about 12 years old. My main graphics is NVidia. Not sure what the onboard GPU is on your model of board, as you did not provide. 

The boot parameter I add to my Grub boot line for a graphics helper is
```

video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank

```
This helps with setting the helper in KMS, in the kernel. This will help with Console vtty's, and further, through the Linux Graphics Layer, if used. You can tweak the resolution to whatever is a match for your system... On console, I further tweak to my own color palette... If I have to change the resolution on the fly, I use 'fbset'.

You can add that to the 'linux' boot line of the Grub Menu (edit)... Temporarily... Until added as persistent to /etc/default/grub.
```

# Just changed & added lines...
GRUB_CMDLINE_LINUX_DEFAULT="video=uvesafb:1920x1080-32@60,mtrr:3,ywrap,noblank"
GRUB_GFXMODE=1920x1080x32 
GRUB_GFXPAYLOAD_LINUX=keep

```
If that doesn't work, then boot an Ubuntu Desktop LiveCD and if you select "Try", does it boot to a desktop? If not, then on boot, edit it's Grub Menu kernel boot line to include a framebuffer helper like above...

I have to do the same thing on my rack servers that connect via KVM switches to my (TFT) rack console.. Because it is only 1024x768 resolution, and I don't think that my servers see the EDD data of that rack console through my KVM switches. 

What would really help, is if you can boot a LiveCD successfully, is to run the UbuntuForums 'system-info' script in my signature line. That will tell us the model of the board, the other hardware present, and what I am recommending a solution for...

---

