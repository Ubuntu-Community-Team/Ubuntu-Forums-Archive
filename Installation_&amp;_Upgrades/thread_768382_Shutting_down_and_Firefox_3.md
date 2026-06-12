---
title: "Shutting down and Firefox 3"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by alligoodw on 2008-04-26
I've upgrade from 7.10 to 8.4. I'm using a Sony Vaio laptop.

Just a couple of things I've noticed here.  One, when I shut the system down, the shutdown process hangs for about 60 seconds while running local boot scripts.  Two, there is a lot of hard drive activity going on while using Firefox 3.  So much so, that it slows Firefox down.  Sometimes Firefox will gray out and in and at other times it just hangs for a couple of seconds.  

Does anyone have a clue what's going on?

---

### Post by Devi 710 on 2008-04-26
I am having the same issue at shutdown with the boot scripts. It is followed by a message that something failed. It doesn't happen every time, just most of them.

As for Firefox 3, I can't install the cool plugins and themes that I like because they are not ready for FF3 yet. And when I install the older Firefox 2, it won't let me install any themes or plugins, even if I get rid of FF3 through synaptic.

No issues like you have though. FF3 is pretty fast for me actually.

---

### Post by Theo148 on 2008-04-26
The high memory usage when using Firefox 3 is due to a new implementation of the phishing/malicious website filter or something like that. There's more information on this thread:

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

---

### Post by alligoodw on 2008-04-26
> **Theo148 said:**
> The high memory usage when using Firefox 3 is due to a new implementation of the phishing/malicious website filter or something like that. There's more information on this thread:

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

After reading the above mention posts, I did the following and it worked.

In Firefox, I went to Preferences/Security and deselected the following two items:

Tell me if the site I'm visiting is a suspected attack site.
Tell me if the site I'm visiting is a suspected forgery.

Once I deselected these two items, I discovered that the hard disk thrashing stopped.  

Now to correct the shut down hanging problem.

---

### Post by arm-c on 2008-04-27
Good notes about the new Firefox Filters.

I too am having a problem with shutdown.  It always hangs and the only way I get it to proceed is a CTRL-ALT-Backspace and then shutdown proceeds.

I do notice that on my 8th terminal (CTRL-ALT-F8), I see the following note:

"mount.nfs:  internal error"

Any assistance regarding this will be greatly appreciated.

---

### Post by timebomb on 2008-04-28
Bump: I'm seeing something similar in that it is hanging on shutdown.

Thanks.

---

### Post by FuturePilot on 2008-04-28
I have the same issue with shutdown. I've looked deeper into the matter and it's not hanging on running on Running Local Boot scripts. That's left over from startup. It's actually hanging on "Shutting Down Gnome Display Manager". It seems to be a problem with GDM. There's a bug here
[https://bugs.launchpad.net/bugs/221525]("https://bugs.launchpad.net/bugs/221525")
but it seems to have been mistakenly marked as a duplicate of another non-related bug. :(
Also I've noticed in my logs
```
Apr 24 03:50:13 P3nguins gdm[5413]: WARNING: main daemon: Got SIGABRT. Something went very wrong. Going down! 
```
That happenes on shutdown.

---

