---
title: "GRUB_GFXPAYLOAD_LINUX does nothing"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Brandon Williams on 2010-03-23
The new /etc/default/grub variable GRUB_GFXPAYLOAD_LINUX (at least I think it's new in Lucid) does not appear to do anything. My expectation is that if I set this variable, it will control the eventual console resolution. For example, if I set it to 'keep', the console resolution/font should be the same as the resolution/font in the grub menu. Or if I set it to 800x600, the resolution of the console should be 800x600 (as long as 800x600 is a supported resolution as indicated by vbeinfo).

When it is set, I get a line in /boot/grub/grub.cfg that says 'set gfxpayload=<value of GRUB_GFXPAYLOAD_LINUX>'. No matter what value I set, the console resolution is always the native resolution of the monitor.

I have observed the same problem on one laptop that uses the intel framebuffer (inteldrmfb) and one that uses the radeon framebuffer (radeondrmfb). On both machines, I have also tried adding the appropriate vga=XXX setting to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub. No matter what I try, I haven't been able to find a way to change the console resolution on lucid.

Is there some other mechanism for doing this on Lucid that I just haven't been able to find yet?

---

### Post by dcstar on 2010-03-24
> **Brandon Williams said:**
> 
......
Is there some other mechanism for doing this on Lucid that I just haven't been able to find yet?

Try the **startupmanager** package.

---

### Post by vishalrao on 2010-03-24
have you tried setting both GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX to "1024x768" in /etc/default/grub then running "sudo update-grub" ?

Also try "echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash" then "sudo update-initramfs -u" then reboot?

---

### Post by Brandon Williams on 2010-03-24
> **dcstar said:**
> Try the **startupmanager** package.

All startupmanager does is configure grub to use the vga=XXX option, which doesn't work. Thanks for the suggestion, though.

---

### Post by Brandon Williams on 2010-03-24
> **vishalrao said:**
> have you tried setting both GRUB_GFXMODE and GRUB_GFXPAYLOAD_LINUX to "1024x768" in /etc/default/grub then running "sudo update-grub"?

Yes. The GFXMODE setting does what it's supposed to do (change the resolution of the grub menu), but the GFXPAYLOAD setting doesn't cause any apparent change in resolution for the console.

> Also try "echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash" then "sudo update-initramfs -u" then reboot?

I've done this in order to get plymouth to display the splash screen. Since it only impacts whether the initramfs will have framebuffering (the console after boot was already buffered), I don't think this change would be expected to impact the post-boot console behavior.

Thanks for the suggestions.

---

### Post by Milos_SD on 2010-03-24
> **dcstar said:**
> Try the **startupmanager** package.

This works great with Nvidia binary driver. :D Now I have plymouth and TTY's. :D

---

### Post by Brandon Williams on 2010-03-24
> **Milos_SD said:**
> This works great with Nvidia binary driver. :D Now I have plymouth and TTY's. :D

Please explain. I already have plymouth and TTYs without startupmanager. I tried using startupmanager to change the console resolution, but it used the deprecated and (for me at least) non-functional method of adding a vga=XXX kernel parameter.

Are you saying that you used startupmanager to change the console resolution and that it works to change the resolution? If so, what changes did startupmanager make to your /etc/default/grub file? Which framebuffer module are you using? Does nvidia have its own framebuffer and does their framebuffer use kms (like the radeon and intel framebuffers)?

Thanks.

---

### Post by vishalrao on 2010-03-24
Probably also try:

blacklist vga16fb in /etc/modprobe.d/blacklist-framebuffer.conf
"sudo update-initramfs -u"
reboot?

before that what does "lsmod | grep fb" show?

---

### Post by Brandon Williams on 2010-03-24
> **vishalrao said:**
> Probably also try:

blacklist vga16fb in /etc/modprobe.d/blacklist-framebuffer.conf
"sudo update-initramfs -u"
reboot?

before that what does "lsmod | grep fb" show?

lsmod says the following:
```
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
vga16fb                11321  0 
vgastate                8961  1 vga16fb
```

I had though about attempting to blacklist vga16fb. I'm not sure if there's a better framebuffer module for me to load in its place. What should I add to /etc/modules if no alternate framebuffer modules loads on its own?

For now, I'll give it a try and revert if it doesn't help or if it appears to break something.

Thanks.

---

### Post by Brandon Williams on 2010-03-24
Blacklisting vga16fb was not the solution, but my concern about what modules would be used got me to look more closely at /var/log/messages than I had previously done. I saw the following:
```
$ grep Console /var/log/messages
<snip>
Mar 24 12:38:54 jitender kernel: [    0.939976] Console: switching to colour frame buffer device 128x48
Mar 24 12:38:54 jitender kernel: [    1.452891] Console: switching to colour dummy device 80x25
Mar 24 12:38:54 jitender kernel: [    1.453199] Console: switching to colour frame buffer device 175x65
<snip>
```

My setting in /etc/default/grub appeared to be having the desired effect, but it was being over-ridden. This occurred immediately after initializing the radeon driver. Looking more closely at the log lines related to init of the radeon driver, I noticed "radeon kernel modesetting enabled." This is what's different about lucid and karmic ... lucid defaults to using KMS while karmic defaulted to not using it.

Now my /etc/default/grub has these settings:
```
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=keep[/code[

And I have a new file called /etc/modprobe.d/radeon.conf:
[code]options radeon modeset=0
```

With the above settings, I get the console resolution that I'm looking for. To the best of my knowledge, disabling KMS can lead to longer boot times, but it should not cause negative behavior post-boot.

Thanks all for pushing me to look in the right places.

---

### Post by Milos_SD on 2010-03-24
> **Brandon Williams said:**
> Please explain. I already have plymouth and TTYs without startupmanager. I tried using startupmanager to change the console resolution, but it used the deprecated and (for me at least) non-functional method of adding a vga=XXX kernel parameter.

Are you saying that you used startupmanager to change the console resolution and that it works to change the resolution? If so, what changes did startupmanager make to your /etc/default/grub file? Which framebuffer module are you using? Does nvidia have its own framebuffer and does their framebuffer use kms (like the radeon and intel framebuffers)?

Thanks.

When I tried this howto to get plymouth working, I didn't had TTY's (only black screen when I switch to it):

[http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html](http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html)

But now I just used startupmanager to change the resolution to 1280x1024 and checked "Show boot splash", and now I have plymouth and TTY's working great. :D

lsmod | grep fb 
shows:
```
fbcon                  32878  71 
tileblit                2103  1 fbcon
font                    7877  1 fbcon
bitblit                 4449  1 fbcon

```

The only change I see in /etc/default/grub is this:

```
GRUB_CMDLINE_LINUX=" splash vga=795"
```

Nvidia doesn't support KMS, and don't have it's own framebuffer.

And by looking at syslog, I think it's using vesafb:

```
vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90005800000, using 5120k, total 5120k
vesafb: mode is 1280x1024x32, linelength=5120, pages=0
vesafb: scrolling: redraw
vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
fb0: VESA VGA frame buffer device

```

---

### Post by dino99 on 2010-03-24
Doing all theses tweaks about grub and nvidia configs will broke everything.

Don't follow oldies and outdated workaround, Lucid is new and dont work like Karmic or Jaunty or older distro.

You should remove / purge all packages about grub2 & grub-legacy if present, and all nvidia packages & xorg.conf too.

 Then reinstall grub-pc without tweakings, and nvidia-current. Reboot then activate driver hardware and configure grub.

---

### Post by eaglemystic69 on 2010-03-26
Hi dino99,

Will the purging you suggest help my initramfs issue too?  My thread is located at: [http://ubuntuforums.org/showthread.php?t=1438161](http://ubuntuforums.org/showthread.php?t=1438161)

Or is there another resolve for the boot stall at the initramfs command?

---

### Post by Brandon Williams on 2010-03-29
eaglemystic69: Please see my follow up on your other thread. I don't see a direct relationship between this thread and the other one, so it's best to move your discussion back there.

---

