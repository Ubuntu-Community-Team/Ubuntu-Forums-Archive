---
title: "Upgrade procedure - How it works ?"
date: 2018-07-30
forum: Installation &amp; Upgrades
---

### Post by Anquietas on 2018-07-30
Hello,

I have a question: I am using Kubuntu 16.04.5 and Ubuntu Server 16.04.5.

I always use LTS editions only, and I understand that the upgrader only shows new releases when the ".1" release is made available.
I totally agree, I need stable systems.

However, I am snooping for the new release every day since July 26th, when the supposed date of launch was set.

I already saw that on the websites, the new ".1" CD-Images are available for download.
Both Ubuntu Server and Kubuntu 18.04.1 CD-Images are available.
That's very nice for someone who is doing a fresh install.

But what about the existing systems that want to be upgraded ?
I didn't get a prompt saying there is a new release ? (will I get one ? on both Server and Desktop ?)

Running "do-release-upgrade" shows "No new release found", for both Ubuntu Server and Kubuntu.
However, running it with the "-d" parameter starts to do something but I aborted before any change was made, because I don't want Development environment. I want the normal, proper procedure.

So, why is this lack of synchronization between the CD-Images on the website and the "do-release-upgrade" for existing systems ?
And what is the proper way to upgrade to the next .1 LTS release ? Should I wait for it naturally or must I run some upgrade commands ?

Thank you.

---

### Post by Anquietas on 2018-07-31
BUMP !

Well ? Anyone ?

---

### Post by PaulW2U on 2018-07-31
> **Anquietas said:**
> Well ? Anyone ?
Answering you posts in reverse order I must say that your posting style does not encourage anyone  to reply. :(
> **Anquietas said:**
> So, why is this lack of synchronization between the CD-Images on the website and the "do-release-upgrade" for existing systems ?
Did you read the [Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes") for 18.04?

They say:
> Upgrading from Ubuntu 16.04 LTS

Upgrades from 16.04 LTS will not be enabled until a few days after 18.04.1's release expected in late July.

Bearing in mind that any notification is unlikely to be enabled on the day after 18.04.1's release (last Thursday) or on a weekend then the "few days after" that the release notes referred to probably means that any upgrade notification may not be received until maybe Wednesday or Thursday of this week. That's my guess. I've seen no official notification of when LTS to LTS upgrades will be enabled. As I no longer have a 16.04 installation it is not something that I can check for myself.
> **Anquietas said:**
> Should I wait for it naturally or must I run some upgrade commands ?
The only command that you need to run, in the absence of any notification, is:
```
do-release-upgrade
```
If you are told that there is no upgrade available then for the next few days at least I would say that there is *no upgrade available*. ;)

---

