---
title: "DOSEMU Downgrade"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by jamillikan on 2008-03-21
Could someone please advise how to install DOSEMU 1.2.2, xfonts-dosemu, and dosemu-freedos from Feisty in Gutsy? 

The Gutsy version does not play well with my specific business software application for whatever reason.

Thanks,

---

### Post by jamillikan on 2008-03-25
Still waiting for an answer.  Anyone?

Thanks,

Joe

---

### Post by jamillikan on 2008-03-29
Does anyone read these posts?  Is there a solution here?

Thanks!

---

### Post by xernos on 2008-05-21
Hi 
I suggest you tray first uninstall actually version  dosemu:
[COLOR="Green"]apt-get remove dosemu[/COLOR]
And install correct version dosemu :
[COLOR="Green"]apt-get install dosemu=1.2.2-x[/COLOR]
Of course you must have in repository with 1.2.2-x for example with 1.2.2-8 from Fiesty  in your  /etc/apt/sources.list.
Don't forget update package base using command :
[COLOR="Green"]apt-get update[/COLOR]
This command show you available versions in your system:
[COLOR="Green"]apt-cache showpkg dosemu[/COLOR]

Bay

---

