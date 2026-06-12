---
title: "how to kill hidden adept process?"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by coughlin on 2007-01-11
During a Java JRE install, there was a Java requirement for the user to 'ok' the Java license.   It was stuck with no way for me to click 'ok' during the Adept installation.

When I closed Adept, I could not re-open Adept without it throwing a dialog box, saying that there is an existing Adept (or Apt etc.) process running.

I've tried:
$ ps -ax
... and ...
$ kill <process ID>
... for anything resembling Adept or Apt.

... but, I still get the warning - even after re-booting.

What process(es) am I failing to see, that Adept sees as an existing process?
Until I find out, I can't install/un-install anything ...

thanks,
Mike

---

### Post by taurus on 2007-01-11
```
sudo kill -9 **PID**
```

---

### Post by coughlin on 2007-01-11
> **taurus said:**
> ```
sudo kill -9 **PID**
```

I'm curious ... what is the significance of the -9 ?
I left it out because I thought that it meant to wait 9 seconds before killing the process ID.
What if one doesn't care if it waits 9 seconds or not? i.e. what if one simply wants to kill the process, immediately?

thanks,
Mike

---

### Post by confused57 on 2007-01-12
> During a Java JRE install, there was a Java requirement for the user to 'ok' the Java license. It was stuck with no way for me to click 'ok' during the Adept installation.

You can highlight the 'ok' button by pressing the right(or maybe left arrow), then press enter..I know this is after the fact, but FYI.

---

