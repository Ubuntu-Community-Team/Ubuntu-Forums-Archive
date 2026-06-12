---
title: "Installation to more than one machine"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by eXistenZ.online on 2005-10-27
Hi to all,

First of all, I apologize for my bad English. (I still try to improve it)

We have an intranet in campus with 10 clients and a server. Last week, we agree to migrate from Fedora Core 3 to Ubuntu, but we have two serious concerns:

1. We want to do a standard installation for every machine, and Ubuntu's standard installation is not enough. For example, we need to install extra packages for TeX, etc. but we don't want to install every client one by one. How can we define a standard installation scheme, or simply update every machine easily?

2. Our old Core 3 recognized our HT CPU's with no problem and installed i686-smt kernels. Does Ubuntu have a such mechanism. (Simply it's better not to compile kernel for me...)

3. In future, how can we automize the update process rather than updating every client seperately. I think this question is related to the first one.

Any help/comment greatly appreciated. Again, I apologize for my bad English. 

Thanks :)

---

### Post by aysiu on 2005-10-29
PartImage can capture the image of an entire partition and compress it. You can set up one box, update it as desired, then capture it and reinstall that on all your machines.

The only issue you may encounter with such a strategy is that all the machines should be the exact same model with the same hardware; otherwise, having the exact same installation (partition image) will be screwy on most of the computers.

---

### Post by eXistenZ.online on 2005-10-29
Thanks for your reply... We have identical clients, so this solution will be our saviour, for sure...

---

### Post by aysiu on 2005-10-29
[QUOTE=eXistenZ.online]Thanks for your reply... We have identical clients, so this solution will be our saviour, for sure...[/QUOTE] You may also want to look into [Mondo Rescue](http://www.mondorescue.org/index.html)

---

### Post by eXistenZ.online on 2005-10-29
One more question. What about the future updates? Can I automize it by a local repolsity, or do I have to use something else?

---

### Post by aysiu on 2005-10-29
[QUOTE=eXistenZ.online]One more question. What about the future updates? Can I automize it by a local repolsity, or do I have to use something else?[/QUOTE] Local repositories get tricky because you have to make sure your own local repository is up-to-date. You can do this, but I don't know how. A search for the forums may help (with *local repository* as the keyword).

I would suggest using the actual Ubuntu repositories and then setting all the machines to auto-update.

---

### Post by eXistenZ.online on 2005-10-29
[QUOTE=aysiu]Local repositories get tricky because you have to make sure your own local repository is up-to-date. You can do this, but I don't know how. A search for the forums may help (with *local repository* as the keyword).

I would suggest using the actual Ubuntu repositories and then setting all the machines to auto-update.[/QUOTE]

In this situation, I think a simple cronjob will save me...

Addition to these, will Breezy recognize my CPU and install the appropriate kernel, or do I have to make a advanced install? I ask this for our collegues not-very-good at Linux...

Thanks :)

---

### Post by aysiu on 2005-10-29
[QUOTE=eXistenZ.online]In this situation, I think a simple cronjob will save me...

Addition to these, will Breezy recognize my CPU and install the appropriate kernel, or do I have to make a advanced install? I ask this for our collegues not-very-good at Linux...

Thanks :)[/QUOTE] Yikes. I don't know. My guess is that it will install the latest kernel, which should be better than the previous kernel at recognizing hardware. The only way to know is to try...

---

### Post by eXistenZ.online on 2005-10-29
Thanks for your help...I will try it as soon as possible and post the results.

Thanks again! :smile:

---

