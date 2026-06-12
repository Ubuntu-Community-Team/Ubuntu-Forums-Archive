---
title: "How can I force a system upgrade?"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by rdh61 on 2014-05-26
Hi,

I am running Lubuntu 13.10 on this computer and I want to upgrade to 14.04. However, the live CD does not give me the option of upgrading, only reinstalling. So I thought I would upgrade directly through the Software Updater. But Software Updater is not notifying me of the release of 14.04 (which by past experience of previous versions would also offer to upgrade), even though "Notify me of a new Ubuntu version" is set to "For any new version". How can I get the system to upgrade?

Many thanks.

---

### Post by mastablasta on 2014-05-26
what happens if you first fully update the OS and then run 

```
[FONT=Courier New]sudo do-release-upgrade[/FONT]


```
or 

```
lubuntu-development-release-upgrade
```

edit the last command should upgrade to next deve lopment version i believe which should be 14.04 in your case.

---

### Post by rdh61 on 2014-05-26
Thanks, that is what I was looking for.

---

