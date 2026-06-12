---
title: "Mythbuntu won't load on my new Mobo"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by bmwman on 2008-08-22
Mythbuntu won't load on my new Mobo!

I finally got all the parts for my new HTPC and of coarse I am so excited. I put it all together real quick. Then I tried to load Mythbuntu but it hangs 20 sec after I start it. I tried Live environment or Install - same thing. It gets to a shell and it just says BusyBox v1.1.3 Built in Shell(ash) then on next line it says "(initramfs)_" and a blinking cursor! I also tried Ubuntu 8.04 and 8.04.1 disk as wel - same result.

What do I need to do to make it load? Is the problem with the Ram since it fails at initramfs? I know the system works because i booted from Vista disk and works fine.

Here're the specs GIGABYTE GA-EG43M-S2H LGA 775 Intel G43 HDMI Micro ATX Intel Motherboard -,
Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory .

PLS HELP!

P.S. AFter loading XP and ubdating the BIOS, the system totally died. I sent the board back to Newegg and I'm getting the new one today. Then I read this review on Newegg:
..................................................................
    Reviewed By: amcnabb on 8/19/2008
    Rating + 5Rating + 5Rating + 5Rating + 5Rating + 5 
    Tech Level: high - Ownership: 1 day to 1 week
    This user purchased this item from Newegg

    Pros: This board works well in Linux, considering how new the board is. However, you can make everything work with a little bit of work.

    There are lots of great connectors, most notably DVI, which can be used to do dual-head with the VGA port. You can also get a cheap SDVO card to add other graphics ports (to support two DVI monitors simultaneously, for example).

    The G43 is supported by Intel, and you don't need any binary drivers! If you aren't a gamer, I would highly recommend getting one of these instead of some motherboard where you would have to get a separate graphics card. Intel has much better support for 2D graphics (dual-head, on the fly resizing and rotation, kernel modesetting, etc.) than any other manufacturer, and the 3D support is more than good enough for me.
    Cons: It's definitely bleeding edge. Some things aren't supported out of the box in Linux. The G43 graphics card is only supported with the 2.4.0 version of the Intel driver, which isn't yet in most Linux distributions. The network driver has a bug and doesn't work well with the 2.6.25 driver, although apparently people are working on fixing the problem. For now I'm just using a PCI card. When Fedora 10 comes out, this shouldn't be a problem.

    I noticed in the manual that the memory slows down to DDR2 667 if there are four modules, but it goes at DDR2 800 if there are only two modules. Weird.
    Other Thoughts: In Fedora 9, I had to do the following to get the graphics supported:

    yum --enablerepo=rawhide kernel xorg-x11-server-Xorg xorg-x11-drv-i810 libdrm

    (I might have installed a few more packages in addition to these). I then set 'Driver "intel"' in xorg.conf. It's a new board, so this is completely understandable. 
.................................................................

Is there a known issue with making this work and what should I do If i get the same error when I get my replacement board today?

Thanks

---

### Post by LowSky on 2008-08-22
you have a hardware issue, a really simple one.

change the cable that connects the CDROM to the motherboard.
USe a 80 Pin cable (smooth IDE ribbon cable), not a 40 pin cable (rough ribbon cable).

---

### Post by bmwman on 2008-08-22
> **LowSky said:**
> you have a hardware issue, a really simple one.

change the cable that connects the CDROM to the motherboard.
USe a 80 Pin cable (smooth IDE ribbon cable), not a 40 pin cable (rough ribbon cable).

The CD drive is SATA. I have another one thats IDE if you think that's gonna make it work?

---

### Post by bmwman on 2008-08-22
I got my replacemet motherboard and still can't load Ubuntu. The 8.04 and 8.04.1 disk comes to a command shell and nothing else. 8.10 seems to load fine but the it goes to a black screen and that's it.

Any help is highly apreciated.

---

