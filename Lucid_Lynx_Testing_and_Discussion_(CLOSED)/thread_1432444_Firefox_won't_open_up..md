---
title: "Firefox won't open up."
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by xVehemencityx on 2010-03-17
Hi, I'm using the newest version of 10.04, and I don't know where to post this, but Firefox will not open at all.  I've tried rebooting, and reinstalling, and neither have worked.

---

### Post by rCXer on 2010-03-17
Open a terminal, enter...
```

firefox

```
...and post the output.

---

### Post by n0dix on 2010-03-17
Try with:
```
$ killall firefox
$ firefox --safe-mode
```

---

### Post by bodhi.zazen on 2010-03-17
> **xVehemencityx said:**
> Hi, I'm using the newest version of 10.04, and I don't know where to post this, ... <clip>

If you are running 10.04 it is in Alpha right now, meaning expect bugs and use the lucid forums , lol.

---

### Post by ankspo71 on 2010-03-18
Firefox 3.6 wouldn't start for me the other day after a few updates. I fixed it by removing all instances of java and its plugin(s), then reinstalling only the java packages I wanted. (It seems I had multiple javas installed since java was reintroduced to ubuntu-restricted-extras) So if you have java installed, have a look in that area by searching for java in synaptic. 

Firefox addons can also cause problems so if you have any installed, try backing up the /.mozilla folder in your home directory, then remove the extensions folder in /.mozilla/firefox/(????).default/extensions . This will manually delete your addons.

Hope this helps.

---

### Post by mdurham on 2010-03-18
I got a tip from another thread [here]("http://swiss.ubuntuforums.org/showthread.php?p=8832779") it fixed the problem for me.
See post #10

---

