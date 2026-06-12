---
title: "Flash has no sound in Chrome"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by csulok on 2009-10-19
Hi!

I have 2 computers, I've installed Ubuntu 9.10 on both of them. They have nearly identical packages installed.

I have all kinds of browsers installed on both of them, but flash doesn't make sound in Chrome on one of the PCs.

I was wondering if someone had a checklist I could go through to make sure everything needed for Chrome is there. Settings, packages, everything.

Thanks

---

### Post by Insane_Homer on 2009-10-19
didn't think Chrome for Linux had been released?

How are you running it?

---

### Post by csulok on 2009-10-19
> **Insane_Homer said:**
> didn't think Chrome for Linux had been released?

How are you running it?

There's a package available on google chrome's website for many months now.

---

### Post by sdowney717 on 2009-10-19
[http://ubuntuforums.org/showthread.php?t=1293624](http://ubuntuforums.org/showthread.php?t=1293624)

try the iron chromium browser. i have sound with flash.

---

### Post by sprince09 on 2009-10-19
I also have sound with my flash using the chromium-browser package from the Chromium PPA and chromium-codecs-ffmpeg-nonfree package.

Link to PPA:

    [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Also, I'm running Karmic, not Jaunty, but I've found the recent chromium builds from the PPA to be very stable (more so even than firefox for me!).

---

### Post by csulok on 2009-10-19
> **sprince09 said:**
> I also have sound with my flash using the chromium-browser package from the Chromium PPA and chromium-codecs-ffmpeg-nonfree package.

Link to PPA:

    [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Also, I'm running Karmic, not Jaunty, but I've found the recent chromium builds from the PPA to be very stable (more so even than firefox for me!).

I have tried chromium-daily and I have the same results with it. The PC that currently has sound in Chrome also has sound with chromium, but the PC that currently doesn't have sound in Chrome doesn't have sound in chromium either.

---

### Post by krish.arava on 2009-10-21
Its the same in Firefox. But the media player seems to work.

---

### Post by wcadrin on 2009-10-21
Assuming you're running the 64-bit version of Ubuntu you may be having the same problem I occasionally have.  The flash plugin is 32-bit and there's a process called npviewer.bin that wraps that plugin so it can be used for 64-bit systems.  Just kill that process and you should be fine.  It happens so rarely for me I can't remember if you need to restart Chrome afterwards.

---

