---
title: "gnome-keyring-daemon not working with 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by peter.van.heusden on 2010-05-02
Since I've upgraded to Ubuntu 10.04 my gnome-keyring-daemon isn't  working on login. It is running - ps ax shows:

 4927 ?         SLl    0:00 /usr/bin/gnome-keyring-daemon --daemonize

but it  doesn't seem to be accessible. Seahorse says: "Couldn't communicate with  key ring daemon", and I never get asked to unlock my keyring on login  (thus saved wireless keys are not available, for example). If I kill the  gnome-keyring-daemon process and run it again from the command line,  everything works. There are not messages in /var/log/messages from the  keyring daemon, so i don't know what it is doing wrong. Has anyone else  seen a problem similar to this?

Thanks,
Peter

---

### Post by LunarEffect on 2010-05-02
Yes, same problem here. The keyring seems to work fine under GNOME, its only when I switch to openbox that I get this problem.

---

### Post by peter.van.heusden on 2010-05-02
> **LunarEffect said:**
> Yes, same problem here. The keyring seems to work fine under GNOME, its only when I switch to openbox that I get this problem.

I don't think this is the same problem. If you switch to openbox I presume you're not using the gnome-session manage and gnome-keyring-daemon is not started. My problem happens with GNOME, with gnome-keyring-daemon started but not responsive.

---

### Post by LunarEffect on 2010-05-02
> **peter.van.heusden said:**
> I don't think this is the same problem. If you switch to openbox I presume you're not using the gnome-session manage and gnome-keyring-daemon is not started. My problem happens with GNOME, with gnome-keyring-daemon started but not responsive.

Well it was similar enough. Seahorse was giving me the same message and "ps ax" gave me the same message as you. I got it fixed though, I added gnome-keyring-daemon to my autostart.sh and it works fine. Maybe you could do the same with your gnome equivalent :)

---

### Post by peter.van.heusden on 2010-05-02
I've found the source of this, its related to this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338) Basically gnome-keyring-daemon unlocks the keyring if my keyring password is the same as the user login password, but doesn't pop up a dialogue box to ask me for my password if they are different.

---

### Post by ikkarus on 2010-05-20
i think that problem is the same i have. the gnome-keyring dont run... i try gnome-keyring-daemon --start, but still the same. the seahorse and mysql workbench show problems because the keyring-daemon dont work, i try to reinstall but nothing... some help please! :(
hugs for all!

---

### Post by jbruni on 2010-05-25
Hi, guys,

I am here because MySQL Workbench complained: "**Error  communicating with gnome-keyring-daemon**"

After doing  some research, I found that this issue is new from **Lucid Lynx**,  and affects lots of software, like Evolution, Empathy, Gwibber,  Seahorse, Network Manager, and much more, as you can figure out from  this search results:
[http://ubuntuforums.org/search.php?searchid=73323038](http://ubuntuforums.org/search.php?searchid=73323038)

More  search results:
[http://www.google.com/search?q=+site:ubuntuforums.org+Error+communicating+with+gnome-keyring-daemon](http://www.google.com/search?q=+site:ubuntuforums.org+Error+communicating+with+gnome-keyring-daemon)
[http://www.google.com/search?q=+site:bugs.launchpad.net+Error+communicating+with+gnome-keyring-daemon](http://www.google.com/search?q=+site:bugs.launchpad.net+Error+communicating+with+gnome-keyring-daemon)

Some  threads provides additional information:
[http://ubuntuforums.org/showthread.php?t=1443896](http://ubuntuforums.org/showthread.php?t=1443896)
[http://ubuntuforums.org/showthread.php?t=1459804](http://ubuntuforums.org/showthread.php?t=1459804)
[http://ubuntuforums.org/showthread.php?t=1462055](http://ubuntuforums.org/showthread.php?t=1462055)

And  we also have several related launchpad bug reports:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/529338)
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/553032](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/553032)
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667)
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/573387](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/573387)

So,  we have a lot of trouble and a lot of information... we can easily get  confused! 

The most comprehensive and useful piece of information  i found was this:
[SIZE=3][COLOR=DarkOrchid]**[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667/comments/18](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/569667/comments/18)**[/COLOR][/SIZE]

So,  forget all the other links! ;-)

I will try to translate what I  learned so far:

[COLOR=Red][COLOR=Sienna]1) [/COLOR]gnome-keyring-daemon[/COLOR]  [COLOR=Sienna]is a piece of software that works like a "safe  password database" for other applications to use[/COLOR]

[COLOR=Sienna]2) other applications access it through [/COLOR][COLOR=Red]libgnome-keyring[/COLOR]



[COLOR=Sienna]3) recent changes on [COLOR=Red]libgnome-keyring[/COLOR]  made it unable to find [COLOR=Red]gnome-keyring-daemon[/COLOR]  through "*environment variables*", but only through "**[COLOR=Red]*dbus*[/COLOR]**"[/COLOR]



[COLOR=Sienna]4) in order to [COLOR=Red]dbus[/COLOR] be able to  find [/COLOR][COLOR=Sienna][COLOR=Red]gnome-keyring-daemon[/COLOR]  it must be started BEFORE[/COLOR]
[COLOR=Sienna]
[/COLOR]
[COLOR=Sienna]5) on system start up, [COLOR=Red]dbus[/COLOR] is  started AFTER [COLOR=Red]gnome-keyring-daemon[/COLOR] 
[/COLOR]
[COLOR=Sienna]
[/COLOR]
[COLOR=Sienna]6) so: no  application which uses [COLOR=Red]libgnome-keyring[/COLOR] can  access [COLOR=Red]gnome-keyring-daemon[/COLOR] because [COLOR=Red]dbus[/COLOR] can't see it[/COLOR]
[COLOR=Sienna]
[/COLOR]
[B]SOLUTION?
[/B]


Well...  it seems that we just need to swap start-up order of [COLOR=Red]gnome-keyring-daemon[/COLOR]  and [COLOR=Red]dbus[/COLOR]...


How? I don't  know. I will continue research. Meanwhile, someone who knows can post  the answer here.


Thanks!

---

### Post by jbruni on 2010-05-25
Among the lots of links from my previous post, I have found this bug report very useful:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/573387](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/573387)

It points useful places:
[B]
/etc/xdg/autostart[/B]
probably where we need to apply the swap-start-order fix (I guess)

**/var/log/auth.log**
where we can check if this bug really affects us

---

### Post by ronaldv on 2010-06-01
Hi,

I had the same problem (in 10.04) and solved it via this post: [http://codept.blogspot.com/2010/05/ubuntu-1004-lucid-lynx-on-hp-mini-5101.html](http://codept.blogspot.com/2010/05/ubuntu-1004-lucid-lynx-on-hp-mini-5101.html)

I think it is a very strange solution but at leats it works.

And then I want to make this remark: it really worries my that a problem that sounds so common to me still exists in a Ubuntu release, 1 month after it first release (mind you, an LTS-release). Why does it take so long to fix this? Are we the only users who have this problem? Why is Mark Shuttleworth not on top of this? Why is nobody from the Ubuntu-organisation picking up on this? If Linux/Ubuntu ever want to become a mainstream-thingy it is things like this that must improve first. Nevertheless, I'm still an Ubuntu believer!

Cheers.

---

### Post by ElijahLynn on 2012-08-23
Happening to me on 12.04. Keyring stops prompting for password to unlock ssh keys. Cannot SSH because of it.

Basically posting here so when I find a fix I can come back and post since it is related.

---

