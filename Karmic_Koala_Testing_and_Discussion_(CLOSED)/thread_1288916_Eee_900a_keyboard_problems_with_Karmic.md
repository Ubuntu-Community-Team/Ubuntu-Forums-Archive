---
title: "Eee 900a keyboard problems with Karmic"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by blueph on 2009-10-11
I recently upgraded my Asus EeePC 900a to Karmic beta, and everything seems to be working fine except for a few important keys.

1. The backslash/pipe key doesn't seem to do anything at all (xev shows nothing when I press the key).
2. The function keys seem to be shifted over one position on the top row.  On my keyboard, the backquote/tilde key is small and to the left of the F1 key, but when I press it, xev reports F1.  Pressing the actual F1 key shows F2, etc. up to F11, which shows F12.  The F12 key doesn't seem to do anything (dead like the backslash key).

I have tried a bunch of keyboard mode settings in the System->Keyboard application.  I tried the obvious Asus setting, as well as all the Generic keyboards, and many other laptop models.  In all cases, the key behavior was the same.

This worked fine on Jaunty UNR.  I have searched all over and have not found others with the same problem.  I've read posts of folks with keyboard issues, but their solutions either don't work or don't seem to apply.

Any help/advice would be greatly appreciated.

---

### Post by blueph on 2009-10-14
I solved it myself.  An update to the BIOS fixed it.

I'm still not sure why it manifested itself only with Karmic and not with Jaunty, but I'm glad it's working now.

---

### Post by Sven6210 on 2009-10-15
Good to hear the problem is solved. I was quite surprised reading about such a problem as I never faced it, neither with 9.04 nor with 9.10.

Did you get your microphone to work? I posted the modification necessary on my 'EeePC 900a' in order to use Skype and Ekiga for VOIP when traveling.

---

### Post by blueph on 2009-10-17
I haven't tried my microphone at all, to be honest.  I don't use Skype or other VOIP application, so haven't had the need to try it.  I'll try it out and let you know what happens.

I am having problems with my WiFi/WLAN/wireless, though.  It keeps getting disabled in BIOS everytime I shut down my machine.  Whenever I power up again, I have to go into the BIOS and enable it explicitly, as it keeps getting mysteriously disabled.

I have tried following the instructions here:

[http://forum.eeebuntu.org/viewtopic.php?f=7&t=3866](http://forum.eeebuntu.org/viewtopic.php?f=7&t=3866)

but this didn't work.

Any other suggestions would be appreciated.

---

