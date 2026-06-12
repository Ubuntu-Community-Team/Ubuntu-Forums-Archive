---
title: "How can I upgrade if I have no network connection ?"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Onesimus on 2008-04-17
My scenario is that I have a computer that is not connected to the internet (This could be because I don't have a internet access or because of local security reasons).  Is it possible to download all the updates that have occurred since the final release of ubuntu version onto a CD (on a networked PC) and then install onto the non-networked PC ?

---

### Post by mikewhatever on 2008-04-17
Yes. [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

### Post by Onesimus on 2008-04-18
Thanks Mikewhatever,

I was unaware of this facility.  I suppose what I am surprised about now is that this facility is not on the Ubuntu Website.  Why do I have to register on an alternative website ?  The process seems to complicated for new users of uploading particular files, etc.

Could not the good guys at Ubuntu provide an ISO file (updated weekly/fortnightly) immediately below the release version of the ISO file ?

---

### Post by dje on 2008-04-18
Download the alternate (instead of the live cd) install iso from ubuntu.com. Burn it to a CD and insert it while your computer is running. A dialog box should appear asking if you wish to upgrade using the CD. Note you can only upgrade from 7.10 to 8.04 and 6.06 to 8.04 otherwise you have to upgrade to the next version until you reach 8.04, if you get what i mean ;)

hope that helps,
dje

---

### Post by Onesimus on 2008-04-18
So is the alternate install CD continually re-built.  I was under the impression that the release version was frozen.

It may be that you have misunderstood my original query (???)

---

### Post by dje on 2008-04-18
Ah i misread what you were trying to do, i thought you wished to upgrade to hardy heron. Ill have a look to see what i can find

dje

---

### Post by dje on 2008-04-18
Have a look in /var/cache/apt/archives on the networked machine, that is where all the .debs you have installed from the repositories (including updates) are stored (unless you've run apt-get clean ;))

hope that helps,
dje

---

### Post by Onesimus on 2008-04-18
No, it doesn't.

I was looking for a simple download (.ISO) of the patches that had been applied to the installation CD.  Download that on my networked machine and burn to CD.  Then insert into my non-networked machine and install from the CD.  Hey Presto - an update machine with minimal amount of effort.

If this facility does not exist, then I can see many benefits if it did.  For example, if someone decides to move over to Ubuntu in six months - and install Ubuntu on ten machines.  All they need to do is download 2 CDs.  The release version and the upgrades.  Otherwise, they would have to upgrade ten machines over the network putting un-necessary strain on the servers.

---

### Post by zvacet on 2008-04-18
Use what** mikewhatever** suggested to you.Read how to and you will see that is not that hard to do.

> For example, if someone decides to move over to Ubuntu in six months - and install Ubuntu on ten machines

He will probably use [this.]("https://help.ubuntu.com/community/Apt-Cacher-Server")

---

### Post by Onesimus on 2008-04-18
Thank you, zvacet.

I am not trying to be awkward (honest !)

But surely, I shouldn't need to use the method that Mikewhatever proposes.  I shouldn't have to register on a non-Ubuntu website to obtain upgrades from the Ubuntu repositories.  How can I be certain that the updates I obtain are certified by Ubuntu ?

If the update process is too arduous a task then users that are non-networked will not upgrade.  I have used Ubuntu for approx. a year (so still consider myself relatively new to Ubuntu) and what I have been particularly impressed with is the ingenuity and ease of use of the OS as a whole.  What I am suggesting should not be too hard a task.

The web page that you suggested I found to be incomprehensible and (I assume) is outside the capability of a significant proportion of desktop users.

---

### Post by zvacet on 2008-04-19
> How can I be certain that the updates I obtain are certified by Ubuntu ?

I don´t know.Maybe because that script is made by Ubuntu forum member named** epimeteo.** You can PM to him and ask why you have to register.

---

### Post by mikewhatever on 2008-04-20
> **Onesimus said:**
> Thanks Mikewhatever,

I was unaware of this facility.  I suppose what I am surprised about now is that this facility is not on the Ubuntu Website.  Why do I have to register on an alternative website ?  The process seems to complicated for new users of uploading particular files, etc.

Could not the good guys at Ubuntu provide an ISO file (updated weekly/fortnightly) immediately below the release version of the ISO file ?

You don't have to register anywhere unless you want to. Updates are non-compulsory, especially with no connection to the net.
The 'good guys at Ubuntu' already provide 4 versions of Ubuntu in about 5 different flavors, all free of charge. Don't you think you're being slightly over demanding?

---

### Post by zsh on 2008-04-29
I think what you are looking for is apt-on-cd. [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Its also in the main or universe ubuntu repos(I believe).

I hope it works out...

---

### Post by blindvic on 2008-04-30
> How can I be certain that the updates I obtain are certified by Ubuntu ?
Because the updates are downloaded from ubuntu's website. Nonetdebs just compiles the list of nedeed updates for your machine

---

### Post by hendersoneg on 2008-05-13
Take a look at AptOnCD.  It is in the Synaptic Pkg manager.  I am a similar situation to you in that I can't get high speed where I live (too far from a tel substation and no cable).  I take my laptop to the local internet cafe in town, update my Ubuntu on the laptop.  Run AptOnCD and make an image.  Burn it to a CD. Stick it in my home machine and Voila, all updates are done and both machines are current.  Pretty simple, even for a newbie like me.

---

