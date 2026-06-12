---
title: "bonobo errors after gutsy&gt;Hardy upgrade"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by SonicSteve on 2008-05-03
Hi folks I've seen a few people now (Ok more than a few) having problems with Bonobo, Gnome, and nautilus after upgrading from Gutsy to Hardy. I'm posting this thread in hopes that a few others may be helped.

This is the nautilus error that would come after login

[COLOR=Blue]'Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.'[/COLOR]

If I logged into the "failsafe Gnome" Everything would work perfectly.

After reading a few different threads I came across a closed Hardy thread that pointed to Mono as a potential source of the issue. A few months back I tried to get MS silverlight working to no avail. However in the process I downloaded and installed the most current Mono installation package from the mono site. This actually broke all mono programs on my computer. 

After upgrading to Hardy I got the Nautilus error above. 

So I went to the Mono installation folder that was created in my Home folder and ran the Uninstall. Everything is running perfectly now. 

Mono turned out to the source of many problems and after running the Mono Uninstall it solved everything.

Cheers, I hope this helps.

---

### Post by halloween2311 on 2008-05-06
Greetings SonicSteve,

Thanks!  This solved a very vexing problem for me!

You Rock!:guitar:

---

### Post by SonicSteve on 2008-05-07
> **halloween2311 said:**
> Greetings SonicSteve,

Thanks!  This solved a very vexing problem for me!

You Rock!:guitar:

I'm glad it helped you. Did you have a similar mono experience/ failure? Don't get me wrong on not in the camp of "Mono Sucks", Nor do I understand the complexity behind it's potential influence on other programming languages, it sure did mess things up though.

---

