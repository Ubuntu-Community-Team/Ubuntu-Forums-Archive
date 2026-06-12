---
title: "OpenOffice Missing from my dist-upgrade"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by blue_thunder on 2006-06-01
hiya,

I just switched over to dapper a few minutes ago, and everything seems to be flowing pretty well with the major exception of OpenOffice...which for some reason is missing. Any attempt to open .doc files is met with an error. Any advice?

thanks.

---

### Post by unnes on 2006-06-01
Same with me. OpenOffice is glaringly missing, and not in the Applications > Office menu like it was under Breezy.

I guess it's time to install from the repos?

---

### Post by metoo on 2006-06-01
Updated your /etc/apt/sources.list correctly?

The package 'openoffice.org' is in main and should give you openoffice 2.0.2 .

---

### Post by unnes on 2006-06-01
[QUOTE=metoo]Updated your /etc/apt/sources.list correctly?

The package 'openoffice.org' is in main and should give you openoffice 2.0.2 .[/QUOTE]

I updated my sources.list with a Dapper sources.list file I saw on the forums. But I think what the OP and I were concerned about is the fact that OpenOffice didn't install with Dapper, like it did with Breezy. I had no problem installing it from the repos, but it should have been installed by default.

---

### Post by Carrots171 on 2006-06-02
OpenOffice went missing when I dist-upgraded, too. I've installed it using Synaptic, but now it looks butt-ugly (see attachment). It doesn't match up with my theme anymore. How do you fix this?

EDIT: Nevermind, I installed the "openoffice-gnome" package or something like that and now it matches my theme. I think that OpenOffice should be installed by default to eliminate this kind of confusion.

---

