---
title: "update-manager-core Doesn't exist"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by timhaughton on 2007-04-19
The upgrade docs say, to upgrade a server...

f you run an Ubuntu server, you should use the new server upgrade system.

   1.

      Install update-manager-core:

      sudo apt-get install update-manager-core



I get...

timhaughton@agibuntu:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package update-manager-core
timhaughton@agibuntu:~$


Any offers?

Cheers

Tim

---

### Post by sabrewulf on 2007-04-19
^^^bump for this guy, I'm having the exact same problem

---

### Post by BoneyOne on 2007-04-19
While I'm not running the server version. I just got finished installing the AMD64 Desktop version and was greeted with the same updates.

It seems as if the repo's are suffering from an overload currently.

I'm going to wait until late tonight or tomorrow to try again to update, maybe the mass of people hitting all the servers will die down some.

---

### Post by ericbarch on 2007-04-19
I had the same problem. Just update your repositories and you should be good to go.

---

### Post by sabrewulf on 2007-04-19
> **ericbarch said:**
> I had the same problem. Just update your repositories and you should be good to go.

still a bit of a noob...  how does one update the repositories?

---

### Post by sabrewulf on 2007-04-20
Just a followup...

Once I commented out the CD in /etc/apt/sources.list and re-ran apt-get update, running apt-get install update-manager-core worked fine.  Of course I didn't get any timeouts on apt-get update like I was getting earlier in the day, so the commenting out of the CD from the repository list may have had nothing to do with anything.  I'm thinking the servers were just getting slammed earlier.

---

### Post by timhaughton on 2007-04-20
It's 0700 GMT on Friday. I'm getting no timeouts on update, but update-manager-core is still not there.

Cheers,

Tim

---

### Post by moon2js on 2007-04-20
I'm trying an alt cd install.

At the "Select and install software" stage (after not choosing DNS server and LAMP), the progress bar goes up to 85% and then hangs at update-manager-core."

This is before I get to be at any prompt where I can do anything really, but maybe it's related to you guys' problem?

---

### Post by timhaughton on 2007-04-20
> **moon2js said:**
> I'm trying an alt cd install.

At the "Select and install software" stage (after not choosing DNS server and LAMP), the progress bar goes up to 85% and then hangs at update-manager-core."

This is before I get to be at any prompt where I can do anything really, but maybe it's related to you guys' problem?

Possibly, at the minute, I'm going to assume the mirros haven't replicated yet. I'll try again tonight.

Tim

---

### Post by wgrant on 2007-04-20
Please ensure that you have the edgy-updates repository enabled, as that's where update-manager-core is.

---

### Post by nickswift on 2007-04-20
I had the same problem too. I definitely had edgy-updates in my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe

When I ran apt-get update it would appear to run successfully but had clearly not correctly updated and I saw the same error as the other posters.

I have just tried it again and it has worked for me.

Nick

---

### Post by timhaughton on 2007-04-20
> **nickswift said:**
> I had the same problem too. I definitely had edgy-updates in my sources.list:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates restricted main multiverse universe

When I ran apt-get update it would appear to run successfully but had clearly not correctly updated and I saw the same error as the other posters.

I have just tried it again and it has worked for me.

Nick

I promised myself I would wait a week before upgrading. Enthusiasm gets me everytime. That's to Ubuntu's credit, I haven't even given a thought to upgrading my XP box to Vista.

Replication will have sorted itself out tonight when I get home.

Tim

---

### Post by etherealremnant on 2007-04-20
The servers are definitely hella hardcore busy.

I switched mine from the US server to the main server though and its working fine now.

---

### Post by timhaughton on 2007-04-20
> **fujitsu said:**
> Please ensure that you have the edgy-updates repository enabled, as that's where update-manager-core is.

OK, just tried again. Updates are and have always been enabled. Still reporting same problem, update-manager-core doesn't exist.

Tim

---

### Post by Watter on 2007-04-27
> **moon2js said:**
> I'm trying an alt cd install.

At the "Select and install software" stage (after not choosing DNS server and LAMP), the progress bar goes up to 85% and then hangs at update-manager-core."

This is before I get to be at any prompt where I can do anything really, but maybe it's related to you guys' problem?
As of today (4/27/07) I am having exactly this same issue. What odd is that on another machine using the same CD, the installation completes. Could this be a network issue on my side? Does the installation process need a working Internet connection in order to complete?

---

### Post by moon2js on 2007-04-27
I don't know whether it was a network/repo problem or not, but in my case, after letting it "hang" for a while, I came back an hour later to find that installation had completed and the CD was ejected. It appeared to be hung, but I guess it was just taking a really long time without giving any progress feedback.

---

