---
title: "Do Not Even Think Of Upgrading to 6.10 from a working installation!"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by psanta on 2006-11-04
Hi Folks.

UBUNTU is definitely GREAT.

But DO NOT EVEN THINK OF UPGRADING to 6.10 version from 6.04!

I followed the "official upgrade instructions":

$ gksu "update-manager -c"

in order to upgrade my working copy of UBUNTU 6.04 (which I previously greatly upgraded from 5.10 with the same technique), and the upgrading could not finished and showed a bunch of errors.

Now, I can't boot my LINUX box AGAIN!

It is completely USELESS.

I will have to mount the hard disk into another linux BOX to make a backup, and then, reinstall everything from SCRATCH.

So, if you are a serious DESKTOP LINUX USER (using Linux for everyday work) think ten times before trying the "suggested" ubuntu upgrade method.

If you are reading this, I hope is not too late...

Best regards.

](*,) :confused: ](*,) :confused:

---

### Post by psanta on 2006-11-04
Sorry. A TYPO. I meant DO NOT UPGRADE FROM 6.06.

---

### Post by NeoLithium on 2006-11-04
Some people I guess, don't have luck; I followed the same method from my Dapper, and everything went smoothly; restarted after the upgrade, never lost a file; or anything.

---

### Post by Drezliok on 2006-11-04
> **psanta said:**
> Hi Folks.

UBUNTU is definitely GREAT.

But DO NOT EVEN THINK OF UPGRADING to 6.10 version from 6.04!

I followed the "official upgrade instructions":

$ gksu "update-manager -c"

in order to upgrade my working copy of UBUNTU 6.04 (which I previously greatly upgraded from 5.10 with the same technique), and the upgrading could not finished and showed a bunch of errors.

Now, I can't boot my LINUX box AGAIN!

It is completely USELESS.

I will have to mount the hard disk into another linux BOX to make a backup, and then, reinstall everything from SCRATCH.

So, if you are a serious DESKTOP LINUX USER (using Linux for everyday work) think ten times before trying the "suggested" ubuntu upgrade method.

If you are reading this, I hope is not too late...

Best regards.

](*,) :confused: ](*,) :confused:

I've read thatif you automated scripts and the "easy" way of setting up things. Like Automatix? {sp?} You can break your system for upgrades.

I had only 1 probelm when I updated. I use the update prog when I wasn't supposed to as a Xubuntu user. Apt-get told me what command to use to fix it anyways so all is right with my Ubuntu.

You must have changed something that might have broke your system.

---

### Post by Sirin on 2006-11-04
The update manager is not an efficient way to upgrade at this time, as there currently are problems when it comes to upgrading to a new distro. It killed my previous Ubuntu installation (rip :(). After that, I decided to experiment and try some other ways. I tried to upgrade via Synaptic, works like a charm (I'm typing this on Edgy, which I successfully upgraded from Dapper using Synaptic. :) ).

Try editing your sources.list (if you don't know where this is, it is in /etc/apt/sources.list), changing every instance of the word "dapper" to "edgy", start up synaptic, click on the reload button, after that, go into Custom Filters > Upgradeable (Upstream), and mark every upgrade in there (using Ctrl-A). Then click Apply, and let the upgrading magic begin. :)

You can also do this using apt-get in the terminal. Edit your sources.list to edgy repos, and typing in the terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Hope this helps. :)

---

### Post by Drezliok on 2006-11-04
If you going to do that and you have custom repos in there, comment them out so they can't mess with the upgrade.

Uncomment afterwards and apt-get update and upgrade away.

---

### Post by yalding on 2006-11-04
I assume you have ATI graphics card.

I think ATI should donate some cards to ubuntu team. Next time, they will not mess ATI users up..

I agree that upgrading a working machine from 6.06 is a bad idea. I have to do a fresh dapper install because I could not figure out how to fix the upgrads in 24 hours and I have to work after the weekend.

---

