---
title: "Grub problems in Ubuntu 9.10"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by Green9090 on 2010-02-02
I installed 9.10 on a computer I'm working on, and right away the graphics went out. It won't display the proper resolution without shoving the display significantly to the left.

After MUCH Googling, I found that this can be fixed by a driver called i915. After much MORE Googling, I found [http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html](http://www.insidesocal.com/click/2009/11/are-your-graphics-dead-in-ubun.html), which as you can imagine filled me with relief.

And THEN I try to follow the instructions and discover to my pure horror that GRUB has been gutted and made unusable in 9.10. GRUB2 just simply does not seem to have an option to insert the i915 driver into my boot command.

Does anyone have any ideas, or should I just forget this unstable release and burn a 9.04 disk instead?

---

### Post by darkod on 2010-02-02
Unstable???

Look here in section 5, in the part about the /etc/default/grub file.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Especially pay attention to the explanation for the following parameter:
**GRUB_CMDLINE_LINUX**
If it exists, this line imports any entries to the end of the 'linux'  command line (Grub Legacy's "kernel" line) for both normal and recovery  modes. This is similar to the "altoptions" line in menu.lst

I guess this is what you need, if it helps.

And for the record, if you are interested, I don't know grub2 that much, I just started using ubuntu with 9.10 version. But it took me only few minutes to find this.

---

### Post by Green9090 on 2010-02-02
Tried it, didn't work. Inserted "i915.modeset=0" into the "GRUB_CMDLINE_LINUX" field, saved, ran update-grub, rebooted... and nothing's changed. Either it's a coincidence that I have the same problem that is solved by the i915 driver, or that command doesn't work or works differently than it should.

My reasoning for calling this unstable is that never before have I installed a fresh copy of Ubuntu and spent over a day trying to then make my computer usable again. Never before have I found a simple solution to my problem in multiple places that ONLY the latest version has made unusable. I've been a casual user of Ubuntu for 5 years and always been able to bumble my way through, but have always watched things become easier and simpler as I went. This is the first time a new version has made something stupidly complicated and unwieldy that used to be as simple as editing a file. This version is broken from the perspective of a casual user.

---

### Post by darkod on 2010-02-02
I definitely understand the frustration, but as long as manufacturers scramble to make windows drivers for their hardware and ignore linux drivers, we're gonna be in this mess.
Ask yourself, would this be easier in windows without windows driver present? I know it's not a consolation, I'm just thinking aloud and sometimes getting pi**ed off how people claim windows works better sometimes just because manufacturers prepare drivers for it. :(
10.04 is far from release but if it interests you, you can check the live desktop with the latest daily build from here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It's barely in Alpha but it already has some issues from karmic resolved. Of course, you can't still install it as main OS. :(

---

### Post by Green9090 on 2010-02-02
I never said a thing about Windows being better. I run a Windows partition on my main computer that gives me 50x the problems of Ubuntu easily (but I am addicted to gaming). I'm just saying that this latest version seems to be a significant downgrade from earlier, more stable Ubuntu versions.

I think I'll let this thread sit for a day, and if no solutions are forthcoming by tomorrow I'll just restart the process with a nice copy of 9.04 until there's proper fix documentation for GRUB2.

Thanks for your help, by the way.

---

### Post by darkod on 2010-02-02
> **Green9090 said:**
> 
Thanks for your help, by the way.

Well it wasn't much of a help. I hope someone else can jump in.

---

