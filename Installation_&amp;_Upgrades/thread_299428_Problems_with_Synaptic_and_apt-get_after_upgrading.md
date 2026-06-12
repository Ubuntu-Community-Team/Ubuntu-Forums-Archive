---
title: "Problems with Synaptic and apt-get after upgrading"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by soapergem on 2006-11-14
I was using Breezy Badger for some time, and finally went through the automated upgrade that appeared on my tray tonight to 6.06 Dapper Drake. But now my Synaptic Package Manager isn't working, and neither is apt-get! This is the message I get when I open Synaptic:
> E: Type 'rpm' is not known on line 1 in source list /etc/apt/sources.list.d/sampler.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'rpm' is not known on line 1 in source list /etc/apt/sources.list.d/sampler.list
E: Unable to lock the list directory
And when I run "sudo apt-get install [whatever]", I get this message:
> E: Type 'rpm' is not known on line 1 in source list /etc/apt/sources.list.d/sampler.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'rpm' is not known on line 1 in source list /etc/apt/sources.list.d/sampler.list
E: Unable to lock the list directory
Somebody help! I don't know how to correct this!

---

### Post by soapergem on 2006-11-14
If it makes any difference, I opened up /etc/apt/sources.list.d/sampler.list using sudo gedit, and here are the contents of that file:
> rpm http://www.cs.wisc.edu/cbi/downloads/rpm fedora-4-i386 apps tools

---

### Post by soapergem on 2006-11-14
Hmmm...I just deleted that line from the file, and now it seems to be working. Thanks, myself, for my quick response! :p

---

