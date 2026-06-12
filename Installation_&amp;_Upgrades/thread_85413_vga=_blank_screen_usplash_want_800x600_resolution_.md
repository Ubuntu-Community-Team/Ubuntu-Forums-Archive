---
title: "vga= blank screen /usplash? want 800x600 resolution in console"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by bekamyn on 2005-11-02
Panasonic Toughbook CF-45 266Mhz
Neomagic Video Chipset.

I performed a server-expert install and everything went fine. My grub line with the default kernel has both vga=0x315 and splash and it boots fine. Albeit without any fancy pictures people talk about.

Because this is a slow machine I decided to compile a leaner kernel without ACPI and other bloat , something I've done several times previous. After 5 hours of compiling, hey I told you it's a slow machine. I boot the kernel and the dreaded blank screen which everyone claims is related to usplash and can easily be solved by removing vga= in the grub boot parameters.

1. What is usplash? Since when my kernel loads all I see is crappy white text at 640x480 resolution.

2. In order to get the kernel not to blank screen I remove the vga= . It boots fine but it's at 640x480 with crappy white text.

As a test I built a kernel using only make oldconfig and then compiled the new kernel so it should be a clone of the default right? Well it gives the blank screen issue also so I not sure what's going on. 

Here's what I want:
99.9% of the time this laptop will be run in console for wardriving and I'd like a 800x600 resolution, and I don't want to wait the extra 2 minutes for X to load so that I can run kismet in a terminal window.  How can I get back my 800x600 resolution? I could care less about pretty pictures while booting.

---

### Post by SilentCacophony on 2005-11-02
Usplash is just a simple graphic with 'ubuntu' displayed, a progress bar under the logo, and some not-so-good-looking text that displays the boot steps and status, much like you'd get without usplash, but using 'splash' in grub.

If the problem is related to usplash, your best bet would probably be to remove the usplash package.

I've previosly tried to change my framebuffer resolution to 1024 x 768, and it went blank on me, so I'd assume that's your problem at this point. After I removed usplash, the problem cleared.

AFAIK, usplash may be part of the ubuntu-desktop meta-package, so if it says it's removing that as well, it's no big deal. The only catch there is that it's advised to have that meta-package installed when trying to dist-upgrade.

---

### Post by bekamyn on 2005-11-03
[QUOTE=SilentCacophony]Usplash is just a simple graphic with 'ubuntu' displayed, a progress bar under the logo, and some not-so-good-looking text that displays the boot steps and status, much like you'd get without usplash, but using 'splash' in grub.

If the problem is related to usplash, your best bet would probably be to remove the usplash package.

I've previosly tried to change my framebuffer resolution to 1024 x 768, and it went blank on me, so I'd assume that's your problem at this point. After I removed usplash, the problem cleared.

AFAIK, usplash may be part of the ubuntu-desktop meta-package, so if it says it's removing that as well, it's no big deal. The only catch there is that it's advised to have that meta-package installed when trying to dist-upgrade.[/QUOTE]


I removed usplash (apt-get remove) rebooted and added the vga= with no luck still got  a blank screen

Just in case, here's my grub kernel line:
boots fine:
kernel /boot/vmlinuz-2.6.12-10205 root=/devv/hda1 ro noapic nolapic quiet

blank screen:
kernel /boot/vmlinuz-2.6.12-10205 root=/devv/hda1 ro noapic nolapic quiet vga=0x315

---

### Post by schilcha on 2005-11-16
[QUOTE=bekamyn]I removed usplash (apt-get remove) rebooted and added the vga= with no luck still got  a blank screen

Just in case, here's my grub kernel line:
boots fine:
kernel /boot/vmlinuz-2.6.12-10205 root=/devv/hda1 ro noapic nolapic quiet

blank screen:
kernel /boot/vmlinuz-2.6.12-10205 root=/devv/hda1 ro noapic nolapic quiet vga=0x315[/QUOTE]

I had a problem with vga= and a blank screen as well. In my situation, I tried 1280x1024x16M, which is vga=0x31B -- resulting in a blank screen. When I fall back to 1280x1024x64k (vga=0x31A), things work well: no background image (I'm trying to get that working right now), but nice small font and also some icons for the boot-status. 

If your problem is similar to mine, try 800x600x64k (vga=0x314) instead of 800x600x16M (vga=0x315).

Good Luck!

---

### Post by bekamyn on 2005-11-25
[QUOTE=schilcha]I had a problem with vga= and a blank screen as well. In my situation, I tried 1280x1024x16M, which is vga=0x31B -- resulting in a blank screen. When I fall back to 1280x1024x64k (vga=0x31A), things work well: no background image (I'm trying to get that working right now), but nice small font and also some icons for the boot-status. 

If your problem is similar to mine, try 800x600x64k (vga=0x314) instead of 800x600x16M (vga=0x315).

Good Luck![/QUOTE]

Tried all the arrangements all produce a blank screen.
I don't have any splash program installed and the result is the same if using the standard init or or initng

---

### Post by schilcha on 2005-12-02
One last guess (although you've probably already checked on that):
Since it's a self-compiled kernel, did you make sure to include all those framebuffer-realted stuff. And, if you compiled them as modules, did you add those to the init-ramdisk? (although, maybe it's required to compile them into the kernel to make them work). I once struggled with SuSE 8.something, until I realized that I simply messed up the kernel. 

Anyways, good luck!

---

### Post by charly4711 on 2005-12-07
Hi,
here's what you do:
1) create a file /etc/mkinitramfs/modules with two lines:
```
vesafb
fbcon
```

goto (3) if you don't want usplash

2) if you want usplash:
relax ;)  , then
find a file /usr/share/initramfs-tools/scripts/init-top/usplash and there locate a line

```
insmod /lib/modules/`uname -r`/initrd/vesafb.ko
```

replace it with:

```
insmod /lib/modules/`uname -r`/kernel/drivers/video/vesafb.ko
```

3) reinstall the kernel image

this all provided you HAVE the vesafb module with your build and you used make-kpkg.

HTH,

Karl.

---

### Post by bekamyn on 2006-01-13
Sorry been on other projects lately. I try the last 2 suggestions and report back.

---

### Post by mättu on 2006-01-15
> 
3) reinstall the kernel image


can you please give instructions how exactly to do this? 
(I'm a little scared to ruin my system when it comes to such things..)
The rest works (finally!) & I have small fonts.

tanx a lot
:m)

---

