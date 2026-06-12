---
title: "Firefox 2.0.0.2 parallel installation"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by aFan on 2007-03-01
I'd like to install Firefox 2.0.0.2 on my Dapper box. I did it manully. Downloaded firefox-2.0.0.2.tar.gz --> untared it into /opt --> made a launcher in /usr/share/applications.

The problem! When i run /opt/firefox/firefox script, instead of the FF 2.0.0.2, the default instalation FF 1.5 launches. Basicaly I did every thing described in [https://help.ubuntu.com/community/FirefoxNewVersion]("http://help.ubuntu.com/community/FirefoxNewVersion"). However i don't want to make FF 2.0.0.2 the default instalation, rather i'd like to run the new FF 2.0.0.2 PARALLELY to the default FF 1.5.

I made symlinks in /usr/bin, but that didn't work (they were broken). What do i have to do to run FF 2.0.0.2 separately form FF 1.5 (keep it in tact)?

I'll apprishiate all the help (If I could learn smothing in the process all the better:-D)

Best regards, M.

---

### Post by kerry_s on 2007-03-01
Did you name the sim link something other than firefox?

I think you should go the easy route with swiftfox which is separate by default->

sudo gedit /etc/apt/sources.list

deb [http://getswiftfox.com/builds/debian](http://getswiftfox.com/builds/debian) unstable non-free

to the bottom.

Then just open synaptic press the reload button and scroll down to swiftfox, select the 1 that matches your cpu.

---

### Post by aFan on 2007-03-01
Yes, i made a backup of the original firefox script & renamed it to e.g. firefox2. Than i symlinked it to /usr/bin

BTW, i'm now familiar with switfox, what the difference to firefox?

However, i still want to do it the hard way:) , without synaptic or aptitude!

---

### Post by kerry_s on 2007-03-01
Swiftfox is firefox built for speed. It's made optimized to the processor that you have.-> [http://getswiftfox.com/](http://getswiftfox.com/)

---

### Post by aFan on 2007-03-01
Installed Swiftfox for my architecture. I tryed form repos first (as you suggested) and the installer. The difference is form repos is installed to /use/lib/ and installer install's to /opt.  

However, firefox and swiftfox do not run parralely! Namely, if i run eather and than launch the other, an additonal window of the one that run first "pop-up"...how about that?

This is probably because they both rely on mozilla and mozilla-firefox in /usr/bin?!

---

### Post by kerry_s on 2007-03-01
Yes, you can only run one or the other at a time, but not both.

---

### Post by aFan on 2007-03-01
> **kerry_s said:**
> Yes, you can only run one or the other at a time, but not both.

Maybe we should suggest that to the developer (would it be safer)?!

---

### Post by nyinge on 2007-03-01
hmm...  They both could be trying to open up the same profile, default.  Create a new profile,
```
 firefox --ProfileManager  
```

Then, run Firefox 2 in the terminal,
```
  /path/to/firefox2.0.0.2/firefox -no-remote -P NAME_OF_NEW_PROFILE  
```

---

