---
title: "apt-get remove wants to uninstall lubuntu-desktop"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by jeffbarish on 2012-12-05
I just did a clean install of lubuntu 12.10 (amd64).  If I try to remove a package (e.g., xpad) with apt-get remove xpad, apt-get wants to remove lubuntu-desktop as well as xpad.  It doesn't matter what package I specify for the remove, apt-get always wants to remove lubuntu-desktop as well.  I tried installing upgrades after the initial install.  I rebooted.  Same behavior with remove.  I tried dist-installing upgrades.  I rebooted.  Same behavior with remove.  I have previously installed lubuntu 12.10 from the same flash drive without having this problem.  The current installation seems to work fine as long as I don't try to remove any packages.

---

### Post by byStanderone on 2012-12-05
...hi, would not advice using the 'remove' command. it is safer to use the package manager instead.

---

### Post by ibjsb4 on 2012-12-05
Could not find the Lubuntu counterpart, but this gives the message about meta-packages.

[https://help.ubuntu.com/community/CommonQuestions#Meta-packages:_ubuntu-desktop](https://help.ubuntu.com/community/CommonQuestions#Meta-packages:_ubuntu-desktop)

---

### Post by snowpine on 2012-12-05
lubuntu-desktop is a "metapackage" that "depends" on xpad and several other applications/packages. apt-get remove is behaving correctly that if you try to remove a dependency then you must necessarily remove the packages that depend on it (or else they will be in a broken state).

[http://packages.ubuntu.com/quantal/lubuntu-desktop](http://packages.ubuntu.com/quantal/lubuntu-desktop)

xpad uses **0.5mb** of disk space so there is really no advantage to uninstalling it, I recommend to let it be. It's a common beginner misconception that removing "bloat" from Ubuntu will make it run faster, but you wouldn't open up the hood of your car and take parts out, would you?

---

### Post by vasa1 on 2012-12-05
Shortly after I installed Lubuntu 12.10, I removed the "games" (ace-of-penguins) via the Lubuntu Software Center. I'm not sure I was asked about it, but lubuntu-desktop was removed as well. I've had no problems because of its removal. It's considered a "meta package" and not of any consequence.

You can read this: [http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
and this:
[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

---

### Post by jeffbarish on 2012-12-05
I am not able to log in after the remove procedure, which is consequential, but it is possible that I have been mislead into ascribing the problem to the removal itself.  I will investigate further.  Thanks for the information.

---

### Post by oldos2er on 2012-12-05
> **byStanderone said:**
> ...hi, would not advice using the 'remove' command. it is safer to use the package manager instead.

apt-get *is* a package manager.

---

### Post by zvacet on 2012-12-05
@ **jeffbarish**

Maybe you will find easier to install,unistall...packages with synaptic.Install it with

```
sudo apt-get install synaptic
```

---

### Post by ivotkl on 2012-12-05
> **jeffbarish said:**
> I am not able to log in after the remove procedure, which is consequential, but it is possible that I have been mislead into ascribing the problem to the removal itself. I will investigate further. Thanks for the information.
 
Do you have further information about not  being able to log in? What happens (or does not happen) when you try to? Do you see any error message on the screen? Can you login from terminal? (alt+F1)

---

