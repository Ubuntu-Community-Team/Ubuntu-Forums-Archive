---
title: "Ubuntu Minimal CD Install; Black Screen"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by tgftw on 2011-10-08
So, I used the Ubuntu Minimal Install CD, installed the base files.

Took out the install disk, rebooted, got a black screen.

If I press CTRL+ALT+F1, it brings up tty1, and everything is fine from there.

Isn't it supposed to show me tty1 from the get-go? I expected to see a command line when I loaded my PC, not a black screen ;)

Is this working as intended, or did I do something wrong?

It's on a Dell GX270, can post more specific information if needed, although I wouldn't think it'd be very relevant.

Thanks in advance!
Tom

EDIT: Using 11.04 minimal CD, just downloaded and burned today.

---

### Post by MAFoElffen on 2011-10-08
> **tgftw said:**
> So, I used the Ubuntu Minimal Install CD, installed the base files.

Took out the install disk, rebooted, got a black screen.

If I press CTRL+ALT+F1, it brings up tty1, and everything is fine from there.

Isn't it supposed to show me tty1 from the get-go? I expected to see a command line when I loaded my PC, not a black screen ;)

Is this working as intended, or did I do something wrong?

It's on a Dell GX270, can post more specific information if needed, although I wouldn't think it'd be very relevant.

Thanks in advance!
Tom

EDIT: Using 11.04 minimal CD, just downloaded and burned today.
Since this is on a Minimal install, read all, before trying to solve.

There is two options for Minimal installation on that disk Graphical and Text mode.  I assume you did Graphical.. That is option 1 and just says "Install".

When it came to the "Software Selection"... what software package did you select and install?  At that screen of the install, is where the Desktop Environments are chosen (along with other packages.)  From what I've noticed, , if you don't select a DE, it starts Xorg-server then locks up at a black-screen because there is no Desktop installed to load up...

If you did not install a DE- Since you "can" get to tty1, 
```

sudo tasksel

```Will bring the app from that screen back up for you to install a DE, such as Ubuntu...

If that doesn't work, no problem... Reinstall.  Look for that screen to come up.  It near the end of the install process, just before the Grub install process.  In the scrolling text box is the packages with checkboxes before each.  It starts out with server package... The Desktop Environment packages are down below near the end (Ubuntu, Kubuntu, etc).

*** If you did install a DE and you get this black screen then you just need to install a video driver for your card... will wait to hear from your before I go on with that, if needed.

---

### Post by tgftw on 2011-10-08
> **MAFoElffen said:**
> 
When it came to the "Software Selection"... what software package did you select and install?  At that screen of the install, is where the Desktop Environments are chosen (along with other packages.)  From what I've noticed, , if you don't select a DE, it starts Xorg-server then locks up at a black-screen because there is no Desktop installed to load up...


Well, yes, this is the problem. I've since installed a desktop environment (LXDE) and everything is working smoothly with that.

However, you shouldn't have to have a desktop environment, several Ubuntu implementations can function well with just a command line.

I guess it's just a little quirk that I didn't expect, not a big deal, just wasn't sure if there was some way to go without a DE without the strange beginning.

I'd say it's solved though, sounds like it just works that way.

---

### Post by papibe on 2011-10-09
Just in case other people see this.

Booting into a black screen when you installed the command line on the Minimal CD it's a bug. (More info here: [Bug #695658]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/695658"), [Bug #700686]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/700686"), and [Bug #831752]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/831752")).

To fix it, as explained in Bug #695658:
> (1) Edit /etc/grub.d/10_linux (e.g. "sudo nano -w /etc/grub.d/10_linux") and comment out the line containing "vt.handoff", or change the number from 7 to some lower number. (I tried it both ways; they both worked.)
(2) Run "sudo update-grub" to apply the new configuration.
(3) Reboot. A usable virtual terminal with a login prompt comes up automatically.

IMHO it seems that they are making sure the bug won't happen in 11.10, but I see no resolution yet to fix the previous versions.

Regards.

---

