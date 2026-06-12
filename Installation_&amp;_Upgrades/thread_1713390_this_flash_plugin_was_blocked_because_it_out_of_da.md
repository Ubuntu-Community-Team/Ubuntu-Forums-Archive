---
title: "this flash plugin was blocked because it out of date"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2011-03-24
I am using Flash plugin 10.1 (please do not suggest upgrade) I would like to use the older version.Things work fine in Firefox but when I use Chrome I get a warning 
```
this flash plugin was blocked because it out of date
```
I checked [here]("http://www.google.ru/support/forum/p/Chrome/thread?tid=4525b12dee005f88&hl=en") and also a command line switch --allow-outdated-plugin as given [here]("http://peter.sh/experiments/chromium-command-line-switches/")  but inspite of opening browser like this 
```
google-chrome --allow-outdated-plugins
```
I get the warning
```
this flash plugin was blocked because it out of date
```

---

### Post by x C0MMAND0 x on 2011-04-07
Any resolution? I am also having this issue.

---

### Post by jamesbon on 2011-04-08
Not yet I am waiting for some one on forum to reply.

---

### Post by sportsdude81 on 2011-04-28
I am having the same issue as well.  I am running 64 bit.  Are you guys too?

---

### Post by sportsdude81 on 2011-04-28
Apparently I was having this issue because I am running 64 bit.

If you replace the libflashplayer.so it should fix this problem.  It fixed it for me.

```
locate libflashplayer.so
```

and replace it with the "square" 64 bit linux, which you can find here [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz")

Don't forget to restart your browser.

---

