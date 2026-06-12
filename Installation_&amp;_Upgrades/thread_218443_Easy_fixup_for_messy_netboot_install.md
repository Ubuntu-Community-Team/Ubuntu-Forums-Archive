---
title: "Easy fixup for messy netboot install?"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by bernied on 2006-07-18
Does anyone have an easy fix for me?

I've installed Kubuntu Dapper onto a 686 pc booting from a usb stick with root filesystem on an nfs share on a gentoo fileserver.

I did it this way because there was no space on the PC hard-drive (but loads on the server) and I didn't want to mess with the PC's hardware anyway (the 'family' would be 'upset').

So it works, but not completely...
For a start I couldn't get grub to netboot properly (couldn't access the nic), so I'm loading the kernel off the usb stick and pointing it to the nfs root on the fileserver.
But of course the ubuntu kernel/initrd combination didn't like the setup and didn't sync with the filesystem - it stops at a busybox (???) prompt (is there something I can do with that initrd?)

So it's running off a custom-built, trimmed down gentoo kernel, with hopefully all the right drivers installed.

So the remaining issues:
- Sound!! It's so quiet without that hard-drive going, but I want it to make some friendly, musical noises. I have definitely compiled the right driver in (Intel8x0) but I'm sure there must be some Ubuntu Voodoo I can do.
- Some niggly bits in kde, like starting konsole always gives me a shell of /bin/sh and not /bin/bash, even though it's configured (I think) for bash. Bash works fine, just type bash and it starts, so why??

The question is, are my issues just the result of not installing enough packages?
So far I used debootstrap to get a minimal install of breezy on, then I did a dist-upgrade to get dapper, then I installed kubuntu-desktop thinking that would get everything else - wrong. So then I went back for ubuntu-standard. (Then the mouse wouldn't work and I realised I'd put the wrong USB protocol in the kernel so had to recompile that - oops - but I swear I have the right sound driver). Then I found usbmount and usb-storage (why aren't they standard?).
So, are there any more packages needed for a base desktop system?

And any ideas on cleaning up the mess easily - I was hoping I could break into the (normally lovely) installation halfway through, but I don't dare use the CD because it's an aggressive little creature (IMO) and does things without asking first and the last thing I want is it to reinstall grub on the hard-drive because it can't find it.

Any ideas?

---

### Post by bernied on 2006-07-18
Both issues mentioned above are now solved.

OK - I apologise. I just read some docs (last resort, obviously) and have now got lovely sweet sound from my lovely kubuntu desktop that is running only on a usb stick (now i just want that particular usb stick to be invisible, hmmm...).

And I worked out how to configure konsole - properly

thanks for looking anyway

---

