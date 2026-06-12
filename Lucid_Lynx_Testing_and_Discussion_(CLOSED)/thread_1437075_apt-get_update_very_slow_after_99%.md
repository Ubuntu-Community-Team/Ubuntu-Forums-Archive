---
title: "apt-get update very slow after 99%"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by cheapsaket on 2010-03-23
when I run apt-get update, it gets upto 99% quickly then is stuck for 2 minutes or so.
I am running beta 1 and have updated it yesterday

any steps to troubleshoot which source might be causing the delay?

---

### Post by ubername on 2010-03-23
Try running synaptic, click 'reload'. If you are having the same problem as I was, you will get to e.g. '39 of 40 files' refreshed fairly quickly. Click 'cancel' and a window will pop up showing which repo/ppa(s) causing problems. Mine was the google one for chrome.

---

### Post by dino99 on 2010-03-23
> **cheapsaket said:**
> when I run apt-get update, it gets upto 99% quickly then is stuck for 2 minutes or so.
I am running beta 1 and have updated it yesterday

any steps to troubleshoot which source might be causing the delay?

that mean lot of people download at the same time, and if you use an overload server, well speed connection is falling, nothing strange.

If you cant wait few seconds, try with an other mirror, it's up to you .

---

### Post by AlanR8 on 2010-03-23
Same delay, same Google Chrome repo....

Nuff said.

---

### Post by cheapsaket on 2010-03-23
Yep Chrome was the culprit.

Thanks all

---

### Post by ubername on 2010-03-23
The google chrome repo problem can be fixed by installing squid (a web proxy) and then pointing synaptic at the proxy rather than direct connection to internet. If you like, I can help you through it, but two days ago I was going 'do what? a what proxy?' so I'm no expert but I got it working. Or check here:
[http://ubuntuforums.org/showthread.php?t=1430453](http://ubuntuforums.org/showthread.php?t=1430453)

---

### Post by krige on 2010-04-09
I had the same problem. The proxy installation and configuration seemed a little too much work for such a trivial problem, so I looked for another solution.

I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```

It seems Google recognizes this as a problem, but "there is no timeframe yet" for fixing it:
[http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3](http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3)

---

### Post by cheapsaket on 2010-04-09
> **krige said:**
> I had the same problem. The proxy installation and configuration seemed a little too much work for such a trivial problem, so I looked for another solution.

I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```

It seems Google recognizes this as a problem, but "there is no timeframe yet" for fixing it:
[http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3](http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3)

Hey thanks for finding that out

---

