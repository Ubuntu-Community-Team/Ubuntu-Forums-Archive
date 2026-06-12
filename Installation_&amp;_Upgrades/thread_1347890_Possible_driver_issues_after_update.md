---
title: "Possible driver issues after update"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by ucal on 2009-12-06
So I just updated the system, and I'm ashamed to say that I did it blindly.  All I remember is that the kernal got updated, as well as what is probably a whole bunch of other stuff.  Now, I can't start warcraft 3 (it gives me cd check issues), which is a problem that I have had before, and was fixed by updating to the latest ATI driver for my card.  

Also, the entire system graphically lags like a bitch.  Just scrolling down in firefox with the mousewheel is like a slide show now (performance isn't reduced, it's just that there's no smooth animation).

So, how do I get rid of this latest series of updates?

EDIT: The proprietary driver is activated, but not in use. Does this have anything to do with my problems, and if so, how do I fix it?  Reinstall the driver?

---

### Post by ucal on 2009-12-06
Here's the output of fglrxinfo, don't know if it's relevant.

```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  156 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14

```

---

### Post by ucal on 2009-12-06
Okay, I fixed the issue. For some reason, the xorg wasn't getting used, so I generated a new one with the following command, and rebooted.  Good luck if anyone has a similar issue!

sudo aticonfig --initial -f

---

