---
title: "Update has screwed up ANOTHER wireless configurtation!!!"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-11-08
This is really getting old. Why does the crap CONTINUE to happen? OVER, AND OVER, AND OVER AGAIN.

If I'm not smart enough to get it right in the first place, that's MY fault. If an upgrade knocks my wireless out of configuration over and over and over again, well, that's my fault too. 



Where is system restore ??? THAT SHOULD BE THE FIRST PROMPT, BEFORE CHANGING ANY CONFIGURATION!!!

---

### Post by pytheas22 on 2008-11-08
How did you get your wireless working in the first place?  If you manually compiled and installed a driver from source, then yes, Ubuntu updates will break it each time that the kernel gets updated, because the module that you compiled needs to be built specifically against the running kernel--so if your kernel changed, you need to recompile the wireless driver to match your updated kernel.

Alternatively, you could select an older kernel at the grub boot menu that you see shortly after turning on your computer (you may need to press escape to get into it; if so a message will display on your screen that says something like 'press escape to enter boot menu...booting Ubuntu in 3-2-1 seconds...') and your wireless would work running under that, provided that you previously compiled a wireless driver against that kernel.

If you didn't do any manual hacking to get wireless running, then the updates should not be breaking your wireless, although it does happen (and too frequently, I agree) that poorly tested updates may include drivers that don't work the way they're supposed to.  If you think that's happening to you, please post the output of:
```

lspci -nn
lsusb
lshw -C Network
uname -m
```

That will tell us which driver you use.

---

### Post by buccaneere on 2008-11-08
Hi there pytheas...

I got it back up with fwcutter module. I think that's how I had it before; I don't have to do it everyday, so I can't remember every time, plus I'm doin' 3 machines wireless, 1 hardwire.

Still, an app that restores all system configurations is necessary. I know this isn't unique to me.

---

### Post by pytheas22 on 2008-11-09
If you're using the b43 driver (which you are if you use b43-fwcutter to extract firmware), it should not be broken by updates.  If you're certain that updates are doing it, you may want to [file a bug report]("https://launchpad.net/ubuntu/+filebug/+login").

---

