---
title: "Hardy 8.04 - first impression"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by zeiz on 2008-05-06
Ubuntu Gutsy 7.10 was my main OS (with mail, docs, pics etc).
First I tried simply to upgrade my 7.10 to 8.04. After 2 hours the upgrade hanged.I got i386.iso and installed from scratch new LTS. First I noticed that Nvidia prop driver is enabled but not in use and looks like doesn't installed. No problem. I tried to install Thunderbird (I have big archive and I really need TB) and it "...cannot  be installed on your computer type (i386)" :shock: Then I found that nothing at all could be installed on my computer type :) including xorg new driver for Nvidia. I rechecked the iso and the CD burned at 4x - no errors. Update manager hangs on 26 out of 35 packages to update repositories that look almost empty if compare with 7.10. So far I noticed only "the bird" and nothing more new except the troubles. 
Guys, is it possible to fix the installation manually?
Any help is highly appreciated :)

---

### Post by jimv on 2008-05-06
Man, I'd just format that drive and try again.  Something seriously got borked during that install.  Instead of troubleshoot for hours, you can format/reinstall and be back up in 30 minutes.

---

### Post by zeiz on 2008-05-06
Thanks, sounds good, you think just installation problems? On the other hand I installed and reinstalled 7.10 many times on the same machine and my laptop without any problems... Really it bits me... Anyway I'll try and report then:)

---

### Post by Pumalite on 2008-05-06
Hardy on a clean install is the best OS around.

---

### Post by ugm6hr on 2008-05-06
This probably represents a problem connecting to the repos.

Is your internet working OK?

If yes - try a different repo mirror.

I've found that the Hardy mirrors are a lot busier, and fail more often than the Gutsy ones ever did.  Hopefully, that will improve with time.

---

### Post by Pumalite on 2008-05-06
It's true that the Servers have been slow, but they connect and update. I just updated this AM.(US)

---

### Post by jimv on 2008-05-06
It kinda sound like apt thinks he has the 64 bit version installed instead of i386...because it's telling him hte i386 packages won't run on his machine.

---

### Post by mikewhatever on 2008-05-06
> **jimv said:**
> It kinda sound like apt thinks he has the 64 bit version installed instead of i386...because it's telling him hte i386 packages won't run on his machine.

Nope. That massage usually means the repositories are disabled or off line, or that there is no internet connection.

---

### Post by ugm6hr on 2008-05-07
> **mikewhatever said:**
> Nope. That massage usually means the repositories are disabled or off line, or that there is no internet connection.

My point exactly.

---

### Post by zeiz on 2008-05-07
First of all guys, thank you all very much! Indeed Ubuntu is the best distro and Ubuntu forum is the best forum ever :)

I reinstalled Hardy and it got a little better although I still had problems. But it became clear that no errors in installation itself because all the problems were connected to repos. My connection was fine but on the Hardy side probably something was wrong and that's it :)
Actually I feel stupid, I could guess myself :oops: but I was scared with the message (never seen before) about "...you computer type(i386)"
Today everything goes perfect :-D
Many thanks again!

---

### Post by jimv on 2008-05-07
In all fairness, I've never seen that message before when the repos weren't responding.  Usually it's just a generic "Connection failed" or "connection timed out" or something like that.

---

### Post by ugm6hr on 2008-05-07
> **jimv said:**
> In all fairness, I've never seen that message before when the repos weren't responding.  Usually it's just a generic "Connection failed" or "connection timed out" or something like that.

Those messages indicate that the servers have failed.

The message he got is caused by an absence of internet connection, specifically at the time of installation.  This can be rectified by connecting, then activating all the relevant repos (e.g. universe etc).

The suggestion that it could also be a problem with the repo was a bit of a guess, but it is entirely likely that if no internet connection at the time of installation causes it, that an offline repo could cause it too.

---

### Post by nick09 on 2008-05-07
> **Pumalite said:**
> It's true that the Servers have been slow, but they connect and update. I just updated this AM.(US)

How do you know if you are downloading a update?

---

### Post by Pumalite on 2008-05-07
Type in the Terminal:
sudo apt-get update
sudo apt-get upgrade

---

