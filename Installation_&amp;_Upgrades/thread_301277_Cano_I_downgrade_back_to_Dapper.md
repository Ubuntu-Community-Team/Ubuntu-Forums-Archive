---
title: "Cano I downgrade back to Dapper"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by zergberg on 2006-11-16
I've discovered that Edgy doesn't really support my video card (along with screwing up my mouse) and I think I'd like to go back. Is there any way I can do this short of a reinstall? And if not, how much as far as configuration settings will I lose if I do reinstall (/home is on a separate partition.)

-o in title. Oops. Good job, Firefox 2 spellcheck!

---

### Post by pay on 2006-11-16
You shouldn't lose anything (confuration wise not program wise) if you reinstall with /home on its own partition. I don't believe you can downgrade.

---

### Post by Joe_CoT on 2006-11-16
There isn't much point in downgrading, and it's night impossible, sorry. If your /home partition is on a separate partition, you should be able to keep most settings, but if you did custom stuff in your system internals (xorg.conf, apache settings, ssh settings, you get the idea) those won't be saved unless you back up all those config files.


Is a downgrade really necessary? what problems are you having with the video card?

---

### Post by zergberg on 2006-11-16
Also, I have dialup, so I really don't want to redownload everything. Is there a directory I can copy somewhere in order to preserve my acquired packages?

---

### Post by Joe_CoT on 2006-11-16
/var/cache/apt/archives has all cached package files. however, most of those are probably edgy packages now, so that won't help you

If you can explain what doesn't work in edgy, we can try to help

---

### Post by pay on 2006-11-16
Yeah. /var/cache/apt/archives

---

### Post by zergberg on 2006-11-16
I have a 3dfx card, and it makes X crash. The only listed workaround is to use VESA, but my gamma is messed up so that's not an option.

---

### Post by Joe_CoT on 2006-11-16
It's fixable
[http://www.ubuntuforums.org/showthread.php?t=292580&page=2](http://www.ubuntuforums.org/showthread.php?t=292580&page=2)

what it means (for now) is getting the source, applying the patch, and compiling it and checkinstall-ing it. is it pretty? no, but you won't need to reinstall dapper

You can get the source with:

```
apt-get source xserver-xorg-video-tdfx
```

apply the patch linked to in that thread, then compile and checkinstall it. You might want to just ask that mooglie guy for the deb

---

### Post by zergberg on 2006-11-17
Arrgh... I just read that AFTER reinstalling Dapper...

---

### Post by Joe_CoT on 2006-11-17
> Arrgh... I just read that AFTER reinstalling Dapper...

Sorry chief. There's a reason I wasn't just saying to go off and reinstall ;)

Almost every critical problem in Edgy Eft has a solution. It's not like Dapper's going to be the last version you can ever use.

---

### Post by ghoran on 2007-04-15
I have the same configuration issue.
I am currently running on Mepis 3.3
I have burned UBUNTU 6.10 but, am having weird video issues.
I have that voodoo3 card in this machine.
I am new to Linux as a desktop. I do have Linux servers I use at work.
To accomplish this update I believe I need to come up in safe mode and then 
 apt-get source ....

---

### Post by Neobuntu on 2007-04-15
Since darn near anything can be done, it's important to know what wastes time and what doesn't.

One must exercise a much greater constraint; with open software because you can run the testing stuff if you wish. Confusing the issue, sometimes the testing tiers work just great. Guess what then happens?

The problem is we all want open software to get better. It is and getting more so very fast. Faster than anything. So we want the new stuff.

So, this leads to two installs. 

One for your "main" system and where you would NEVER upgrade to a beta/testing version. Yet, also *ubuntu has introduced the LTS idea. Where Edgy is released but it is not LTS (Long term service).  Neither will Fiesty be. So, (for your main system) there is a quandary.  Do you stay with Dapper and keep Dapper upgraded and perhaps with some limited backports or do you RISK Edgy. See now, Edgy is largely stabilized and about to become the "old" release but that doesn't mean everything works as well as Dapper. Here, "works" is a relative term. Even if you're not running just a server, Dapper not only functions generally well, without major bugs and in major areas but it is more what you might call "built-out", in various areas. That is, when using everything that you personally, want to use. If you want "everything" to work (by in large) then stay with Dapper.

Two, the thing is, if most people do not try the testing versions, then guess what? They come out of the gate in much less a ready a state. This is why, for your main install (One above), you should seriously consider only a release thats not only officially past it's release candidate, but well past it and improved at large (and LTS). So here, a second partition and install should be for your testing SEPERATELY.

As much as I like the idea of (manager/dist)upgrading, and as close as *ubuntu comes to perfection on OLDER versions (only older releases and by one step at a time) one can not currently beat a "clean" and fresh install. Even with backing up and reinstalling your /home directory, you save TIME and get a better, CLEAN system.

1. Never upgrade your main system unless the next version has long been out and the (manager/dist)upgrader is long tested. Duplicate your main version first(and keep it), in order to test the (manager/dist)upgrading process.

2. Clean installs are generally better.

3. Don't dist-upgrade to test (unless you are testing a dist type upgrade separately).

4. Be patient.

---

### Post by ghoran on 2007-04-17
I don't mean to be a pain but, I think we all got sidetracked. I don't think I got an answer.
Thanks
Gary

> **ghoran said:**
> I have the same configuration issue.
I am currently running on Mepis 3.3
I have burned UBUNTU 6.10 but, am having weird video issues.
I have that voodoo3 card in this machine.
I am new to Linux as a desktop. I do have Linux servers I use at work.
To accomplish this update I believe I need to come up in safe mode and then 
 apt-get source ....

---

