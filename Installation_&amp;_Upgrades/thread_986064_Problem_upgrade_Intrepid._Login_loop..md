---
title: "Problem upgrade Intrepid. Login loop."
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by feddozz on 2008-11-18
Hi all,

I tried to upgrade to Ubuntu 8.10 from 8.04. It downloaded successfully the packages, installed them and rebooted the laptop.

The problem is that I can't go any further than the login. After I login it goes back to the login in a loop. Again and again...

Suggestions? Shall I repair the installation, and how?

Thank you.

fed

---

### Post by taurus on 2008-11-18
At the GUI login screen, press <Ctrl><Alt>F2 and see if you are able to log in with your username and password.  If you can log in, check the disk space

```
df -h
```
and the permissions of your $HOME directory.

```
ls -la ~ | more
```
Hit the Space bar for the next 24 lines.

---

### Post by 5407 on 2008-11-18
Hi, I am having the same issue in Kubuntu.  It originally showed up a few days after an upgrade.  I thought that perhaps some tinkering from long ago had finally caught up with me, so I did a fresh install last night and am getting the same thing.  I also noticed before running into this problem that when I tried to add yakuake and a couple other essential tools that I was having some issues with the repositories (don't recall what exactly it was but it failed to allow download or install).

Any assistance or ideas would be appreciated.

Should I create a new topic for my issues?

---

### Post by taurus on 2008-11-18
> **5407 said:**
> Hi, I am having the same issue in Kubuntu.  It originally showed up a few days after an upgrade.  I thought that perhaps some tinkering from long ago had finally caught up with me, so I did a fresh install last night and am getting the same thing.  I also noticed before running into this problem that when I tried to add yakuake and a couple other essential tools that I was having some issues with the repositories (don't recall what exactly it was but it failed to allow download or install).

Any assistance or ideas would be appreciated.

Should I create a new topic for my issues?

It would be nice if you can post the complete command that you ran and the error message.  It makes it much easier to diagnose the problem.

---

### Post by 5407 on 2008-11-18
I want to try a couple things to see if I can fix it.  I am not knowledgeable enough to know what I am looking at with this stuff, and I don't know of a way to copy what I am seeing.  If I can't get it fixed I will write down the error messages.  I have had a lot more issues with the clean install than I did with the upgrade, as when I try apt-get update or upgrade now it tells me to run dpkg, however I get an error there as well.

thanks for the quick reply.

---

### Post by 5407 on 2008-11-18
Alright, well without having done anything kde decided to start working.  When I try to do apt-get update or upgrade I get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I do that and I get "dpkg: parse error, in file `/var/lib/dpkg/updates/0130' near line 1: newline in field name `#padding'"

I get a similar issue to the apt-get message now with adept.  Before all this I noticed that while it was running while trying to connect to repos that had "Translation-en_US " or something like that in them, it said something.  While looking at it in the command line it looks like those were ignored.  Not sure if that is an issue, but it seems like it doesn't matter right now due to the dpkg problem.  I do know that it looked like everything was fine when I started trying to download things with adept, but when I came back there was an error message.  I didn't save it and I have since forgotten what it said, so it could have been the same thing.

I also don't know what to look at for a cause to my problem while logging in, so while I am currently logged in with KDE, I am not sure I would have the same luck again.

---

### Post by 5407 on 2008-11-19
bump

---

### Post by feddozz on 2008-11-25
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 and see if you are able to log in with your username and password.  If you can log in, check the disk space

```
df -h
```
and the permissions of your $HOME directory.

```
ls -la ~ | more
```
Hit the Space bar for the next 24 lines.

Thank you all for your sugestions.
I could make it work unistalling compiz-core. then it worked fine without effects of course. Then I tried to install compiz again. I was ready to face the problem again but it didn't happen. Now I use Intrepid with compiz and it's fine.
Probaly I didn't activate all compiz features, are there some incompatibilities?

Bye

---

### Post by roshanjose on 2008-11-25
> **5407 said:**
> Alright, well without having done anything kde decided to start working.  When I try to do apt-get update or upgrade I get "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

I do that and I get "dpkg: parse error, in file `/var/lib/dpkg/updates/0130' near line 1: newline in field name `#padding'"




just open the terminal and run this 

sudo dpkg --configure -a


will fix the issue

---

### Post by 5407 on 2008-11-25
That is what I was saying was not working.  I did that and I got:
"dpkg: parse error, in file `/var/lib/dpkg/updates/0130' near line 1: newline in field name `#padding'"

I am in the process of deciding what to do with a reinstall, as I have had so many issues with intrepid...amongst everything else is a very annoying screen flicker when I am using KDE.

---

