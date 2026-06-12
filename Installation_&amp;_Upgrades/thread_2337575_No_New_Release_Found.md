---
title: "No New Release Found ???"
date: 2016-09-19
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-09-19
Have Xubuntu v14.04 installed a HP Elitebook 6930, and recently saw an Upgrade to v16.04 is available. Chose not to at that time.

Today I ran the following in terminal;

```
lsb_release -a

```

Shows, "Ubuntu 14.04 LTS Trusty".
So then I ran ...

```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get dist-upgrade
sudo do-release-upgrade

```

And received - 
"Check for new Ubuntu release ... No new release found"

That is strange ... What am I missing ? ? ?

:confused:

---

### Post by #&amp;thj^% on 2016-09-19
Have you tried this yet?
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
let us know..

---

### Post by Rick St. George on 2016-09-19
> **1fallen said:**
> Have you tried this yet?
```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```
let us know..

I get - "update manager core is already newest version".

---

### Post by #&amp;thj^% on 2016-09-19
> **Rick St. George said:**
> I get - "update manager core is already newest version".

Rick why is nothing just easy here?:D
Try this one
```
sudo update-manager -c
```

---

### Post by Rick St. George on 2016-09-19
I get Software Updater to come up and report - "The software on this computer is upto date".

Under Settings I have;

Ubuntu Software 
___Canonical supported .. main
   ___Proprietary drivers 
   ___Source code

Other software
   ___Canonical Partners
   ___Canonical Partners (source code)
   [___www.BitDefender]("http://www.BitDefender") [just to show link]
   [___www.handbrake]("http://www.handbrake")
   [___www.team-xbmc]("http://www.team-xbmc")

Updates
   ___Important Updates
   ___Recommended Updates
   ___LTS versions

Authentication
   [usual keys] ftpmaster; cdimage; packages@bitdefender

Still stumped .. what gives???

---

### Post by #&amp;thj^% on 2016-09-19
That is a mystery??
One more to try....**but be very very careful **you see **16.04 Xenial** and not [B]16.10 Yakkety
[/B]```
sudo do-release-upgrade -d
```
Oh make sure uninstall Proprietary drivers (Nividia) first...Unless it is Intel GPU then you are ok.

---

### Post by Rick St. George on 2016-09-19
No New Release Found ! ! ! 

WOW ...

---

### Post by #&amp;thj^% on 2016-09-19
> **Rick St. George said:**
> No New Release Found ! ! ! 

_WOW ..._
Wow is right? You do have a working internet connection right? (not being snarky here just checking)
This will do it...well at least it never fails me.
Do disable 3rd party ppa's first...you can change them later.
```
sudo sed -i 's/trusty/xenial/g' /etc/apt/sources.list
```
Followed by....and again check everything it reports to you, before proceeding.
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Reboot
If all goes well run again
```
sudo apt update
sudo apt full-upgrade
```
If this dose not work...I'm simply out of ideas.

---

### Post by Rick St. George on 2016-09-20
You know, sometimes you feel like an eagle, other times like a duck.  Just to be sure - I checked my connection. Lo and behold, it was loose at the back of my Router. And since my Title Bar is hidden, I did not notice there apparently was not a connection last night.

Sorry guys ... my mistake! Let that be a LESSON ... Always check the obvious first and follow proper procedures for troubleshooting.

Thanks! Case closed.
Rick

---

### Post by #&amp;thj^% on 2016-09-20
Good Job... thought that something like that was the case...it happens to all of us at some point.
Cheers

---

