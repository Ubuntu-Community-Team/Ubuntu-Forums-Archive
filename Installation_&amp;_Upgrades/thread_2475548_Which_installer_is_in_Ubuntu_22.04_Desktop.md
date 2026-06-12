---
title: "Which installer is in Ubuntu 22.04 Desktop?"
date: 2022-05-31
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2022-05-31
Hi

I have searched like crazy for this info on how to use the new autoinstall for Ubuntu 22.04

Doesn't Ubuntu Server and Desktop use the same installer? Is Desktop still on Ubiquity and Server uses the newer Subiquity or what is it?

If that is the case, it explains why I wasted days to make the autoinstall to work on the Desktop.
When can autoinstall work for Desktop? 22.04.2?, 22.04.3?

Any can confirm?

---

### Post by tea for one on 2022-05-31
You can explore the manifest for each release
[https://hr.releases.ubuntu.com/22.04/](https://hr.releases.ubuntu.com/22.04/)

Desktop - ubiquity	22.04.15
Server -  snap:subiquity	stable/ubuntu-22.04	3359

---

### Post by guiverc on 2022-05-31
The new *desktop installer* (no official name yet; it's been referred to as the *canary* installer) was not yet ready for *prime-time* at the release of Ubuntu 22.04 LTS, thus was only available as an *alternate* installer.

The hope is that it'll be ready for later re-releases of 22.04; ie. 22.04.1 & 22.04.2, so those may contain `ubiquity` if it's not yet ready, but may switch to the new *desktop installer* (which is based on `subiquity`) **when**it's deemed ready.

To know what'll be used for 22.04.2 & 22.04.3, you'll have to watch the various announcements.Also note I don't try and keep up with them, so my knowledge won't be complete; but I'm involved in QA-testing (*and agree the canary installer wasn't ready!*) and involved with Ubuntu News so do tend to see notices/updates on installers when they are published.

---

### Post by Jaxilian on 2022-06-01
thank you for info

---

### Post by Jaxilian on 2022-06-01
> **tea for one said:**
> You can explore the manifest for each release
[https://hr.releases.ubuntu.com/22.04/](https://hr.releases.ubuntu.com/22.04/)

Desktop - ubiquity	22.04.15
Server -  snap:subiquity	stable/ubuntu-22.04	3359

Thank you. I couldn't find that

---

### Post by Jaxilian on 2022-06-01
> **guiverc said:**
> The new *desktop installer* (no official name yet; it's been referred to as the *canary* installer) was not yet ready for *prime-time* at the release of Ubuntu 22.04 LTS, thus was only available as an *alternate* installer.

The hope is that it'll be ready for later re-releases of 22.04; ie. 22.04.1 & 22.04.2, so those may contain `ubiquity` if it's not yet ready, but may switch to the new *desktop installer* (which is based on `subiquity`) **when**it's deemed ready.

To know what'll be used for 22.04.2 & 22.04.3, you'll have to watch the various announcements.Also note I don't try and keep up with them, so my knowledge won't be complete; but I'm involved in QA-testing (*and agree the canary installer wasn't ready!*) and involved with Ubuntu News so do tend to see notices/updates on installers when they are published.

I had nice preseed-files (ubiquity) that worked for 20.04.4, both with LUKS encryption and without, but same preseed-files sort of half-worked for 22.04. The installation stopped in the middle prompting me for the step "Updates and other software". I could not find reason for it. If I clicked to continue from that step, the installation just continued normally like it should.
I guess I have to go back to 20.04.4 again until 22.04 is properly remade.

---

### Post by tyang821 on 2022-10-08
> **Jaxilian said:**
> I had nice preseed-files (ubiquity) that worked for 20.04.4, both with LUKS encryption and without, but same preseed-files sort of half-worked for 22.04. The installation stopped in the middle prompting me for the step "Updates and other software". I could not find reason for it. If I clicked to continue from that step, the installation just continued normally like it should.
I guess I have to go back to 20.04.4 again until 22.04 is properly remade.

hello, have you fix the problem of "The installation stopped in the middle prompting me for the step "Updates and other software"? i meet same issue even with 22.04.1.

---

### Post by wesleymason on 2022-10-13
I am having the same issue as @tyang821 and @Jaxilian.  My preseed pauses at **Updates and other software**.  I find it hard to believe that wasn't flagged for fix.  Or is all efforts going into Canary, while I understand this still doesn't seem it should be a hard fix?

---

