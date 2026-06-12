---
title: "Fresh install, Software Updater hangs - command line alternative?"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by jub2 on 2016-06-02
I find that it's a toss-up whether Software Updater will complete or hang on the long initial update after a fresh install. 

How can I accomplish this via the command line?

```
sudo get-apt update
```Will that do it, or do I also need to run
```
sudo get-apt upgrade
```

Also, on the restart immediately after a fresh install, a message box pops up "Incomplete Language Support" with the option to "Run this action now". 

Seems strange that a LTS distribution (Xubuntu 16.04 64-bit) would have something like that as incomplete. Wondering if this is normal. Language selected during install is US English.

---

### Post by ajgreeny on 2016-06-02
```
sudo apt-get update
sudo apt-get upgrade 
```should do it; you had the **apt-get** reversed.

As for the language message you saw, I am not sure of the reason, but it may be that you did not choose to install updates as you carried out the installation, or perhaps you did not have a network connection, which would have been necessary for that.  You will have chosen a language, but there are so many available that the system always seems to think that more would be iseful.  I personally ignore that message as long as I have the English_UK version, as that is all I ever need or use; your situation may be different of course, particularly if you have users who want different keyboard layouts.

I always update after installing and also add the third party applications needed, eg for mp3 playback, etc etc, as I then get just what I want and need.

---

### Post by jub2 on 2016-06-02
Thanks. So what does this do?
> sudo apt-get upgrade

I want to stay on the LTS version of Xubuntu (16.04) and not upgrade beyond that.

I was not connected to the network, so you're probably right about the language message.

---

### Post by QIII on 2016-06-02
Hello!

upgrade and dist-upgrade upgrade the packages within the current release.  They do not upgrade the release itself to the next.  14.04 stays 14.04 and 16.04 stays 16.04.

---

### Post by jub2 on 2016-06-02
Thanks. So I should run the following and that's the equivalent of running Software Updater?

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Edit: doing some reading and it looks like just executing apt-get update and apt-get dist-upgrade is sufficient, as the latter's function is a superset of apt-get upgrade's function.

---

