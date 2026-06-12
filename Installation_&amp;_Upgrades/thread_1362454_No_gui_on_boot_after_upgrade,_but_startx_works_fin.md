---
title: "No gui on boot after upgrade, but startx works fine"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by maartmeester on 2009-12-23
So I have scoured the ubuntuforums as well as the rest of the internet for solutions to my problem, but up to now I haven't found a suitable solution. 

Here's the lead-up to the problem. On a perfectly working Ubuntu 9.04 I installed XBMC from the repository xbmc.org indicated. After this installation successfully completed I played around with the program for a while, before upgrading to 9.10 using the Update Manager. After this upgrade also completed without any problems, I played around with XBMC some more and used the option XBMC offers to shutdown my system (so straight from XBMC, not by selecting the shutdown button from Ubuntu).

And that's when the sh*t hit the f*n.

Since then Ubuntu boots to the command line (no GUI) resulting in the following message:
> Ubuntu 9.10 computername tty1
computername login:
This may seem quite similar to [the sticky thread]("http://ubuntuforums.org/showthread.php?t=1305459") in this forum, but in sharp contrast to the symptoms described there, I have no video-related problems whatsoever. When I log in in the command line environment and run "startx" the X-environment loads effortlessly and my system reports no errors at all. 

In the X-environment I have successfully completed a number of diagnostic tests and also updated my Ubuntu through the Update Manager, but nothing I've done has resulted in automatically loading the X-environment when booting.

So my question now is: what can I do to autostart the X-environment when booting my system like it used to do?

I consider myself to be quite the Linux-n00b, so detailed instructions on how to fix this would be much appreciated!

---

### Post by tommcd on 2009-12-23
There is a bug report about this on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/438820](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/438820)
As it says, this may be related to **upstart**, which is used for starting services on bootup and stopping them on shutdown in Ubuntu now:
 [http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)
You are booting to tty1 instead of tty7 like you should. When you bootup, try hitting: ctrl + alt + F7, and see if you get the gdm graphical login prompt.
Check if upstart is installed:
```
aptitude search upstart
```
If there is an "i" before the package name it is installed. A "p" before the package name means it is not installed. If you do not have upstart, then try installing it and reboot. Also make sure gdm is installed. If you got all the updates for 9.10 you should have these though. 
There are threads about this that predate 9.10 however:
[http://ubuntuforums.org/showthread.php?t=950992](http://ubuntuforums.org/showthread.php?t=950992)
[http://ubuntuforums.org/showthread.php?t=978295](http://ubuntuforums.org/showthread.php?t=978295)
So it could be something else.
This guy fixed the problem with the nvidia driver:
[http://newyork.ubuntuforums.org/showthread.php?p=8205195](http://newyork.ubuntuforums.org/showthread.php?p=8205195)
If I find anything else I will post it here.
BTW, this is a risk you take when using third party repositories with Ubuntu, especially before doing a dist-upgrade. You should have installed XBMC after the upgrade. I would not shut down the computer with XBMC again.
BTW #2: XBMC has caused other problems as reported here:
[http://ubuntuforums.org/showthread.php?t=1358120](http://ubuntuforums.org/showthread.php?t=1358120)
I would not use it.

And welcome to the Ubuntu forums!

---

### Post by maartmeester on 2009-12-23
Djeez, that was really simple... All I did was (re-?) install gdm through the Synaptic Package Manager, reboot and the problem was solved! Wow! Excellent! Thanks a bunch, Tom!

And I'll pay more attention to those third party apps in the future... :oops:

---

### Post by tommcd on 2009-12-23
> **maartmeester said:**
> Djeez, that was really simple...
Well, that is just totally excellent! Glad it was a simple fix.
I was not sure what exactly the problem was. I just made a semi-educated guess based on the info I could find with a search. I was afraid this would be one of those threads that no one else responds to; and I was pretty much out of ideas on this one. I'm glad you got it fixed.

---

