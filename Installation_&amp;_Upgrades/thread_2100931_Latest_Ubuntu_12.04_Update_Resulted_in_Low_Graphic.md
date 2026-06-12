---
title: "Latest Ubuntu 12.04 Update Resulted in Low Graphics Mode Only"
date: 2013-01-03
forum: Installation &amp; Upgrades
---

### Post by DoingMyHeadIn on 2013-01-03
Greetings All ;)

Today I allowed the automatic update on Ubuntu 12.04 64bit to run, this has now resulted in my machine only booting in low graphics mode and I cannot resurrect Unity.  I have tried a number of methods but these have not helped at all. (e.g. sudo... update, upgrade; ctrl+alt+F7, etc).

There is some output data I have, which can be found at:
[http://paste.ubuntu.com/1491310/plain/](http://paste.ubuntu.com/1491310/plain/)
[http://paste.ubuntu.com/1491303/plain/](http://paste.ubuntu.com/1491303/plain/)

Any help to recover the system will be appreciated as (always) I have some important work in Blender, Salome and others that I have been bashing my head against a brick wall for a couple of months :( and need to continue working with for Uni :).

---

### Post by howefield on 2013-01-03
Are you using proprietary drivers ?

If so, try removing them from a virtual console, Ctrl+Alt+F1.

---

### Post by DoingMyHeadIn on 2013-01-03
Thanks Howefield

I have used startx and found that: 
NVIDIA: API mismatch: the NVIDIA kernel module has version 304.48, but hte NVIDIA driver component has version 304.43. Please make sure that the kernel module and all NVIDIA driver components are the same version.

Fatal server error: no screens found, etc etc.

So that means I have a driver error - thanks. Are you aware of a link to some support that will step me through the removal/updating of the NVIDIA driver.
:)

---

### Post by howefield on 2013-01-03
Try in virtual console.

```
sudo apt-get remove nvidia-current
```

---

### Post by DoingMyHeadIn on 2013-01-03
Have tried the sudo command suggested and this has not resolved the issue, I note that system output states:
Package nvidia-current is not installed so not removed.
0 upgraded, installed, removed...

Also when I hit ctrl+alt+F1 nothing seems to happen?

---

### Post by howefield on 2013-01-03
Must be another nvidia package that you have, maybe nvidia-experimental-304 ?

---

### Post by DoingMyHeadIn on 2013-01-03
You rock! :)

We are back in action, last query - Now we are back in action what is best way to have the correct resolution for the desktop that remains set after being turned off.  Should I reload the NVIDIA drivers or is there another recommended method?

---

### Post by howefield on 2013-01-03
I guessing that one of the updates you installed was a kernel update, which knocked out the proprietary drivers.

You should be fine in reinstalling the nvidia driver.

---

### Post by DoingMyHeadIn on 2013-01-03
Thanks

---

