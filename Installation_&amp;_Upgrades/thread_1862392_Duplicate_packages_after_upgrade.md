---
title: "Duplicate packages after upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Burillo on 2011-10-16
Basically, after upgrade i have a lot of duplicate packages.

Symptoms? Basically, this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204552&stc=1&d=1318799372[/IMG]

I have a lot of these. They at least exist in "main" and "restricted" repos.

The "duplicate" (second) packages list some other packages as unavailable. An example:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204553&stc=1&d=1318799596[/IMG]

The "original" (first) packages, however, list those same packages as perfectly available and sometimes even installed (e.g. look at acpid and lsb-base):

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204554&stc=1&d=1318799654[/IMG]

Another difference with them is that they don't provide any description.

Prior to making these screenshots, i have cleared all sorts of package caches (ran apt-cache clean and removed everything in /var/lib/apt/lists), and i have disabled all software sources aside from main repo (deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main).

What could be the problem and what do i have to do?

---

### Post by Burillo on 2011-10-17
up?

---

### Post by brakkio on 2011-10-17
I've the same problem but I don't understand why this happen :(

---

### Post by Burillo on 2011-10-18
i *think* it might be due to the fact that i used a lot of PPA's (including testing and experimental) and these are the natty dependencies that are somehow still surviving updates (that could explain why i.e. lsb-base is not available - the *natty* version of it is indeed not available due to all software sources set to oneiric) - but unfortunately apt/aptitude doesn't display the intended distribution of the packages.

can i somehow check what distribution the package is intended to use?

---

### Post by agnul on 2011-10-26
I have the same problem on a clean 11.10 install. Also, everytime I run aptitude it shows some thousand new packages (my guess: the number of packages available) even if I "Forget new packages" everytime.

Any ideas anyone?

---

### Post by hackwater on 2011-10-26
It's a known bug with aptitude not seeing packages correctly when multiarch support is enabled (and it's enabled by default in new Oneiric installs):

[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768)

Here's hoping for a fix; in the meantime, I guess I'll see what this Muon thing is all about.

---

### Post by awry on 2011-11-21
I truly do not understand the decision-making process that led to shipping with a broken aptitude (an essential, widely used system tool), to enable an experimental feature (multiarch) relevant to only a small handful of programs.

Multiarch is certainly not relevant to most server systems, so why not at least disable it in the server edition?

Decisions like these cause me to question my faith in Ubuntu.

---

### Post by snowpine on 2011-11-21
> **awry said:**
> I truly do not understand the decision-making process that led to shipping with a broken aptitude (an essential, widely used system tool), to enable an experimental feature (multiarch) relevant to only a small handful of programs.

Multiarch is certainly not relevant to most server systems, so why not at least disable it in the server edition?

Decisions like these cause me to question my faith in Ubuntu.

To be fair, Canonical no longer includes aptitude in the default Ubuntu install.

---

