---
title: "I can't download packages with Synaptic"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by galej on 2012-05-10
Hi everyone.

I'm migrating to 12.04 but before I want to preserve some packages of my older repo. I trying to download the packages with Synaptic and then make a DVD with AptOnCD. 

The problem appears when I select the "download only" option in Synaptic. When I click Apply the dialog shows the rate download but when I check in /var/cache/apt this folder is empty and the free space on the HDD is not affected.

I think that the problem is because I'm refering to the repository with a line like

deb file:///media/....

so I tried to put the repository on a local webserver so the sources.list line be

deb [http://.](http://.)..

as in school where everithing works fine, but other problems appears.

The question: How can I download packages from this repository?

---

### Post by 2F4U on 2012-05-10
Have you tried to open the repository url in Firefox and just do a save as to the location you wish?

---

### Post by galej on 2012-05-10
> **2F4U said:**
> Have you tried to open the repository url in Firefox and just do a save as to the location you wish?

You mean navigate lo the location of each package and then download? I'm talking of +4000 packages. I'm trying to use Synaptic because it solves all the dependencies.

---

