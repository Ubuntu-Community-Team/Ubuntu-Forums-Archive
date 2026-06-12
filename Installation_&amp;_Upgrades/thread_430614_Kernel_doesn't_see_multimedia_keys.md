---
title: "Kernel doesn't see multimedia keys"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by Lacoste on 2007-05-02
Hi there,
      I'm a long-time Linux user, somewhat recent Ubuntu desktop installer.  I'm having a problem and I'm hoping someone can point me in the right direction.   I am trying to get my multimedia keys working on my keyboard.  I have checked out the hotkeys and lineak packages, tried modifying my xorg.conf, but the root cause of my issue seems to be that the kernel doesn't generate any codes for the keys when pressed.  I used xev and no codes are generated for the 8 keys on my Compaq 9963, or my 0133.   Nothing occurs when I go to a tty (alt-F1) and try hitting these multimedia keys.
     I checked the kernel config for the default kernel ( /boot/config-2.6.17-11-generic ), but under Device Drivers -> Input device support -> keyboards I just see 4 keyboard modules for non-PC keyboards.  What am I missing?  I assume that all these common multimedia keyboards are bundled into the default keyboard driver ... why won't my system see the codes?   Does it matter if the keyboard is connected via USB or PS2?   I'm pretty sure I tried both.  My current guess is that there is a problem with the hardware (keyboard or motherboard) or that my particular combo doesn't work, but if anyone has any ideas, I'd be very happy to try them out.

Thanks!

Lacoste

---

### Post by kidders on 2007-05-03
Hi there,

I clicked on this thread thinking "Ah... I know this one!" ... but it seems like _you_ know all the right things to try too.

Occasionally, I come across input devices that don't function _fully_ in Linux ... ie some buttons work, and others don't. For instance, an A4Tech mouse I'm currently using has 10 buttons, only one of which won't talk to xev. My guess is that there's something non-standard about it that, in a fully manufacturer-supported environment (eg Windows/OSX), would be handled by the supplied A4Tech driver. It seems odd that ***none*** of your extra keyboard buttons work though.

This may be a ridiculous thing to suggest, but do you suppose that the way X is interacting with your keyboard makes any difference? For instance, could there be "Option" directives that you could add to your xorg.conf's "InputDevice" section that would improve things?

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by Lacoste on 2007-05-04
I went through checking the xorg.conf while trying to resolve the problem.  One of the packages I tried had you change the XkbModel from pc105 to inet.  However, even if I don't start X, I should still get a response from the keys in the console on login, and I don't get anything, so I think it's a kernel or hardware problem.

I'll keep poking around ...

Lacoste

---

### Post by kidders on 2007-05-04
> **Lacoste said:**
> However, even if I don't start X, I should still get a response from the keys in the console on loginI wasn't so sure about this, but it certainly _seems_ reasonable.

I noticed this ... [http://linux.omnipotent.net/article.php?article_id=12340](http://linux.omnipotent.net/article.php?article_id=12340) ... on my travels. The tool it mentions (hotkeys) doesn't seem to be in any way special, but I thought I would mention it because the page specifically refers to your keyboard.

I hope this doesn't turn out to be a hardware problem. :-(

---

### Post by Lacoste on 2007-05-07
Nope, hotkeys is at the application layer again (I tried it and lineak prior to starting this thread).  I'm pretty sure this is a hardware issue with my motherboard, but I'm not sure why.  I have a Dell xw6000 with their 'Linux-recommended' BIOS installed.  Maybe I will try going to a normal BIOS.

Thanks for following up though!

Lacoste

---

