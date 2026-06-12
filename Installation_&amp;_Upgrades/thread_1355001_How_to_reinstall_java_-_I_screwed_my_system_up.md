---
title: "How to reinstall java? - I screwed my system up"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2009-12-14
I was attempting to install the Android SDK, which requires (I'm told) Sun Java 6. I installed that, but something isn't right.

For example:
```
$ update-alternatives --config javac
No alternatives for javac.
```

And this:
```
$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu12)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
```

On top of that, Gmail crashes my browser now due to /usr/lib/mozilla/plugins/libflashplayer.so.

I'm thinking it is best to remove all the java-related stuff and start over.

If that's the best approach, which packages should I remove? Synaptic shows a lot of java related packages.

I want to start fresh by installing Sun Java 6 (for Android SDK) and 64 bit Adobe flash (which I know how to install).

FYI: ```

$ uname -a
Linux UbuntuBox 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux
```

---

### Post by phillw on 2009-12-14
Hi, this how-to may be a bit out of date - check the release versions of what is being proposed to down-load. (you'll be looking for possibly ..6 and not ...5)

but, I can confirm it works (he that posted back to state it did).

I'll go have a play and update it if you can't follow it.

[http://ubuntuforums.org/showthread.php?t=1235767&highlight=sdk+android](http://ubuntuforums.org/showthread.php?t=1235767&highlight=sdk+android)

Regards,

Phill.

---

### Post by phillw on 2009-12-14
oh ... 

> On top of that, Gmail crashes my browser now due to /usr/lib/mozilla/plugins/libflashplayer.so.

Try uninstalling it via synaptic. 

now, don't quote me on this one ... but ... if it doesn't want to go, delete the little horror., you may also find it lurking in /home/*username*/.mozilla/plugins  

That'll take care of it, you can then put on the adobe version - it's over here --> [http://ubuntuforums.org/showthread.php?t=1352947](http://ubuntuforums.org/showthread.php?t=1352947)

(Sorry, I'm on 10.04 alpha - but it is the latest release of flash from Adobe and shuld be happy in 9.10)


Phill.

---

### Post by MountainX on 2009-12-14
Thanks for your replies. Should I delete IcedTea before I start? What other java packages should I delete to start fresh?

---

