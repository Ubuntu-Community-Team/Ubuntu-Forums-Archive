---
title: "[SOLVED] Modprobe Usage error on boot"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by blink0 on 2008-09-09
Hello there!
It's my first post here, so sorry if there's something wrong with it. I have been using Linux for some time, but I am not so "fluent" in it, when it comes down to the more technical details (like the problem I am about to describe).
I have the same problem as this guys here:

[http://ubuntuforums.org/showthread.php?t=212777](http://ubuntuforums.org/showthread.php?t=212777)

So, my problem started when some guy was upgrading something (I think Matlab) on the computer, and that caused some problems. When I rebooted the machine, I got a lot of modprobe errors (basically it only says "usage: modprobe -l <example> -i <example2>" like I had typed in an incorrect usage for modprobe) which go on for some minutes, after which it says "ALERT! /dev/sda1 does not exist. Dropping to a shell!" and runs the BusyBox Built-in shell.
I have been consulting some friends who know a bit more than I do, and the problem seems to be on the disk module (or the module that provides access to the disk). That's why it complains about /dev/sda1 not existing and that's why I can't boot the computer at all (access to the disk is quite important, eh?).
I have physical access to the computer and I can use a fancy Live CD to get inside, I just don't know what to do after that...
It's a Ubuntu 6.06 on a fancy HP server rack-shaped (I can get you a more detailed model information on the server in some hours, when I get there).
Could I get a little work on this one? It's an important server which I am responsible for :-(
Thanks in advance!!
Daniel

---

### Post by blink0 on 2008-09-11
Well, I re-installed the whole system, so the problem's solved.
Just so that all the nice people out there who were just about to help me don't waste their time ;-)

---

