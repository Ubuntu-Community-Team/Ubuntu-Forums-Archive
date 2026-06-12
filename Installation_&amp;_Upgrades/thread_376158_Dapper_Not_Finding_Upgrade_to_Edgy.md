---
title: "Dapper Not Finding Upgrade to Edgy?"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by TehVague on 2007-03-04
I just installed Dapper Drake last night on my PC and I looked up ways to do the upgrade from Dapper to Edgy Eft but when I go to my terminal and type in the stuff for the update manager that I've seen posted everywhere on this site and on google it just comes up saying that there are no updates. I don't get the update for 6.10.

Any suggestions? I would really like 6.10.

---

### Post by taurus on 2007-03-04
What command(s) did you run from a terminal anyway?

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by TehVague on 2007-03-04
I did

gksu "update-manager -c"

---

### Post by bryak on 2007-03-04
I think it might be a server end issue.

I just decided to make the upgrade and am having the exact same issue.  After a few minutes of frustration and googling, I found my way here.  I'll be watching.

---

### Post by taurus on 2007-03-04
Since it's a newly installed, why not install Edgy directly from a CD since upgrading from Dapper to Edgy sometimes breaks your machine.  That's probably the best solution and saves you a lot of headaches too.

---

### Post by TehVague on 2007-03-04
Because for some reason everytime I've tried burning my own copy of Edgy it messes up on the computer. I don't know why either. And it's not just this computer, I've tested it on my primary machine and my parents machine, my brothers and this one. It wouldn't work on any of them.

---

### Post by taurus on 2007-03-04
Here's a guide on how to download, run checksum, and burn to a CD.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by TehVague on 2007-03-04
My PC isn't working at the moment so I kind of just have to do the dl update. Either way, why isn't it working for me?

Is there actually some kind of server down like bryak said?

---

### Post by bryak on 2007-03-04
[looks like it's not just us.]("http://www.ubuntuforums.org/showthread.php?t=375226&highlight=edgy+upgrade")

---

### Post by TehVague on 2007-03-04
I got mine resolved. I did just as he did and it's upgrading as I'm typing this.

I had a 6.10 CD but whenever I boot from it, it wouldn't work, now that this is upgrading I'm very excited, and very relieved.

Thanks Bryak for sending that link it just made my day.

---

### Post by TehVague on 2007-03-04
I wanted to post one more time just to confirm that Edgy Eft is working.

Thanks

---

### Post by oldHat on 2008-02-20
Me too.

When I type "gksu update-manager -c", it starts the gui and informs me that my system is up to date.

I click "check", it goes through a cycle of "downloading package information", then again tells me again that my system is up to date.

At no point in this cycle am I given the option to upgrade.  The only options on the GUI are HELP, CHECK and CLOSE.

"lsb_release -a"  shows that I am running 6.06.2 LTS

Has a solution been found yet?  I hope that longterm support for 6.06 includes an upgrade path for the end of its lifecycle.

---

### Post by Partyboi2 on 2008-02-20
> **oldHat said:**
> Me too.

When I type "gksu update-manager -c", it starts the gui and informs me that my system is up to date.

I click "check", it goes through a cycle of "downloading package information", then again tells me again that my system is up to date.

At no point in this cycle am I given the option to upgrade.  The only options on the GUI are HELP, CHECK and CLOSE.

"lsb_release -a"  shows that I am running 6.06.2 LTS

Has a solution been found yet?  I hope that longterm support for 6.06 includes an upgrade path for the end of its lifecycle.
[here]("http://ubuntuforums.org/showthread.php?t=695700") is some info

---

