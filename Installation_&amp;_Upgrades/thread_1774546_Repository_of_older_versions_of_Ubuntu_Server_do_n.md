---
title: "Repository of older versions of Ubuntu Server do not work"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by rawa on 2011-06-03
HI

 I installed Ubuntu Server 8.10, 9.04, 10.04, until I discovered that the packages of these versions to upgrade and install graphics settings are not available, then install the current version is 11.04 and there I found that repositories responded and set me right.

 Then the repositories of previous versions are not available?
 When I install the current version on all packages that I need to back packs and save it for if I need it later.

 How do I get the packages and put together a repository itself if others were dashed this is still operating, and maintenance would be needed?

 Hear their input, thank you very much.

 Ruben

---

### Post by mörgæs on 2011-06-04
8.10 and 9.04 are unsupported, so best is forgetting about them.

For 10.04, there should definitely be a repository available. If you install, don't you get the option of installing updates?

---

### Post by ghira on 2011-06-05
I have a (desktop) machine running 9.04, and "update manager" has switched
from offering 9.10 to offering 10.04.2 

I didn't think this was a legitimate upgrade path.

Has something changed, or is it that with 9.04 and 9.10
both being unsupported, this machine can no longer be upgraded
at all, and update manager offering me 10.04.2 is a mistake?

---

### Post by ivanovnegro on 2011-06-05
> **ghira said:**
> I have a (desktop) machine running 9.04, and "update manager" has switched
from offering 9.10 to offering 10.04.2 

I didn't think this was a legitimate upgrade path.

Has something changed, or is it that with 9.04 and 9.10
both being unsupported, this machine can no longer be upgraded
at all, and update manager offering me 10.04.2 is a mistake?

9.10 also reached end of life this year in April. Seems you will be better with install 10.04 (recommended) or 11.04 fresh.

---

### Post by ghira on 2011-06-05
> **ivanovnegro said:**
> 9.10 also reached end of life this year in April. Seems you will be better with install 10.04 (recommended) or 11.04 fresh.

"fresh" applying to both of them?

The release notes for 9.10 were phrased in terms of "delay until 
this is fixed" for stuff that apparently never was, so I kept
putting it off. Hmm.

---

### Post by ivanovnegro on 2011-06-05
> **ghira said:**
> "fresh" applying to both of them?

The release notes for 9.10 were phrased in terms of "delay until 
this is fixed" for stuff that apparently never was, so I kept
putting it off. Hmm.

Yes, I mean both of them. Normally you cannot upgrade without to pass one release if it is not an LTS. So, in your case I am not sure if you can upgrade right now without problems to 10.04, maybe its still possible, but really it would save you time to install from scratch, the new Ubuntus improved drastically and the install is under 30 minutes.

I would recommend you to backup all your files, you should to do this anyway and then try the 10.04 Live CD, if everything is running alright, if you just upgrade you could encounter maybe problems with the newer versions, so to try a Live CD is always a good idea.

---

### Post by ghira on 2011-06-05
> **ivanovnegro said:**
> Yes, I mean both of them. Normally you cannot upgrade without to pass one release if it is not an LTS. So, in your case I am not sure if you can upgrade right now without problems to 10.04, maybe its still possible, but really it would save you time to install from scratch, the new Ubuntus improved drastically and the install is under 30 minutes.

I would recommend you to backup all your files, you should to do this anyway and then try the 10.04 Live CD, if everything is running alright, if you just upgrade you could encounter maybe problems with the newer versions, so to try a Live CD is always a good idea.

OK thanks for the info. I have to admit that the new grub, filesystem,
booting etc. have sounded appealing for some time. Backup and clean
install it is, then. (Actually I've been happy with 9.04
and if the package repositories were still there but never updated
I might have stuck with it indefinitely given that this machine
is 4 years old: I'll probably get a new machine soon enough anyway)
But if even package installation is no longer possible I think an upgrade
has become unavooidable. I'd been planning on doing 9.10 and 10.04
in the next few days but I don't think I'd have got some of the better stuff
that way.

Thank you again.

---

### Post by mikewhatever on 2011-06-05
While the repositories for 10.04 are well and alive, there are also repositories for old unsupported releases. If, for whatever reason, you need to use one of those, edit the sources.list as follows:
> ## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverse

Note: CODENAME = the name of the release, for example, jaunty.

---

### Post by ghira on 2011-06-05
> **mikewhatever said:**
> While the repositories for 10.04 are well and alive, there are also repositories for old unsupported releases. If, for whatever reason, you need to use one of those, edit the sources.list as follows:


Note: CODENAME = the name of the release, for example, jaunty.


Oh! Thank you. In the short term, I shall do this.

---

### Post by mörgæs on 2011-06-05
> **ghira said:**
> ...given that this machine
is 4 years old: I'll probably get a new machine soon enough anyway

A four years old computer is great for Ubuntu. None of mine are that new :-)

---

### Post by ghira on 2011-06-06
> **mörgæs said:**
> A four years old computer is great for Ubuntu. None of mine are that new :-)

Well, my main computer before this (until 2006) was an Amiga 1200, last upgraded  significantly in 1997. (To a 50MHz processor!) But sadly it became too fragile and getting parts was getting harder and harder.

I suppose I could run UAE on ubuntu and... no that's a bit silly really.

---

