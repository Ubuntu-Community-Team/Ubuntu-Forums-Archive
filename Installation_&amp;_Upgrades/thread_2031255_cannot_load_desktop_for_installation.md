---
title: "cannot load desktop for installation"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by vectorthorn on 2012-07-21
ok, so i downloaded the desktop version of 12.04, and i see the ubuntu  loading dots while it loads. at some point, i see a cache of what was  last on my video card (from my fedora desktop), and then the screen goes  black, falling back to console, and complains about the nouveau driver.

i am some what familiar with this, because i always have to replace it  with nvidia's driver for fedora, but it's never kept me from getting a  desktop. i have no idea what to do for ubuntu, to get the graphical  desktop from the live cd...

any one know a way around this? is there a way to ad boot arguments to the live cd like you can with fedora so that you can blacklist the nouveau driver?

thanks

---

### Post by vectorthorn on 2012-07-21
on the main screen you can hit a(ny?) key to see the options. after fiddling around for a moment, you'll see that under f6 is the nomodeset option. hit enter to select it, then hit escape to get back to the boot menu. i also seen that i could add the text to the boot parameters manually, which i did. so, i'm not sure which one did it, but it got me into a desktop.

---

### Post by vectorthorn on 2012-07-21
ok, i got the installer cd to run completely, but it won't boot. i get a screwed up screen for a while, then it goes black, and that's it, until i reboot. i can't find a way to change the boot parameters to say nomodeset when booting after install. any one know how to fix this?

---

### Post by vectorthorn on 2012-07-23
ok, evidently i should have done a search first. this whole thing is discussed in great detail here:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

as a side note, the grub menu may not show up at all for you, and you may try hitting shift repeatedly, as instructed, only to see no grub menu. on my computer, i have to HOLD down the shift key, AFTER a certain point in the boot process, in order for the motherboard not to assume that the key is stuck, and for grub to acknowledge it.

---

