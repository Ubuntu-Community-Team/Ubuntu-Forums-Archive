---
title: "Unable to download updates"
date: 2020-03-15
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2020-03-15
Running 19.10.  When I am prompted to install updates and I click to install them now the following error message pops up:

Unable to download updates:
failed to refresh cache: #: The repository ‘[http://ppa.launchpad.net/darklin20/bomi/ubuntu](http://ppa.launchpad.net/darklin20/bomi/ubuntu) eoan Release’ does not have a Release file.

What should I do to correct this problem?

Thanks for any advice.

Caruso

---

### Post by Impavidus on 2020-03-15
That repository has no software for Ubuntu 19.10. It hasn't been maintained for 5 years. Disable it.

---

### Post by carusoswi on 2020-04-18
How do I disable it?

. . . and thanks for the reply.

I almost asked this question again, today.

Caruso

---

### Post by CelticWarrior on 2020-04-18
Use the same command you used to add it but with the --remove argument or, in GUI fashion, open Software & Updates > Other software (2nd tab), select it and remove (type your password when requested).

---

### Post by SeijiSensei on 2020-04-19
It's likely the line referencing the darklin20 repository resides in a file with a .list extension in /etc/apt/sources.list.d/. If so, you can just delete the file (using "sudo rm filename") and run "sudo apt update" again.

---

### Post by Vignesh_S on 2020-04-21
Try correcting ur time if wrong, it may solve the problem

---

