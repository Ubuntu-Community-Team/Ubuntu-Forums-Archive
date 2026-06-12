---
title: "apt-get install- package not found &gt; emacs?"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2011-08-07
Re: Ubuntu Server Edition, 32bit, fresh install today (2011.07.07).

Usually th first thing thing I do after a server install, I update, upgrade... then install Emacs to configure services...

I can get to it from my other servers and PC's, have an internet connections from that server // so I know things should be okay...

I'm thinking maybe it's a repo problem in my source list... and I'm not sure what repo Emacs is from.  I'd like to check this, before doing a reinstall on this.   I had just added in the mounts & fstabs on my data RAID arays... Would be more work, but still not too far into it. 

I would say it's just a convient, but it points out that there "is" a problem somewhere and I don't want it to bite me later down the road.

Can anyone help with this?

---

### Post by oldos2er on 2011-08-07
Which version of Ubuntu are you using?

---

### Post by MAFoElffen on 2011-08-07
> **oldos2er said:**
> Which version of Ubuntu are you using?
11.04 32bit on this server... But holding pattern on that version for a couple days before going 11.10 for dev tests. Mobo HP (asus) LRT-LS Server Board...

---

### Post by MAFoElffen on 2011-08-07
Solved-- 

unmounted RAID arrays > reinstalled server fresh > 
```

sudo apt-get update
apt-get install emacs
apt-get upgrade

```
Everything went well.

---

