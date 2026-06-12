---
title: "Install Error (Bad Sector??)"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by rwsh on 2010-02-05
Hey all,

This is gonna be a bit long, but please read on, I'm quite lost... I tried to give as many "related" details as I could...

I have a Fujitsu Siemens Amilo 1437G. 
I normally use XP.
My hard disk has 4 partitions.
I wanted to give Linux a shot, downloaded wubi and the desktop cd's from (x&k)ubuntu-9.10-desktop-i386.iso and wanted to try kubuntu and xubuntu first. 

My Laptop has 2 problems:
a) its about 4 years old. After xp starts, I normally have an icon on the tray bar to play with the volume. One day it didn't show up after a startup. I think someone dropped the laptop a while before that, so it could be related to that. Thinking it could be a connection thing, I stuck in a headset and played with the jacks while my computer was starting up, and it worked that time. After this point it just got worse. I used the computer a lot, without sound.. Right now I really have to pull the sockets up with the headphone jacks during startup to have sound. Then, when the computer is on, I still have to play with the jacks sometimes to be able to hear something..

b) The cd-rom drive stopped working as well, it doesn't appear in my computer (except for every once in a long while, so I'm guessing its related to problem a)

So I tried to install kubuntu with wubi. After restarting, I got a black screen with this:

[   20.4823123 ] hda-intel : spurious response 0x0 :0x0, last cmd=0x0f0004
[   21.2343563 ] hda-intel : spurious response 0x0 :0x0, last cmd=0x0f0004
[   22.3239843 ] hda-intel : spurious response 0x0 :0x0, last cmd=0x0f0004
.....

the first number was obviously a counter.. I thought it might have be related to the sound card thing so I played with the jacks and got this for a second:

(the first asterix was actually red.. weird :) )
* PulseAudio configured for per-user sessions
* Enabling additional executable binary formats binfmt-support
* Checking battery state...

And then everything was fine. I got the same screen again and did the same thing, no problems afterwards. The sound issue even seemed to be better because I didnt have to play with the jacks after the startup, while at windows i usually do...

Then I wanted to try xubuntu, I liked it even better but there was one problem, xubuntu couldn't see my other partitions, while kubuntu could... (ofcourse the problem about audio repeated as well) So I wanted to try ubuntu.

Everything was the same, ubuntu could see my other partitions, but, ubuntu said my hard disk had a lot of bad sectors! Kubuntu and xubuntu had worked, but ubuntu couldnt start any programs after installation. When I restarted it tried to install ubuntu again, but same result...

So I came back to xp, checked for bad sectors and xp couldnt find anything...

So I tried to install in a different partition but got the same problem...

What might be going on?? :D

Thanks for reading :)
robert

---

### Post by rwsh on 2010-02-12
no ideas?

---

