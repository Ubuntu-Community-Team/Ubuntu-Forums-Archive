---
title: "Upgrade 22.04 to 23.04"
date: 2023-05-30
forum: Installation &amp; Upgrades
---

### Post by regs4 on 2023-05-30
Is it possible to upgrade directly? **do-release-upgrade** only offer 22.10.

---

### Post by #&amp;thj^% on 2023-05-30
Please make clear your intentions here, you post>> **"Upgrade 22.04 to 23.04 "** but you ask about "**only offer 22.10. "**
clarity needed here first.

---

### Post by Impavidus on 2023-05-31
I think a direct upgrade from 22.04 to 23.04 is supposed to be offered when 22.10 has reached end of life, two months from now. And I also believe these skipping upgrades that are not LTS to LTS are less thoroughly tested than other release upgrades.

---

### Post by regs4 on 2023-06-01
> **1fallen said:**
> Please make clear your intentions here, you post>> **"Upgrade 22.04 to 23.04 "** but you ask about "**only offer 22.10. "**
clarity needed here first.
Intention is to upgrade 22.04 LTS to 23.04. do-release-upgrade says there is only 22.10 to upgrade to.

```

# do-release-upgrade
Checking for a new Ubuntu release

= Welcome to Ubuntu 22.10 'Kinetic Kudu' =

The Ubuntu team is proud to announce Ubuntu 22.10 'Kinetic Kudu'.

```

---

### Post by guiverc on 2023-06-01
Ubuntu offers two upgrade paths.

- You can upgrade from 22.04 LTS to the **next LTS** **after** 24.04.1 has been released; but that's not for a long time.

*OR*

- You can upgrade from 22.04 LTS to the **next release** which currently is to 22.10.  That is a *fully QA & CI *tested upgrade path.

After the EOL of 22.10, the [*ubuntu-release-upgrader*]("https://launchpad.net/ubuntu-release-upgrader") tool will allow you to upgrade from 22.04 to the next release, which **will then be 23.04**, however it's far less less QA-tested (*though is still CI tested*) path.

ie.  I'm agreeing with what Impavidus has already stated.

FYI:   I'm involved with a *flavor* of Ubuntu, and we [didn't/don't perform]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") QA testing of 22.04 to 23.04; as we QA test only the next release (ie. 22.04 to 22.10), or LTS to LTS (ie. *we'll QA-test from 22.04 to 24.04 & 23.10 to 24.04 in the future*) which is common as 22.04 to 23.04 gets little interest.

---

### Post by TheFu on 2023-06-01
> **regs4 said:**
> Is it possible to upgrade directly? **do-release-upgrade** only offer 22.10.

Please carefully consider ramifications before moving from an LTS release (22.04) to a short-term release (22.10 or 23.04 or 23.10).  There are a few good reasons to switch, but many, many, many more to stay on the LTS.

---

### Post by ajgreeny on 2023-06-01
In theory it is possible to do what is often called a **dirty-upgrade** by running the upgrade/install medium from USB, using the **Something Else** option, pointing the new root to your original root partition, but most importantly deselecting the **Format** tick-box.

I have never tried this and would simply warn that you ensure before trying it that you have good usable backups of everything important to you.

I must also repeat what has already been said about moving from an LTS to a standard or intermediate version which will have support now for only another 7 months before you have to upgrade the version again. Most users stick entirely with LTS versions only and perhaps try the intermediate ones as virtual machines just to see how the OS is proceeding and what, if anything is really new and better.

---

### Post by guiverc on 2023-06-01
> **ajgreeny said:**
> In theory it is possible to do what is often called a **dirty-upgrade** by running the upgrade/install medium from USB, using the **Something Else** option, pointing the new root to your original root partition, but most importantly deselecting the **Format** tick-box.

I have never tried this and would simply warn that you ensure before trying it that you have good usable backups of everything important to you.


Can't say I'm a *like* seeing it described as a "*dirty-upgrade*", but given I call it an *"**unclean***" install  (or *upgrade via re-install*), its the same thing. I use it often... as it's a *testcase* we at Lubuntu test for meaning I use this install roughly *weekly* using a *daily* ISO of an unreleased product (eg. 22.04.3) to upgrade packages on a system & ensure my files are untouched, no configs were changed etc & achieve my upgraded packages whilst performing a QA-test install at the same time :P

When a release goes EOL & I don't need an install for support purposes any more; I use this re-install method to switch the release to the next *development* release then start re-installing that weekly instead of upgrading packages... I also use it for my own boxes too often as it's faster than the normal *release-upgrade* process (*and doesn't require anywhere near as much free disk space to complete*). My last install of it can be seen [here]("https://iso.qa.ubuntu.com/qatracker/milestones/446/builds/279262/testcases/1761/results") where I switched a Ubuntu-MATE 23.04 install (*with additional or 'manually installed' packages & data files*) to a Ubuntu Desktop *mantic* (23.10) system without losing my *manually installed* packages or data files, yet also achieved a switch from MATE to GNOME at the same time as switching release.  ie. **I'm a *big fan of it *and it's *power***.

**HOWEVER **I'm largely talking about QA-test installs if you note above; where only Ubuntu repository software is installed (ie. **no third party**).   It's great if you have no third party, however results can be mixed with third party. Depending on how the third party software is packaged, you may or may not have problems with it.  I use this install on my own systems with some third party, but I'll assess what packages are there, where its from (*ie. who packaged it*) before I use this method, and often decide to remove that (3rd party) software prior to the install, then add it back post-install depending on what 3rd party packages were involved.  ie. this *dirty* or *upgrade via re-install* cannot do everything for you.

---

