---
title: "[SOLVED] make own repository"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by xyrer on 2007-02-26
Hi, i want to install ubuntu on some user desktops in my company but i don't want them all to download all the upgrades over and over, is there a way to share the upgrades from a central server so when the server gets upgraded the desktops can obtain them from a local repository?

Thanks.

---

### Post by MontanaMax on 2007-02-26
Yes, it's possible - I've seen an article on this recently that I'm having trouble locating for your at the moment, but there is a lot of information about setting up personal or local repositories on the Ubuntu wiki over here:

[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

The general strategy is to setup a local repository per this idea:

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

And then put packages into that for local sharing.

I think there is a slicker way to setup a full local mirror however, and as soon as I can find it again I'll post it for you.

Good luck!

---

### Post by nyinge on 2007-02-26
I've also heard good things about apt-proxy.  You can further read about it [here]("http://apt-proxy.sourceforge.net/").

---

### Post by Horza on 2007-02-26
Oops, this doesn't answer the question posed, I can't find a delete post button so
I put the confession of irrelevance at the top


I've been using APTonCD for more or less this purpose.  The technique I use is:

  install APTonCD
  put a copy of the APTonCD .deb installation file in the apt cache if you didn't
    install it with apt-get (for Dapper, you need a special version isn't available
    via apt-get) - this is supposed to be fixed soon)
  APTonCD Create
    this makes a CD repository of everything in the apt cache, including APTonCd itself

Then on the machine you want to update:

  enable unauthenticated repositories
  add the APTonCD repository CD in synaptic
  install the 'aptoncd metapackage' (installs all new packages on the original
    machine)
  install the updates that become available (from the original machine)
  disenable unauthenticated repositories

I hope I haven't left out or misdescribed any step, I'm quite nOObish as far as linux is concerned.

I haven't tested 'cumulativelty' for this, that is, install some more new stuff on the original machine, make a new aptoncd repository (which would contain everything in the original APTonCd repository, plus the new stuff), and then update the other machines from that.

---

### Post by xyrer on 2007-02-28
apt-proxy looks promising and seems to be exactly what i want, thank you very much for the various answers. I'll try it and tell you how it goes.

---

### Post by bazzer on 2007-03-19
Hi - any words of how you got on? I'm thinking of implementing a similar system this week...
edit: I've done it, it's a piece of proverbial....! :)

---

### Post by xyrer on 2007-03-20
Yep, it actually works perfect with apt-proxy so far, I found this: [apt-proxy howto]("https://help.ubuntu.com/community/AptProxy?action=show&redirect=AptProxyHowTo")

---

