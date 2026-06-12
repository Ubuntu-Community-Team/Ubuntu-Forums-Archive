---
title: "Trying to Install Ubuntu 18.04 (plebeian here)"
date: 2018-08-09
forum: Installation &amp; Upgrades
---

### Post by bananabueza on 2018-08-09
This is my first time try and installing ubuntu. So please explain like you are explaining it to a baby.

After I finish installing ubuntu, it ask me to restart my computer, so I restarted it. But before it restarted my computer froze and after waiting a couple of minute I press the power button and remove my USB stick.

When I start my computer again and went to ubuntu, this happened
[ATTACH=CONFIG]280686[/ATTACH]
At first I thought It was updating or installing something, so I left it alone. But when I came back, it's still running the same line of gibberish (at least to me).

So I turn off my computer again and try running ubuntu again for multiple time, but I got the same result.

Please help

---

### Post by springshades on 2018-08-09
The error looks like it's related to a PCI Express port obviously. If you don't know what that is, it's the long slot things on your motherboard. More specifically, it's probably an error related to the card that you have plugged in to one of those slots. Usually, that's going to be your graphics card, but it could be many other things.

Since it sounds like there might have been an issue with your install itself, you may just want to try installing again. Trying to figure out what went wrong will likely take hours at minimum. Reinstalling can probably be done in 20-30 minutes.

The error message doesn't seem to be a lot to go on unless someone has seen the exact same message before and knows what it is. It looks like a general error about one of your PCIE cards to me. You may want to post back with more details about your computer and what you're trying to do. Someone may have a better idea of a known incompatibility if they know your hardware for example. Stuff that may be helpful: as much about your hardware as you know, which specific Ubuntu ISO are you using (minimal vs server vs standard Ubuntu... 18.04.0 or 18.04.1... 32 bit vs 64 bit... etc), and your intended setup like whether you are dual booting or just running Ubuntu.

Just as a general test, when you installed Ubuntu did you run the live session first to make sure it worked? It's not a 100% accurate test, but it's a pretty good way of knowing whether Ubuntu will run on your hardware.

---

### Post by bananabueza on 2018-08-09
I did tried it first, and it worked fine. So I went ahead and tried to install it.

I'm just going to try and reinstall it. 

So do I need to uninstall ubuntu first? Or do I just stick my USB again and try to install it.

---

### Post by springshades on 2018-08-09
You should be able to just reinstall it again. The installer should reformat your partitions which will get rid of everything.

---

### Post by bananabueza on 2018-08-09
Thanks, but I was able to fix it. Yahoo!

I went to recovery mode and pulled of a hacker-man.

I'm using it now as I'm replying to you.

---

