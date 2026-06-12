---
title: "More Java Problems - Why is this so hard?"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by redwoodguy on 2010-09-08
Ubuntu 10.04 - Firefox - 

Suddenly, I can't upload pictures to COSTCO photo. I call and they say they don't support Linux (of course) but to check my Java version. 

I check and see my Java is not the latest which is version 21 of Sun Java. I have tried a dozen ways to update this, none work. The Software Center app seems useless. I tried downloading a file from Oracle which was a .BIN. I could not make that work. I tried Software Update, and that loads version 20, when 21 is the latest. Why? 

I seem to have a million "java" files or programs including iced tea and all kinds of others. I tried the instructions in another post to make Sun Java the priority. It does nothing. I tried "REMOVING" all these other java apps using Software Center - doesn't remove anything. 

Isn't there some basic simple way to get the right version? This is trying my patience regarding Ubuntu. I've never seen anything so difficult to do which ought to be so simple. Any advice is appreciated.

---

### Post by lykeion on 2010-09-09
[LIST]
[*]Uninstall icedtea6-plugin
[*]Enable partner repository
[*]Install sun-java6-plugin
[*]Restart browser
[/LIST]

See this for details:
[http://ubuntuforums.org/showthread.php?t=1517979](http://ubuntuforums.org/showthread.php?t=1517979)

---

### Post by redwoodguy on 2010-09-09
Thanks. I finally did that, and it actually is working! I must say though, It was not easy. I spent 6 hours doing it. Ok, I admit, I am a Unix Terminal Moron. I have one heck of a time getting the shell to do anything useful, and I don't mind saying I have no interest in learning a complete language just to move files, or run a program. It seems ludicrous that this shell is  key part of anything in the user's world. 

I tried many times using Software Center to "remove" IcedTead. It gives you a remove button, but the button is connected to a rubber hinge and does NOTHING when pressed! I only *accidentally* discovered that with Synaptic Package Manager I could actually, finally REMOVE a program. 

I know this is a rant, but I find this aspect of Ubuntu to be so ridiculous as to be funny by the end of the day. I love the way Ubuntu works as an "appliance" for me getting useful things done. I abhor the way it works for everything else. This business of installing applications is so bizarre it really defies explanation. It's a total disaster for users who don't wish to become programmers. Oh well.

---

