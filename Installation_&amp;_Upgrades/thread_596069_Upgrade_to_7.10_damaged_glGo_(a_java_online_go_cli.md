---
title: "Upgrade to 7.10 damaged glGo (a java online go client)"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by jimwalsh3 on 2007-10-29
I play go (a board game) online using a java based client called glGo. Before upgrading to 7.10, it worked well. After upgrading, it crashed when trying to use some of its functions (I could still play games with others, but the experience was not as good).

In an attempt to solve the problem, I uninstalled glGo and re-installed it.

Bad idea.

Now my personal account details are gone, and when I try to use "set up new account", it crashes.

---

### Post by The Chef on 2007-10-29
Same issue.  Crashes whenever it needs access to a profile.  Say when you hit the Preferences button on the splash screen, or add login info.  Working on it.  Let me know if you solve. Thanks.

---

### Post by ejket on 2007-10-29
The java client is gGo, and glGo is its successor, written in C++ and python.  GGo seems to work okay for me in 7.10, but it's a bit old (2004) and you may be having a problem with the newest java.

In any case, if one doesn't work, try the other.

---

### Post by Bloch on 2007-10-30
When run from the cammand line glGo returns an error message saying
libpython2.4.so.1.0
is missing.

The version of python in Gutsy is 2.5

The file libpython2.5.so.1.0 exists, so I simply copied it, renamed the 2.5 part to 2.5 and put it back in the folfer ( /usr/lib)

Well glGo workd then - for a while - but crashed when I tried to change the board from 2D to 3D

Maybe if python 2.4 was installed alongside 2.5 it would work? Or maybe not.

I will send an email to the creators at Panda [http://www.pandanet.co.jp/English/glgo/index.html](http://www.pandanet.co.jp/English/glgo/index.html) as it seems to me it shouldn't be too hard to update to a python 2.5 version

---

### Post by Bloch on 2007-10-30
I emailed PANDA-glGo. They are aware of the problems with the new Ubuntu (annd seemingly the latest version of Debian too, if not others)

They suggest this fix, which may be found under the help glgotab  link on this page:
[http://panda-igs.joyjoy.net/English/events.html](http://panda-igs.joyjoy.net/English/events.html)

> Recent Debian and Ubuntu upgrades affect the behaviour of the client
program glGo. The symptoms are unpredictable crashes. Waiting for an
indepth analysis of the problems at this point it seems related to a
recent upgrade of the GTK libraries in combination with the way glGo
uses tabs.

The solution is (for the time being) to turn off the use of tabs in your
glGo configuraton file (~/.glGo/glGo.rc):

   UseTabs=0

This should make glGo run fine. Of course if you didn't use the tabs
mode in the first place you probably were not affected by the bug.

This fix does not help me. glGo fails to launch, reporting libpython2.4.so.1.0 as missing.  Ubuntu 7.10 uses python2.5

Are other users here using python2.4??  Did you install it alongside python2.5?

---

### Post by ejket on 2007-10-30
That explains why I can't seem to download the .deb for glGo.  (This thread made me realize I was using an ancient java client when there was something more recent to try.)  Shame, too, since I wanted it for debian etch, which uses python 2.4 ...

---

### Post by The Chef on 2007-10-30
I suppose you have all seen this note in the IGS install page

> Note to users of SuSE Linux (and possibly others): SuSE ships with an outdated expat library. If glGo fails to start due to missing libexpat.so.1, do the following as root:
"cd /usr/lib"
"ln -s libexpat.so.0.5.0 libexpat.so.1

---

### Post by Bloch on 2007-10-30
Jago is a java client that connects to the IGS server, other servers,  or to gnugo.

I've always preferred its way of handling the removing of stones and scoring at the end. It's  a really nice interface - lacks the 3D effects of glGo, but has beautiful stones.

[http://www.rene-grothmann.de/jago/](http://www.rene-grothmann.de/jago/)

There's also the Cgoban that can be installed from the Add/Remove or by the command:
sudo apt-get install cgoban

It's also perfectly good - for some reason I prefer Jago.

---

### Post by jimwalsh3 on 2007-11-02
Thanks a bunch to all you for the comments.

The "help glotabs" issue existed long before the current problem, so I don't think that the response to the email was accurate.

My friend tried a lot of things mentioned here without success, but I will aim him here, in case.

---

### Post by kalle314 on 2007-11-14
I just noticed that the source code is available at 
[http://panda-igs.joyjoy.net/English/glgo/downloads/src/](http://panda-igs.joyjoy.net/English/glgo/downloads/src/) if anyone would like to have a try -  I didn't manage to build it myself.

---

### Post by fishfunctor on 2007-12-15
Same problem over here.
qgo is a decent substitute for glgo, whereas cgoban offers just the bare bones. That's all three ubuntu packaged go clients for you.

---

### Post by SickBoy on 2008-01-09
Bad thing that cgoban changed it's license and can be no more in repos. I'll give qgo a try

---

### Post by apetresc on 2008-02-09
> **kalle314 said:**
> I just noticed that the source code is available at 
[http://panda-igs.joyjoy.net/English/glgo/downloads/src/](http://panda-igs.joyjoy.net/English/glgo/downloads/src/) if anyone would like to have a try -  I didn't manage to build it myself.

That isn't the source code to glGo -- that's the source code to the LGPL-licensed libraries he uses. None of his own code is open-sourced, or this problem would have been solved long ago.

---

