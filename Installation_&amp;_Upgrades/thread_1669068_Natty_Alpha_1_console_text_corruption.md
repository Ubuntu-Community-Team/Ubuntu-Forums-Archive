---
title: "Natty Alpha 1 console text corruption"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by sirjasonr on 2011-01-17
Hello all you wonderful ubuntu-loving people :)

I am just after a little bit of help with fixing a text corruption issue / advice for filing a bug report (if necessary).

So, generally speaking the stability I am experiencing with Natty is as I expect; I'm fully aware that this is a very very early development release and so all sorts of things can go wrong. So let's not be mean to me about that... I totally get the risks involved etc. etc. I just wanted to point that out ;)

So while Gnome/Unity are up and running, graphics run more or less perfectly, the boot process text is completely garbled and if after everything is fully loaded I hit Control+Alt+F1-F6 the text looks like:
* [this]("http://picasaweb.google.com/lh/photo/uv-jTmc_9p_ZArZytBTBDTZf4cZWJILkBmYHchZ4xbc?feat=directlink")
* [the above image close-up]("http://picasaweb.google.com/lh/photo/L1hVdV31O29Bi7bBrD0b5DZf4cZWJILkBmYHchZ4xbc?feat=directlink")
The above links are supposed to be of the ubuntu login prompt.

The problem occurred after running the upgrade command: ```
sudo do-release-upgrade -d
```
As is standard upgrade procedure.

Is there anything obvious going on that I can tweak to make it all happy again?

Since I have a working GUI, it's not super important for me to fix it in a rush... so if it's a matter of simply waiting for updated packages, then so be it. But any advice on the matter would be fantastic!

Cheers,
Jason

---

### Post by efflandt on 2011-01-17
Until Natty is released, there is a separate forum for it [http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

I have never seen such a display with apparently wrong or corrupted fonts.  The only problem I have with text consoles (tty) is that the login prompt (often, but not always) ends up in lower right of screen 3.5 lines from bottom, so I cannot see what I am typing.  I am using GT 430 with nvidia 260.19.29 drivers (no tty problem with same nvidia drivers in Maverick).

What graphic card and drivers are you using?

---

### Post by sirjasonr on 2011-01-18
Thanks for letting me know about the correct forum. I have reposted there and will use that thread instead. If you still want to follow it, this is the link:

[http://ubuntuforums.org/showthread.php?p=10373303]("http://ubuntuforums.org/showthread.php?p=10373303")

To answer your question, my graphics card as reported by lspci is 01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1).

I still have no idea what its problem is! Ohhh well...

---

