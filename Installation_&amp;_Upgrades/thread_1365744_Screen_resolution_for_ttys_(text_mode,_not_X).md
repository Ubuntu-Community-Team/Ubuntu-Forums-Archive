---
title: "Screen resolution for ttys (text mode, not X)"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by SecretCode on 2009-12-27
I have my new installation of Karmic running very smoothly, with the proprietary Nvidia drivers giving me fast, crisp and snappy performance in X (GNOME) at my laptop LCD panel's native resolution, 1280 x 800.

But the ttys (tty1 to tty6, ctrl-alt-f1 to ctrl-alt-f6) insist on running at a default 640x480. And the same applies to boot-time messages.

Is there a way I can tell Ubuntu to work at 1280x800 when in text mode?

I see a lot of threads on resolution for X, but nothing much on this.

---

### Post by SecretCode on 2009-12-29
[SIZE="1"]*bump*[/SIZE]

---

### Post by SecretCode on 2009-12-30
I know this isn't a showstopper, but there must be someone with an idea to help. The X screens look so good it's a shame to have a messy login (even the pulsing white Ubuntu logo is distorted because it's a wide screen) and limited screen space in tty windows.

---

### Post by SecretCode on 2010-01-03
So, I spent the day booting with different options. 

The grub2 official method appears to be setting the *gfxpayload* option, either to 'keep' or to a specific value. However, no values produced useful results - the login messages and the TTYs either defaulted back to 640x480, or were black or a garbled mess of colours.

The older way is adding '*vga=*' to the boot options, but grub2 says this is deprecated, and it doesn't work for most values. I got halfway by setting vga=792, making sure 'quiet splash' were *not* present, and ignoring the deprecated message. Then I got a 1024x768 resolution for login and tty consoles. Other values just got low resolution.

But the best result was by changing the boot commands in /etc/grub.d/10_linux from 'linux' and 'initrd' to '**linux16**' and '**initrd16**'. Then setting the boot option "**vga=865**" in GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub - and including "quiet splash" or not, it doesn't matter - I am able to get full native resolution of 1280x800, both in login console messages (visible if "quiet" isn't specified) and in TTYs 1 - 6. :) :D

If anyone is tempted to try this out, check what video modes your card supports via ```
sudo hwinfo --framebuffer 
```and get the mode number from the line you want - I used Mode 0x0361 which is 865 decimal. You can probably set the boot option vga=0x0361 directly.

And **remember** after any changes to run ```
sudo update-grub
```



Now ... is this a bug? And is it a bug in Ubuntu, Debian, Grub2 or the kernel? :confused:

---

