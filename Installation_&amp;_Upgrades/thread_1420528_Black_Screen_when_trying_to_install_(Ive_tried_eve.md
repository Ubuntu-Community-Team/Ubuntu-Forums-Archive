---
title: "Black Screen when trying to install (Ive tried everything)"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by SteadyEdd on 2010-03-03
Ok so i been searching around on google and the forums and so far all solutions have failed.

Im trying to install 9.10 on my acer 5935g with Nvidia gt 240m.

When I choose install I get a blank screen. I tried setting it to safe graphics mode and no change, ive tried changing the boot line by removing splash and replacing with nosplash, ive tried taking out the quiet part and added various options to the line like noapil etc. and nothings working? So far all ive got is a black screen with 2 cursor marks in the top left and top right corners.

I noticed on the boot line there are 2 dashes at the end of the line, what are they for? '--'

---

### Post by darkod on 2010-03-03
That sucks. :(
If you tried safe graphics, noapic, etc, I guess the only option left is the alternate install cd. But note that even if it installs OK, the first boot might not succeed and you might need to do some tweaking depending what the problem is.
On the other hand, the first boot might go just fine.

The alternate installer is text based, and works in most situations. You don't have the nice GUI during install but it's not difficult to use at all.

You can get it here, scroll down and you'll see all the images. You have alternate i386 or amd64 depending if you want 32bit or 64bit version.
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by SteadyEdd on 2010-03-03
This is the edited bootup line I used, can someone tell me if im even doing it right as some other forum posts are posted up with bad grammar etc.

[normal boot line] nosplash noapic irqpoll noirqdebug --

I left the dashes on the end as I dont know what they are there for?

---

### Post by SteadyEdd on 2010-03-03
Right ive done the alternate install instead and it kind of works. I got the grub loader to work but it still goes black when i try to start, even in recovery mode.

ive tried doing ctl-alt-f1 to get a console and it doesnt work. I know the login is working because I can hear the drums of the login screen. I dont know what to do once i get a console up anyway. wtf am i supposed to do?

EDIT:

I added i915.modeset=0 to my grub line and it booted up. so ill just install the nvidia driver from the desktop now and hope it works.

---

### Post by darkod on 2010-03-03
> **SteadyEdd said:**
> Right ive done the alternate install instead and it kind of works. I got the grub loader to work but it still goes black when i try to start, even in recovery mode.

ive tried doing ctl-alt-f1 to get a console and it doesnt work. I know the login is working because I can hear the drums of the login screen. I dont know what to do once i get a console up anyway. wtf am i supposed to do?

EDIT:

I added i915.modeset=0 to my grub line and it booted up. so ill just install the nvidia driver from the desktop now and hope it works.

Glad to know you're getting there, step by step. :)
I don't know much about video drivers but if in doubt which driver to install for nvidia, you can quickly check here too. Just select your card model, and it will show which driver version supports it. You don't have to download it from nvidia, some of the drivers are in the ubuntu repositories.
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by farkascs on 2010-03-09
I have the exact same problem on the exact same laptop model. The problem is I can't get to a console. I know it works, because I can log in, and when I type 'init 0', the laptop shuts down, but doing this blind won't work for me.
I tried 'service gdm stop', but didn't help...

Any ideas?

---

