---
title: "updating kubuntu 10.04 to 12.04 issues"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by vaim369 on 2012-05-23
Alright, Tried to do it updating my package kits, got a problem, normally it should say when the latest LTS is out right? Well it is not for me, tried changing some settings, and now it says maverick 10.10 is the latest distro (wtf?) some help or advice would help.
Kinda new to using ubuntu, so go easy on me

Edit: Okay I think I screwed up, ran a terminal, put in some commands i found on other threads (changed prompt in update manager from lts to normal, looks like this
Prompt=normal

now it's updating to 10.10 maverick. . .what now?

Edit:NVM, it stopped at a yes or now option, no worries

---

### Post by Maro848 on 2012-05-23
This is a problem that I have heard about on all forms of Ubuntu not just Kubuntu, the fix to this is to backup your files and info and to do a reinstall using the new LTS. For some reason there is a problem that people are having when they upgrade from 10.04.

---

### Post by jadtech on 2012-05-23
if you are running 10.04 fact is 10.10 is the newest distrbution upgrade 12.04 is labeled current release . 

if you go into you software updater settings ubuntu software tab bottom menu notify me of new ubuntu version , switch it from only long term support to FOR any new version  then close and check to see if  the upgrade changed to 12.04 release .. 

if not go to terminal , type this 

```
 sudo apt-get update

sudo apt-get do-release-upgrade 


```

do your self a favor and back everything up  if there is nothing imporatant enough to  take the time to back up then  might as well do a clean install ..

---

### Post by vaim369 on 2012-05-23
Thanks for the ideas, think ima just back up everything re install

---

### Post by mastablasta on 2012-05-24
> **vaim369 said:**
> Thanks for the ideas, think ima just back up everything re install
 
that would be A LOT faster.

---

