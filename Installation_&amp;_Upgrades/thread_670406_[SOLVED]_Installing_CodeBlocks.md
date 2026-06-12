---
title: "[SOLVED] Installing CodeBlocks"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by MunkyJunky on 2008-01-17
Ive been trying to get Codeblocks for a while now, but it never seems to want to work. 

I've had a look at several topics on installing Codeblocks about the forums, and after trying different methods I've still not been able to get it. 

I'm running Ubuntu Gusty, so if anyone can give me any help to getting Codeblocks I would be very thankful! Preferably Id like instructions using apt-get, as I find that easier to work with than building from source, but ANY method will do... I miss Code::Blocks!  :(

---

### Post by kellemes on 2008-01-17
Does this help?
[http://ubuntuforums.org/showthread.php?t=558030&page=2](http://ubuntuforums.org/showthread.php?t=558030&page=2)

---

### Post by MunkyJunky on 2008-01-17
I got the following from trying the instructions in that thread:
```

The following packages have unmet dependencies.
  libcodeblocks0: Depends: libwxgtk2.8-0 (>= 2.8.7) but 2.8.4.0-0ubuntu3 is to be installed
E: Broken packages

```

...Which I'll go ahead and assume means I need wxWidgets, even though I'm pretty certain I installed 2.8.7 earlier. That was actually the first thread I used to try help me get codeblocks, but unfortunately, it didn't want to work. 

Also, if I this
```
sudo apt-get install libwxgtk2.8-0
```

It says the newest version is already installed. 

Any suggestions? :confused:

---

### Post by kellemes on 2008-01-17
Sorry for not really helping I guess..
I'm on another system so I can't try myself..

I would at least remove all instances of libwxgtk and focus on getting version 2.8.7 or higher.

Found another link, see post #4
[http://ubuntuforums.org/showthread.php?t=590676](http://ubuntuforums.org/showthread.php?t=590676)

This link helping? Could be I'm wrong but as I understand it, you can get the bleeding edge version of wxwidgets (libwxgtk ??). Well, see if it works.
[http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian)

---

### Post by MunkyJunky on 2008-01-17
That top link worked! 

Oh what a glorious day this is for me, I've been trying to get Codeblocks up for a LONG time now. You, my dear Kellemes, have made my day!

---

### Post by kellemes on 2008-01-17
> **MunkyJunky said:**
> That top link worked! 

Oh what a glorious day this is for me, I've been trying to get Codeblocks up for a LONG time now. You, my dear Kellemes, have made my day!

Glad I could help. :)

---

