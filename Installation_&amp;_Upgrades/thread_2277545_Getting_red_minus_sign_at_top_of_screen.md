---
title: "Getting red minus sign at top of screen"
date: 2015-05-09
forum: Installation &amp; Upgrades
---

### Post by gordie692 on 2015-05-09
keep getting this red minus symbol up top of screen something about package manager failed I tried choosing different server for updates
not sure what this is or means

---

### Post by Bashing-om on 2015-05-09
gordie692; Hello;

> **gordie692 said:**
> keep getting this red minus symbol up top of screen something about package manager failed I tried choosing different server for updates
not sure what this is or means

An advisory from the package manager.
Let's get the full story, post back the complete outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

so
[INDENT][INDENT]the story is told
[/INDENT][/INDENT]

---

### Post by gordie692 on 2015-05-09
what causes the minus symbol says its package error I've seen it and fixed it but I can't figure it out

---

### Post by Bashing-om on 2015-05-09
gordie692; Huh ??

> **gordie692 said:**
> what causes the minus symbol says its package error I've seen it and fixed it but I can't figure it out

If the error has been addressed then the "minus symbol" should no longer appear .

[INDENT][INDENT]it ain't magic
[/INDENT][/INDENT]

---

### Post by efflandt on 2015-05-11
When I get that (-), I use a filter in synaptic to find upgradable packages, upgrade them, and the (-) goes away. It is generally some wine related stuff for a ppa (pipelight?) that I added which didn't even do what it was supposed to do (be able to use MS Silverlight in Firefox).

I don't need that for Netflix any more because that works in Google Chrome with HTML5. But I was trying to get Firefox to work for Dayforce which uses Silverlight for some odd reason. But fortunately I can access Dayforce (for requesting vacation days) with an app on my Android phone.

---

### Post by ian-weisser on 2015-05-11
> **gordie692 said:**
> what causes the minus symbol says its package error
It means you have an unresolvable package conflict, and that you may be unable to install or remove software until you fix it. You may not be getting security updates until you fix it.
There are several possible causes, often related to non-Ubuntu software sources.

Bashing-om's instructions are the best way to discover exactly what the problem is so you can resolve it.
If you don't understand the output of the commands, then copy-and-paste it here and we will happily help.

---

