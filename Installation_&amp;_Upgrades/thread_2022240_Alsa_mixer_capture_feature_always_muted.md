---
title: "Alsa mixer capture feature always muted"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by smoczyna on 2012-07-10
Hi

I've recently upgraded my ubuntu server to the latest 12.04 version. Almost everything is fine but experiencing few painful issues. Namely my alsa mixer shows capture features always muted, or rather turn down completely after restart. Each time I have turn up the volume to be able to use skype.
How can I set the volume of the capture input for good?

---

### Post by jmfal on 2012-07-10
Welcome to Ubuntu.

I'm pretty sure that capture is muted at startup by default.

I tried looking for a work-around or script to add, but .........

---

### Post by smoczyna on 2012-07-10
My previous version 10.04 LTS was fine about that so there is probably a file containing this settings. Or we've got a step back here. For instance playback is alway on the level of volume I set last time.

Besides what would be the reason to mute anything by default.

---

### Post by jmfal on 2012-07-10
Capture is line input and there is for the most part no incoming sound at startup

I can't help  thats the way it is .
I can turn up my mic and line in and restart and both will be muted at restart

---

### Post by flemur13013 on 2012-07-10
You might be able add "amixer" to a startup/login script:

Try: 
$ amixer  scontrols
$ amixer --help

 --> 
$ amixer sset Capture 100

I'm not sure about the "100" value.

---

### Post by beterhans on 2012-07-11
open a command windows

use alsamixer to adjust your settings
and use 
```

sudo alsactl store

```

---

### Post by smoczyna on 2012-07-23
and what is the location of the file where those settings are being saved by the ALSACTL command ? It is still not working although it looks like settings are being saved, I've got no error and any other feedback.

---

### Post by dda on 2013-02-12
> **beterhans said:**
> open a command windows

use alsamixer to adjust your settings
and use 
```

sudo alsactl store

```

Thank you, that helped me too.

---

