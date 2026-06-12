---
title: "How do I smoothly upgrade from EOL?"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by michwill on 2011-06-19
Hi All,

I'm looking to bring several 9.04 systems up to 11.04.  I have tried following the tutorial here:
[https://help.ubuntu.com/community/EOLUpgrades/Jaunty]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty")

Everything seemed to go fine, but after I restarted, it was still on 9.04.  I'm not sure where to go from here.  All but one of the servers is running Ubuntu Server (i.e. no desktop GUI) so I'll still need a command line solution (which is preferable anyway).

Thanks in advance.

---

### Post by dFlyer on 2011-06-19
I may be wrong but you will need to upgrade using an install cd. Unless things changed only LTS can be upgraded with out a fresh install, unless you install each versions. IE 9.04 > 9.10 > 10.04 > 10.10 > 11.04.

---

### Post by michwill on 2011-06-19
I'm ok with each step.  In fact, that's what I was attempting by following that path in the "tutorial".  However it doesn't seem to work for me -- and I have no idea why.  

I was attempting to go from 9.04 to 9.10, and while it initially looked like that happened, a restart showed otherwise.  I'm still on 9.04  =\

Any thoughts?

---

### Post by snowpine on 2011-06-19
What criteria are you using to determine "I'm still on 9.04"?

---

### Post by michwill on 2011-06-19
> **snowpine said:**
> What criteria are you using to determine "I'm still on 9.04"?


Well, on this particular go-round I'm actually using the GUI-based install so I have access to both the ABOUT as well as "lsb_release -a".  Both are telling me I'm still on Jaunty.  One question, when following the tutorial, should I be changing the source to the next release instead of leaving it on the current?  So, for example, when going from 9.04 to 9.10 should I be using:


```
# EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu/ karmic-proposed main restricted universe multiverse

```

...instead of:

```
 # EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

```

?

---

### Post by snowpine on 2011-06-19
That's one way to do it. Debian users do it that way all the time, but for some reason it is not the recommended method for Ubuntu. YMMV. :)

---

### Post by michwill on 2011-06-19
> **snowpine said:**
> That's one way to do it. Debian users do it that way all the time, but for some reason it is not the recommended method for Ubuntu. YMMV. :)

Fair enough.  I just want to be sure.  I installed these servers as static file servers two years ago.  Over time they've come to host a couple of websites, etc. and the owner wants them blindly (as in he gives no reason other than "I want the newest!") updated to the most recent versions.

That said, I don't want to break anything major or have a crippled update occur.  Obviously worst case, upon failure, I could simply copy the "www" directories and reinstall.  I simply am not getting paid enough to do it all over again.  :P

Thanks again.   Keep the ideas coming as I still have 4 more opportunities to mess things up.  [-o<

---

### Post by michwill on 2011-06-20
Actually, changing "Jaunty" to "Karmic" failed as well. =\  Am I going to have to DL all old releases and upgrade from CD?   If so, can I use the same "Alternate Install" disc for server and gui alike or do I need to make CDs for both versions of each release?

---

