---
title: "Feisty/2.6.20.3 recompile/no framebuffer console text"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by Malibyte on 2007-06-01
I have Feisty x86-64 installed on an Athlon-64x2 system with twin nVidia 7600 GT video cards (SLi). This was done via dist-upgrades from Dapper LTS -> Edgy -> Feisty.

The stock 2.6.20-16-generic kernel boots fine; no problems; the framebuffer seems to work - the boot parameter "vga=794" works, no sweat (though I can't get a CLI console login prompt by hitting ctrl-alt-Fx - just a blinking cursor) - I need to figure out what's up here).

However, there are a few little tweaks I want to make, so I installed the kernel source package, changed the few options I needed, then recompiled.

On reboot, I get no framebuffer console text unless I remove the "vga=xxx" line in the bootloader (after which, I only get the huge 80x25 characters).

I went back in and changed .config, compiling the nVidia framebuffer support into the kernel, rather than as a module. No better.

Interestingly, I had a similar problem on another system running Mandrake, when I tried to compile a vanilla 2.6.20 kernel...that box has an nVidia video card also.

So it appears that there is a certain setting that has to be tweaked just right to have the framebuffer work with nVidia cards...???

I have seen some references to this via Google, but haven't found a fix yet. Anyone else on this forum seen this? If so, could you give me a clue as to what I need to set to get this fixed?

Also, I want to use the nVidia binaries, rather than the stock "nv" driver. I have installed the Ubuntu-specific packages (through Synaptic), but changing the driver name to "nvidia" in xorg.conf doesn't work.  Since I can't get a CLI console, I can't kill X to try and install the binaries from the nVidia web site.

Any help would be appreciated - thanks.
Bob

---

### Post by Malibyte on 2007-06-02
bump...?

---

