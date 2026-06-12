---
title: "Cannot remove boot splash/graphics mode"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by mabra on 2012-10-28
Hello !

I've just installed ubuntu 12.04 (LTS) server.
I immidiately added LXDE.
What I am getting after the grub(2) boot-menu, is completely
hiden to me, it is just behind a purple graph, with prevents
me to see the log. ON a server, I think, this should really NEVER
happen.

This evening, I tried to remove this, but no success.
I've read and follows this steps:

[http://ubuntuforums.org/showthread.php?t=1997199&highlight=remove+purple+screen](http://ubuntuforums.org/showthread.php?t=1997199&highlight=remove+purple+screen)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/761830)

This looks like a bug. Even if I go to the configuration, as
described and update-grub, it does not disappear. To the hell,
it looks like, that someone else is fumbling this settings in
a - probably (?) - hiden manner.

I found this package: 'plymouth'.
[Called "graphical boot and animation logger"].
This may be fine on a desktop [If users can accepts, to
not see errors]. For me, coming over from debian, this
looks strange and wrong.

And 'plymouth' is not a standalone package and cannot be removed:

root@ubu12:~# apt-get remove plymouth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[COLOR=Red]The following packages have unmet dependencies:
 upstart : Depends: initscripts
           Depends: mountall
           Depends: ifupdown (>= 0.6.10ubuntu5)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.[/COLOR]

Probably someone is in the same situation and give me a tip??
It sounds strange to me, to put a 'market-symbol' that deep into
the dependency chain. Where I am stranded now??

Thanks anyway.

br,
++mabra

---

