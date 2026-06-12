---
title: "Update/install hell on Samsung Q1 usb"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by kpgalligan on 2008-07-19
This is extremely frustrating.  Can't really stress that enough.

I had 7.10 running on my Samsung for a while now.  Did light code editing on it, and watched videos.  Had the touchscreen working, etc.  Took some tweaking, but it worked out.

I wanted to try the mobile edition, but the installer wipes the hard drive completely, which I didn't want to do.

One day, I decided to do a version upgrade to 8.04.  Huge, huge mistake.  Touchscreen doesn't work anymore.  Couldn't figure out why.  Since I'm pretty much watching videos at this point, I figured "what the hell", and installed mobile.

Its pretty flakey.  Was missing a few things that I wanted from the regular install.  So, I installed 8.04.

Had some trouble.  Tried installing 7.10 with the net install.

That failed.

Reinstalled 8.04.  Booted once (I think).

Now I get a grub error 15, file not found.

I've been editing grub from the grub command line, but can't seem to sort it out.

So, what I want to do now is just get ubuntu running good enough to watch videos on my machine.  I'd like to have a touchscreen and be able to do normal computer stuff, but, again, at the very least, boot and use the mouse.  Is there a bug in the usb install process for 8.04?  So far I've had great experiences with ubuntu.  Frankly, I'm shocked at how difficult this has been.  Hate to be the complainy guy on an open source forum, but I'm ready to chuck this thing out the window.  What should I try to install?  I really don't have hours to mess around with grub.  It shouldn't be quite this difficult.

---

### Post by PmDematagoda on 2008-07-19
Can you please post the menu.lst file in the Ubuntu install if possible? Also(if possible), post the output of:-
```
sudo fdisk -l
```

---

