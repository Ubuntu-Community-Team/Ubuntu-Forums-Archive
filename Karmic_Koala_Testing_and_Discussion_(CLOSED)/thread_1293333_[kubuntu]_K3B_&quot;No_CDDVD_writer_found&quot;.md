---
title: "[kubuntu] K3B &quot;No CD/DVD writer found&quot;"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BigCajun on 2009-10-16
Running Karmic 64-bit. I just grabbed the latest updates from the last 24 hours and now K3B shows me this message, both on an HP EliteBook laptop and my desktop machine. I actually noticed the issue earlier today on my laptop. So I got home, checked to see if K3B was working on my desktop and when I started it up, it showed both CD/DVD burners I have. So I figured it was an issue with my laptop.

However, I then updated my desktop. My last update was about 24 hours ago, so it seems things have broken within the last 24 hours. Now when I start up K3B, I get this:

```
No CD/DVD writer found.
K3b did not find an optical writing device in your system.
Thus, you will not be able to burn CDs or DVDs.
However, you can still use other K3b features such as audio track
extraction, audio transcoding or ISO9660 image creation.
```

Unfortunately, there seems to be a fair number of packages that were changed within the last 24 hours (I guess that's the nature of the beast when the release is just about to come out of Beta). Here's the list of what I updated tonight:

```
cdrdao compizconfig-backend-gconf gnome-power-manager
hal-cups-utils libavcodec-extra-52 libavutil-extra-49 libgudev-1.0-0
libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libudev0
nvidia-173-modaliases nvidia-96-modaliases policykit-1 python-cupshelpers
system-config-printer-common system-config-printer-gnome
system-config-printer-udev ubuntu-wallpapers ubuntu-xsplash-artwork udev
update-manager update-manager-core update-manager-kde xsplash
```

And then after that I got these:

```
compiz compiz-core compiz-gnome compiz-plugins compiz-wrapper
evince evince-dbg grub-common grub-pc grub2 libdecoration0 libevdocument1
libevview1 libusplash0 linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
linux-image-2.6.31-14-generic linux-libc-dev usplash
```

I'm guessing maybe the cdrdao package? But that's just a shot in the dark. I'd say something funky in the kernel packages, except I haven't rebooted (I don't have the little icon in the systray telling me I need to though).

Anyone else having issues with K3B lately?

---

### Post by BigCajun on 2009-10-16
Sorry folks, it must have been the kernel updates as rebooting resolved my issues. I feel like an idiot posting before at least seeing if a reboot would have fixed it.

---

