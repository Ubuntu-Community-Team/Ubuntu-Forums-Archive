---
title: "Not on the latest version ?"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by oygle on 2016-12-30
When in terminal I see ..

```
 youtube-dl --version
2016.02.22

```

yet when I view the package details at [https://launchpad.net/ubuntu/+source/youtube-dl](https://launchpad.net/ubuntu/+source/youtube-dl)

I see  **2016.06.25-2** 

Synaptic package manager shows that I'm all updated ?

---

### Post by TheFu on 2016-12-31
When I **need** the latest version of a package, there are a few ways.
a) use the version from the official repos.
b) find and use a PPA from a trusted source.
c) find and use a .deb file from a trusted source.
d) find the source and use that.

For scripts, like youtube-dl, I'd use the source if the repo version doesn't do what you need. For any issues with it, the normal thing the authors as is 1) are you running the current version and 2) does that fix the issue?  Then they ask for a bug report on their project page.  I happen to know that youtube-dl project is on github and they have issue tracking there.  So - for anything related to youtube-dl, I'd suggest you ask on their project page on github.  I believe that youtube-dl is primarily used to violate ToS for a number of video sites. Perhaps it should be removed from the official repos?

**wget** is a generic tool with many, many, many different uses.  I use it to record OTA TV on a specific channel for a specific length of time using a network tuner device. It can also be used to break ToS though it isn't used that way very often, IME.  It can be used to mirror a website or selectively download only certain files too.

I cannot speak about the others. Don't know anything.

---

### Post by vasa1 on 2016-12-31
> **oygle said:**
> ... direct me to another fourm where I may obtain the answer ??
...
My answer from way back but I think it's still valid: [http://askubuntu.com/a/380460/248158](http://askubuntu.com/a/380460/248158) and several others.

---

### Post by ian-weisser on 2016-12-31
The version of each package in each release of Ubuntu:

```
$ rmadison youtube-dl youtube-dl | 2012.02.27-1          | precise/universe         | source, all
 youtube-dl | 2012.02.27-1ubuntu0.1 | precise-updates/universe | source, all
 youtube-dl | 2014.02.17-1          | trusty/universe          | source, all
 youtube-dl | 2015.02.28-1          | vivid/universe           | source, all
 youtube-dl | 2016.02.22-1          | xenial/universe          | source, all
 youtube-dl | 2016.06.25-2          | yakkety/universe         | source, all
 youtube-dl | 2016.12.01-1          | zesty/universe           | source, all
```

2016.02.22-1 is indeed the most recent available for Xenial (16.04).
There are indeed newer versions available. They have not been backported to Xenial for two reasons.

1) It defeats the purpose of an LTS. The purpose of an LTS is stability-through-minimal-changes. Security updates occur frequently, of course. Non-security package updates require a very good reason.

2) The list of possible very-good-reasons are explained at the [Stable Release Update page]("https://wiki.ubuntu.com/StableReleaseUpdates"). Nobody has identified a need to SRU this particular package.

---

### Post by oygle on 2017-01-01
> **TheFu said:**
> When I **need** the latest version of a package, there are a few ways.
a) use the version from the official repos.
b) find and use a PPA from a trusted source.
c) find and use a .deb file from a trusted source.
d) find the source and use that.


Yes, but what do you consider to be a trusted source ? Is there a list somewhere of trusted sources for different packages ?

> **vasa1 said:**
> My answer from way back but I think it's still valid: [http://askubuntu.com/a/380460/248158](http://askubuntu.com/a/380460/248158) and several others.

Thanks for that. Yes I noticed the **-U **never works for me - some msg about the package being installed by synaptic or similar. Is it much work to compile, considering you get the source ? 

> **ian-weisser said:**
> 
2016.02.22-1 is indeed the most recent available for Xenial (16.04).
There are indeed newer versions available. They have not been backported to Xenial for two reasons.

1) It defeats the purpose of an LTS. The purpose of an LTS is stability-through-minimal-changes. Security updates occur frequently, of course. Non-security package updates require a very good reason.

2) The list of possible very-good-reasons are explained at the [Stable Release Update page]("https://wiki.ubuntu.com/StableReleaseUpdates"). Nobody has identified a need to SRU this particular package.

Okay, thanks for explaining that. I wondered why I was on a later version on another (Xenial) laptop, so checked the sources and there is [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) there. Is that source trusted ? I think that particular ppa is shown for quite a few packages.

That SRU link had a link to [http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html) , and I see plasma is there, so that is great. Just need Kmail to be fixed (just about broken on Xenial).

---

### Post by TheFu on 2017-01-01
> **oygle said:**
> Yes, but what do you consider to be a trusted source ? Is there a list somewhere of trusted sources for different packages ?

What is trust?  That is a very personal question that only you can determine.  For me, a trusted source is Canonical or the project team.  Once in a while, someone on the core team might make an Ubuntu PPA available, if I recognize the name and they have a good reputation on the web, inside the team, on other projects, then I'll add the PPA.  For example, you shouldn't trust a PPA that I create. You don't know me or anything about me. At least not at this point.  Heck, I might not even be a person. ;)  

> **oygle said:**
> Thanks for that. Yes I noticed the **-U **never works for me - some msg about the package being installed by synaptic or similar. Is it much work to compile, considering you get the source ?  This is to protect us.  Things installed using the package manager need to be managed/updated/removed using the package manager. Things installed outside the package manager need to be manually managed.  I avoid going outside the package manager and try to only run versions of most things from Canonical. There are a few exceptions, but I accept the extra responsibility and manually check for updates all the time.  youtube-dl is one of those manually installed tools.  wget is NOT.

> **oygle said:**
> Okay, thanks for explaining that. I wondered why I was on a later version on another (Xenial) laptop, so checked the sources and there is [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) there. Is that source trusted ? I think that particular ppa is shown for quite a few packages.  Don't know.  youtube-dl is a script. No compile needed.  I'd get it directly from the project page on github and use the -U option to update it.  It doesn't even need to be installed using elevated privileges. Just put it into your ~/bin/.

Don't know anything about the other questions. Sorry.

---

### Post by oygle on 2017-01-01
> **TheFu said:**
> What is trust?  That is a very personal question that only you can determine.  For me, a trusted source is Canonical or the project team.  Once in a while, someone on the core team might make an Ubuntu PPA available, if I recognize the name and they have a good reputation on the web, inside the team, on other projects, then I'll add the PPA.  For example, you shouldn't trust a PPA that I create. You don't know me or anything about me. At least not at this point.  Heck, I might not even be a person. ;) 

Yes, trust is very subjective. Do you consider this PPA to be trusted ? - [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/)

---

### Post by TheFu on 2017-01-01
I've never used that PPA, so I don't have a positive opinion at this stage. 
If this is about youtube-dl, use the source from github. Can't say anything about the other things. Don't use them.

---

### Post by oygle on 2017-01-01
> **TheFu said:**
> I've never used that PPA, so I don't have a positive opinion at this stage. 
If this is about youtube-dl, use the source from github.

Thanks. When you first stated about the source, I assumed I would have to compile. But now realise it is a script, so just download/install.  :)

---

### Post by TheFu on 2017-01-01
Yes. That was mentioned in post #3 above.
We all miss details like that, sometimes. ;)

---

### Post by oygle on 2017-01-03
> **TheFu said:**
> We all miss details like that, sometimes. ;)

Yes, no one is perfect.  :D

---

