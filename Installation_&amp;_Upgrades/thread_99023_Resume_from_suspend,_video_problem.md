---
title: "Resume from suspend, video problem"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by hizaguchi on 2005-12-04
My laptop is a Dell Inspiron 4150 with an ATI Mobility Radeon 7500 M7 video card.  After some searching of the forums, I found out how to enable suspend to ram, and it is working just fine, but when I try to resume from being suspended I get a screen full of garbled brown letters, followed by either a plain black screen or something that looks like a barcode.  The mouse cursor is a big white block.

I thought maybe it was my video driver, so I tried to install a new one, but the ATI driver does not support my card, and I got an error message when I followed the guide for installing it (sorry, don't remember the exact message, not smart enough to write it down, but it was something about the device not being present).

Has anyone seen this before?

---

### Post by hizaguchi on 2005-12-05
Ok, in case anybody else is in the same boat, there is a line in /etc/default/acpi-support that the comments tell you if you change "mem" to "standby" it will save less power but work with more systems.  I changed it and it works now... a little too good.  My computer has become narcoleptic.  It falls back asleep after I wake it up the first time.

---

### Post by ranf on 2005-12-06
**How** do you suspend it? And how do you resume it? Key combination? Lid?

---

### Post by hizaguchi on 2005-12-06
I'm having a different problem with shutting the lid, because if I do that the monitor turns off and doesn't come back on till I restart the computer.  So I have been using my suspend button or selecting suspend from the logout menu.  Also, the more I play with it, it seems to be a random occurence.  Sometimes it falls back asleep once, and sometimes it does it repetatively.

---

### Post by ranf on 2005-12-06
The remaining question is how do you resume? I simply use the Ctrl key (but I have a different brand of laptop).

---

### Post by hizaguchi on 2005-12-06
Oh yeah, sorry, I've just been using the power button to resume (like I would from a Windows suspend).  I tried alot of other keys, but I'm not sure if control was one of them.  I'll give that a shot.

---

### Post by hizaguchi on 2005-12-06
Ok, I tried that and every other way of putting it to sleep or waking it up I could think of.  It still randomly falls back asleep.  No idea where to go from here.

---

### Post by ranf on 2005-12-08
[QUOTE=hizaguchi]Ok, I tried that and every other way of putting it to sleep or waking it up I could think of.  It still randomly falls back asleep.  No idea where to go from here.[/QUOTE]
**Maybe** running:
```
sudo tail -f /var/log/acpid
```

tells you something useful.

---

### Post by termite on 2005-12-08
I have a similar problem.  My laptop (Toshiba Satellite A65) suspends fine, but doesn't turn the screen on when I come back from suspend.  In fact, nothing at all happens until I reset.  The output from 
> sudo tail -f /var/log/acpid
is:
> [Thu Dec  8 15:19:20 2005] exiting
[Thu Dec  8 15:19:32 2005] starting up
[Thu Dec  8 15:19:33 2005] 47 rules loaded
[Thu Dec  8 15:19:33 2005] client connected from 9346[111:111]
[Thu Dec  8 15:19:33 2005] 1 client rule loaded
[Thu Dec  8 15:20:18 2005] exiting
[Thu Dec  8 17:47:11 2005] starting up
[Thu Dec  8 17:47:12 2005] 47 rules loaded
[Thu Dec  8 17:47:13 2005] client connected from 6227[111:111]
[Thu Dec  8 17:47:13 2005] 1 client rule loaded

Any ideas?

---

