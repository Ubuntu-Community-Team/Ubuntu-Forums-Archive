---
title: "Authentication Required"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by TheRaveinlinux on 2010-06-11
Hello guys I´ve searched for this problem of mine throughly in the forums but I cannot find anything so if any mod sees this please redirect me :]
Ok now on to the problem..
Yesterday my girlfriend installed Ubuntu, I guided her through the installation by phone since we live in different states. Everything went fine until she tried installing Java, I´ve installed Java using the terminal and the software center, and never gotten the error she got which said: ´Authentication is required to install software packages, the application is attempting to perform an action that requires privileges. Authentication is required to perform this action.´
We tried using both the terminal and the soft center and nothing? I´ve never gotten the error before :o she typed in the password that it prompts her for but still nothing.
It also happens for ANY application she tries to install which is pretty weird. Any help is greatly appreciated.
-Luis

---

### Post by efflandt on 2010-06-11
Authentication is typically required to do anything that affects the entire system, so things can be installed as root, or similarly "**sudo** " prefix is needed for similar things done from the terminal.  The password should be her normal password.

By default, 10.04 uses a different open source java instead of Sun Java.  If she opens Synaptic and installs **ubuntu-restricted-extras**, that will install java, flashplugin, and other codecs related to audio/video.  And instructions in Synaptic description for that package includes instructions how to install something needed to play DVD video.

---

