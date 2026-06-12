---
title: "Could not boot or install with live cd"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by capitanleniz on 2007-02-22
Hello. My name is José Solé. I'm a noob Linux user, trying to install Ubuntu Linux 6.10 in one of mi PCs (the older one) but I can't start the live cd OS. After I select the first option in the live cd splash menu (Start ubuntu), it starts to load, but then I get this error message (I will write the last lines on the screen) :

[32.265570] EIP: [<c0209fb1>] acpi_hw_low_level_read+0xa/0x7c SS:ESP 0068:cfa
51f34
[32.265675] <0> Kernel panic - not syncing: Attempted to kill init!
[32.265768]

And then, it stops there, and I have to restart my computer.

Mi computer specs are the following:
Pentium 4 2.800 mhz
80gb HD
512 mb RAM
Integrated sound card
ATI Radeon 9200 SE video card
Two PCI Network cards

I don't know what other specs are relevant. 
I have tried the noapic commands, I changed my RAM sticks, and tied some other stuff from the forums, with no result.

Also, the cd I use is good, since I hace tried it in my other computer, loading Ubuntu from the Live CD.

If ANYONE knows what else I could do, I'll be happy to try any advice. Also, if you need more info about specs or anything else, I'll be happy to give it.

Thanx in advance.

José Solé

---

### Post by Platinum89 on 2007-02-23
I couldn't get it to work here either. However, using the 5.10 Install CD did work. Keep in mind that you will need to change a line after the install to deal with the ATI Radeon issue. Hopefully this helps. (If this works, you can easily get the upgrades and updates via the update feature)

---

### Post by capitanleniz on 2007-02-23
Actually, I installed Ubuntu 6.01.1 from the live cd, and all went ok, and I'm using Ubuntu now. But I updated to 6.10, and it's working, but when I booted with the new kernel, I received the same error as before (with the 6.10 live cd), so I'm now using Ubuntu 6.10, with the 6.01.1 kernel. 

So, I think the issue here is that the kernel has some conflict with my hardware. Could this be because of my ATI video card (and if that is the issue, how can I solve it)? Because I think that now a problem with the RAM could be discarded.

I hope that someone has a solution to this problem. I seriously doubt that I'm the only one who has been through this before.

Thanks for the reply.

capitanleniz

---

### Post by mortis42 on 2007-02-23
I've had similar problems.
I can install and run the LiveCD versions of edubuntu 6.06.1 and ubuntu 5.04, but for any 6.10 version, I get the ubuntu logo and loading bar, but after the screen goes to multi-colored stripes like the display is not showing correctly.  The loading sounds play, so I was reletively sure it is an issue with the display.
I've tried the dvd, desktop, and alternate install cd's for 6.10 and they all do the same thing.

I was able to launch the desktop LiveCD using the "vga=771" switch for laptop users that was mentioned in the help on the CD, but my mouse pointer would not show. I was able to install still, but the same display error came up on reboot.

The odd part is, I was going to try to install envy from my usb stick, thinking it might be a nvidia problem, but when I went to ctrl+alt+F1, I had the same striping, but in black and white.

Specs for the rig in questions:
AMD Athlon XP 2600+
sda = Window drive, 500gig sata
hda = ubuntu drive, 80gig (root, /home, swap partitions)
Geforce 6600GT 128mb

If this is a related problem, then it is not an ATI-only issue.

---

### Post by capitanleniz on 2007-02-23
mortis42, I don't think it's the same problem, because the only error I have had is the one about the kernel panic - not syncing. Have you tried installing Drapper instead of Edgy?

---

### Post by mortis42 on 2007-02-23
> **capitanleniz said:**
> mortis42, I don't think it's the same problem, because the only error I have had is the one about the kernel panic - not syncing. Have you tried installing Drapper instead of Edgy?

I wasn't sure if it was related because I can't actually read anything on my screen when mine errors, but it seemed it might be around the same place during the load.

As far as your question to me (and I don't want to hijack your thread), every version besides the current 6.10 installs fine for me.  I haven't tried installing 6.06 and then upgrading yet.  I just wanted to see if there was someone with related trouble to mine.

---

### Post by capitanleniz on 2007-02-23
Well, if you can't find any solution to your problem, you can install 6.06.1 live cd, and then update it to 6.10. But you should note that if the problem lies with some kind of incompatibility between the 6.10 kernel and your hardware, you'll have to use the old kernel, from 6.01.1, like me.

---

