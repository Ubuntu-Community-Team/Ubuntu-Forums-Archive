---
title: "Need Install VLC on Ubuntu without Internet [Beagleboard]"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by avi@nitc on 2010-03-02
Hi all,
I am a Newbie to linux, And 

I am trying to** install VLC player on OMAP based beagleboard[BB]**, which has **Ubuntu 9.04** OS, **without GUI [no X**].

There is no Internet connectivity on Beagleboard. I did not find any How-to for this case.

I need VLC to receive a stream of data from an AdHoc network and display. Which are the essential libraries i need to install. and how do i do that.


[LIST=1]
[*]Do I need to download and install VLC on BB, as I do on Intel machines.
[*]Or, do I need to cross compile, as OMAP is an ARM based processor. if so, How do I do that.
[/LIST]

As i am not using GUI , guess vlc-nox should be sufficient.

Regards
Avinash

---

### Post by avi@nitc on 2010-03-03
Hi,

:( not much hlp,

I found out that i can use 
$ sudo dpkg -i package.deb 

to install debian packages. I downloaded vlc-nox for armel machine [Beagleboard] from 
[http://packages.debian.org/lenny/armel/vlc-nox/download](http://packages.debian.org/lenny/armel/vlc-nox/download)

when i do dpkg on beagle board, it throws tens of error message, saying dependent libraries not found.

I understand i need to install depedent libraries. but my question is , 
Do I have to download each n every lib mannually and install, or am I doing it completely wrong?

Please suggest, Thanks in advance.

Regards
Avinash

---

### Post by ImperialXT on 2010-03-03
Why do you need VLC? wouldn't it be better to use mplayer?

---

### Post by avi@nitc on 2010-03-03
I don't know if mplayer is able to read stream from network? [Please let me know if I am wrong]

But have tested VLC player to do that. 

I am Live streaming the desktop captured from my laptop using FFMPEG + FFSERVER, over a WiFi Adhoc Network. and trying to read the stream at BeagleBoard using WiFi USB adapter. This is where i need to install VLC Player.

Regards
Avinash

---

### Post by avi@nitc on 2010-03-04
Yeah!! managed to solve the problem :)

Got help from Beagleboard mailing list :)
[http://groups.google.com/group/beagleboard/browse_thread/thread/22d980bab9da9214#](http://groups.google.com/group/beagleboard/browse_thread/thread/22d980bab9da9214#)

Thought this could help newbie's like me looking for** ubuntu for OMAP based Beagleboard**.

Regards
Avinash

---

