---
title: "[SOLVED] Anyone knows how to help me on this....?"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by r_l on 2007-08-25
Hi, 

I use [_**[COLOR="Sienna"]Ubuntuzilla[/COLOR]**_]("http://ubuntuzilla.wiki.sourceforge.net/") to install the lastest Thunderbird 2.  However, my Ubuntu update manager keep popping up to ask me to install a security update for Thunderbird 1.5012.   

I *think* I should ignore it (or should I?)  If I should, is there a way to tell the Update manager that I do not want to update this particular package and stop bugging me with that notification icon? - and best to exclude this package so I won't accidentally select it with the others to update next time.

Thanks in advance.


[Update] I got an answer from launchpad: 
[https://answers.launchpad.net/update-manager/+question/12154]("https://answers.launchpad.net/update-manager/+question/12154")

RL

---

### Post by Warren Watts on 2007-08-25
I am having the same problem:
[http://ubuntuforums.org/showthread.php?t=529491]("http://ubuntuforums.org/showthread.php?t=529491")

And so is this guy:
[http://ubuntuforums.org/showthread.php?t=529235]("http://ubuntuforums.org/showthread.php?t=529235")

So far, no one has offered any help....

---

### Post by r_l on 2007-08-25
Then bump

---

### Post by r_l on 2007-08-25
Ok, I checked my synaptic packages on Thunderbird and all the packages say 1.5++, while my the about Tab in my Thunderbird say 2.0.0.6.  What should I make of this?

---

### Post by merlinus on 2007-08-25
That is because Thunderbird 1.5++ is the latest version in the ubuntu repositories, and so the updates are for that version.

Version 2 has not yet been listed.

How did you install it?

-merlin

---

### Post by r_l on 2007-08-25
> **merlinus said:**
> That is because Thunderbird 1.5++ is the latest version in the ubuntu repositories, and so the updates are for that version.

Version 2 has not yet been listed.

How did you install it?

-merlin

I use Ubuntuzilla, see 

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)[http://ubuntuzilla.wiki.sourceforge.net/]("http://ubuntuzilla.wiki.sourceforge.net/")

---

### Post by merlinus on 2007-08-25
Two choices.  Ignore the updates, or revert to version 1.5xx until 2 hits the ubuntu repos.

-merlin

---

### Post by r_l on 2007-08-25
Thanks for the reply.
I only wish the updater has an option to let the user to choose to ignore a particular package and don't show it again.  I guess this is not possible at least for now, but I think it is a good feature to have as sometimes there is a need for that.

---

### Post by merlinus on 2007-08-25
I completely agree!

-merlin

---

### Post by nanotube on 2007-08-26
> **r_l said:**
> Hi, 

I use [_**[COLOR="Sienna"]Ubuntuzilla[/COLOR]**_]("http://ubuntuzilla.wiki.sourceforge.net/") to install the lastest Thunderbird 2.  However, my Ubuntu update manager keep popping up to ask me to install a security update for Thunderbird 1.5012.   

I *think* I should ignore it (or should I?)  If I should, is there a way to tell the Update manager that I do not want to update this particular package and stop bugging me with that notification icon? - and best to exclude this package so I won't accidentally select it with the others to update next time.

Thanks in advance.


[Update] I got an answer from launchpad: 
[https://answers.launchpad.net/update-manager/+question/12154]("https://answers.launchpad.net/update-manager/+question/12154")

RL

just to be clear, you don't need to uninstall tbird 1.5 (as the launchpad link recommends), you can just let the updater do its thing. it won't affect your tb2 installed with ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/#tochome18](http://ubuntuzilla.wiki.sourceforge.net/#tochome18)

---

### Post by r_l on 2007-08-26
> **nanotube said:**
> just to be clear, you don't need to uninstall tbird 1.5 (as the launchpad link recommends), you can just let the updater do its thing. it won't affect your tb2 installed with ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/#tochome18](http://ubuntuzilla.wiki.sourceforge.net/#tochome18)

Thanks for the clarification!  It is a nice design that way, although I uninstalled the old version anyway for the free disk space.

---

