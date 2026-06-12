---
title: "Um... why is Update Manager going to delete some of my packages?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by AlsoPenCover on 2011-04-28
Going from 10.10 to 11.04 and I get this message:

[http://i.imgur.com/hS4yi.png]("http://i.imgur.com/hS4yi.png")

I honestly have no idea what most of those are (yes I'm a huge noob), so it's possible that it's necessary to delete some of them, but *Handbrake*? Open Office? Why would it delete those? What possible reason could there be?

Additionally, what does "no longer needed" mean? Is it going to delete those packages too?

---

### Post by wilee-nilee on 2011-04-28
> **AlsoPenCover said:**
> Going from 10.10 to 11.04 and I get this message:

[http://i.imgur.com/hS4yi.png]("http://i.imgur.com/hS4yi.png")

I honestly have no idea what most of those are (yes I'm a huge noob), so it's possible that it's necessary to delete some of them, but *Handbrake*? Open Office? Why would it delete those? What possible reason could there be?

Additionally, what does "no longer needed" mean? Is it going to delete those packages too?

Natty uses libreoffice, handbrake can be reinstalled the rest of the list looks rather small I wouldn't worry about it. 

I hope your backed up though.

No longer needed could mean the function is not needed or covered by something else, just think of the possibilities.

---

### Post by AlsoPenCover on 2011-04-28
> **wilee-nilee said:**
> Natty uses libreoffice, handbrake can be reinstalled

I realize that, but why would it delete it in the first place? I honestly cannot think of a good reason.

---

### Post by qamelian on 2011-04-28
> **AlsoPenCover said:**
> I realize that, but why would it delete it in the first place? I honestly cannot think of a good reason.
The version you have installed probably conflicts with some package required by the upgrade.

---

### Post by AlsoPenCover on 2011-04-28
> **qamelian said:**
> The version you have installed probably conflicts with some package required by the upgrade.
I suppose that makes sense, thanks. :)

I just wish they would have told me that, or given me an option to save the list or *something*.

---

### Post by JohnAStebbins on 2011-04-29
> **AlsoPenCover said:**
> I realize that, but why would it delete it in the first place? I honestly cannot think of a good reason.

I'm going to make a guess that you are using the 0.9.5 release PPA for handbrake found here 
[https://edge.launchpad.net/~stebbins/+archive/handbrake-releases](https://edge.launchpad.net/~stebbins/+archive/handbrake-releases)

There isn't a natty package available on this PPA yet, and the maverick package will not work on natty.  So an upgrade will cause the old package to be deleted rather than upgraded.

There is a natty build queued on the PPA.  Currently it says it will start the build in 21 hours.  Assuming all goes well, you should be able to install it tomorrow.

Alternatively, if you don't mind living on the bleeding edge, you could use the handbrake nightly builds PPA which has had natty builds for a couple weeks now.
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

