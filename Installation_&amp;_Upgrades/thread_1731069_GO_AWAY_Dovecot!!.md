---
title: "GO AWAY Dovecot!!"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by bbqroast on 2011-04-16
Sigh. Well until now i've been findign Ubuntu amazing programs install without hitches! Things just... Work (I come from Vista so that's very new!).

Anyway here is my problem:
I have been setting up a mail server but out of pure laziness I screwed up the first time so now I want to redo it this time using Courier instead of Dovecot (from what i've read courier seems far more useful in my situation).

Anyway I start uninstalling my first installation of my mail server so I enter:
[HTML] sudo apt-get uninstall dovecot [/HTML]and wait then:
[HTML] Reading package lists... Done
Building dependency tree
Reading state information... Done
Virtual packages like Dovecot can't be removed[/HTML]Well what the??
I really need to kill Dovecot cause it's hogging Couriers job.

If this was windows Dovecot would be cowering in the corner while I raised my weapons- but knowing me i'd corrupt my hard drive in the process of destroying it.

Oh yeah barely on the topic but:
How hard is it to flip Courier over to using virtual accounts?
I want to read re-read and check the guide thanks to the "Incomplete Article" flag before I switch it over.

---

### Post by Dutch70 on 2011-04-16
Well I believe the command would be...
```
sudo apt-get remove dovecot
```
and/or 
```
sudo apt-get purge dovecot
```

At this point though I would suggest using synaptic package manager to remove it. Just open synaptic, search for dovecot, mark it for complete removal & apply.

That should have it cowering in the corner. ;)

---

### Post by srs5694 on 2011-04-16
A "virtual package" is a package that's nothing but dependencies on other packages, to simplify installing a collection of related packages. Ubuntu packages Dovecot as several packages, presumably to enable users to install only the parts they need.

Dutch70's suggestion should work; you should be able to locate all the Dovecot packages via synaptic and uninstall them.

---

### Post by bbqroast on 2011-04-19
Tried:
sudo apt-get purge
No use :(.

srs5964 what do you mean by that please explain??

---

### Post by Dutch70 on 2011-04-19
Since he isn't logged in right now, I'll give this a shot.

I think basically what he is saying is, there isn't just one package for dovecot, hence the reason "purge dovecot" didn't work. It's a compilation of several packages.

Open Synaptic Package Manager. Search for "dovecot". Mark anything related to it that is installed for complete removal, and click apply. 

Not sure if you've used synaptic before, so I've included a pic. Anything that has a box colored in on the left, is installed.

---

### Post by Jose Catre-Vandis on 2011-07-05
Same issue on server installation (so no gui / no synaptic). Chose mail server during installation, but I don't need it and wish to uninstall it all.....

---

