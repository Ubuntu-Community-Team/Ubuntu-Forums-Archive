---
title: "HDMI only Install Blank Screen or Unsupported Signal"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by beardeddev on 2013-02-20
I decided last night to install ubuntu on a computer that is hooked up to my tv. When I put the USB drive in that has ubuntu 12.10 on it I get to the options to try it out, or install it. I select to install it and then on the one tv I tried to use the screen goes blank, on the other tv the screen says unsupported signal. And the keyboard lights go out and nothing happens.

Im wondering is it just that you can use hdmi out to a tv to install. I dont currently have a monitor available to use. I am planning to order a couple for it however was hoping to get by with the tv for few weeks.

Any ideas would be greatly appreciated.

---

### Post by beardeddev on 2013-02-20
I was able to get ubuntu to boot by setting nomodeset in grub2. Now it starts to boot but gets stuck on the ubuntu logo with the dots under. it starts to load then the dots turn red and it stops.

Any ideas?

---

### Post by cortman on 2013-02-20
Press the enter key and report what the last message on the screen is. This may help troubleshoot it.
Sounds like a graphics issue to me.

---

### Post by beardeddev on 2013-02-20
Hitting Enter doesn't seem to do anything just sits on the ubuntu loading screen.

---

### Post by beardeddev on 2013-02-20
Esc on the other hand does. Seems to be getting stuck after Starting CUPS printing spooler /server [ok].

---

### Post by cortman on 2013-02-21
Sorry! Forgot it's the escape key.
Try booting with nomodeset. Instructions [here]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation").
If that doesn't work, boot into recovery mode per instructions [here]("https://wiki.ubuntu.com/RecoveryMode").
If you can get into recovery mode, run

```
lspci | grep -i vga
lshw -C video
```

and report back what it returns.

---

### Post by beardeddev on 2013-02-21
I am using nomodeset to get to the point im at now. Prior to that I was just getting a blank screen. 

I am unable to get to a recovery mode. The options only consist of try ubuntu, install ubuntu, oem install, and check disc for defects. If i hit escape I get to the grub command line, but not sure what to do there.

---

### Post by MadmanRB on 2013-02-21
sounds like a bad burn to me.
This is a live CD you are trying correct?

---

### Post by beardeddev on 2013-02-21
Yeah, USB. Ive tried remaking it several times thinking that might be the case at first and keep getting the same results. And when I run the check this disk tool, it comes back saying there were no errors.

---

