---
title: "Installing the android ADT"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by OsuSurfRat on 2011-12-14
Good day,
I preface my post with the fact that I don't know much about much.
I am trying to set up eclipse to develop android applications.
I am having an awful time trying to use eclipse with the android SDK.

When ever I open eclipse it runs like molasses.  I am able to open the android VDM and an emulator and it all seems to work if you don't mind waiting for ever. I think that I have the android SDK extracted to the wrong place.  Where should this be?  I think it should be in the usr/lib but can not seem to get it there.

Also, I read that in an earlier version of Ubuntu (Drake) the Sun Java SDK must be installed rather than the GNU Java SDK.  Is this true for lucid as well?

---

### Post by OsuSurfRat on 2011-12-15
I threw in the towel on that situation.
I upgraded to naughty narwhal and am going to build my projects from the command line with the android ADT.
:guitar:

---

### Post by MAFoElffen on 2011-12-16
> **OsuSurfRat said:**
> Good day,
I preface my post with the fact that I don't know much about much.
I am trying to set up eclipse to develop android applications.
I am having an awful time trying to use eclipse with the android SDK.

When ever I open eclipse it runs like molasses.  I am able to open the android VDM and an emulator and it all seems to work if you don't mind waiting for ever. I think that I have the android SDK extracted to the wrong place.  Where should this be?  I think it should be in the usr/lib but can not seem to get it there.

Also, I read that in an earlier version of Ubuntu (Drake) the Sun Java SDK must be installed rather than the GNU Java SDK.  Is this true for lucid as well?
I'm running Eclipse Galileo with the Andriod SDK... On Ubuntu 11.04 64bit.  Seems to run okay. startup lags a bit, but once it's running.

I have the SunJava installed as when I originally installed it, thats what it said it required.  I heard from other users that now it works with the Open Java JDK, but since I already had the other installed...

---

### Post by N00b-un-2 on 2011-12-16
Yes, you are going to want to install the official sun Java 6 or Java 7 JDK.

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install update-java
```

You're also going to need the Eclipse plugin.  Once you download all that stuff, you're going to need to fire up the Android Software and VM Manager (the android binary in "tools" in the SDK)  All in all, it usually takes several hours to set up the Android SDK with Java and Eclipse.

You will need REAL java if you plan on writing apps for Android.  It's a proven fact that ANY Android byte code that was developed using the OpenJDK will fail to build at compile time.

to answer your question, there is no such thing as extracting the SDK to the wrong place.  I keep mine in my home folder and I symlink the commonly used binaries (android, adb, ddms) to /usr/local/bin so that I can execute them easily.

As far as android VMs go, I've never had one run at anything close to real time speed.  They are always a bit laggy no matter what you do.

---

