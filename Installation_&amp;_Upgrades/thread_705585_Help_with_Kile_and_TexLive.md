---
title: "Help with Kile and TexLive"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by ezru on 2008-02-23
I am a beginser to Kubuntu. I installed Ubuntu 7.10 but then I used synaptic to install Kubuntu so that I can use kile with it. I am using a latex format which has some external files that do not come with the default installation of Latex, and I am trying to add these to the Texlive folders  by downloading them from CTAN website. My problem:

I dont know how to install these....

1) I tried to copy the files in to they texmf/ folder but I dont know which one it is that I have to use as there are several of them

2) After a few googling of the internet I read I should try installing TexLive 2007. But this is giving me headache trying to install it. I tried following the instructions on [http://www.tug.org/texlive/doc/texlive-en/live.html#x1-120003](http://www.tug.org/texlive/doc/texlive-en/live.html#x1-120003) but the computer says no to the very first line I have to do..

Can some one please point out to me where I have gone completely wrong?

Many thanks,
Israel.

---

### Post by frisket on 2008-03-20
> **ezru said:**
> I am a beginser to Kubuntu. I installed Ubuntu 7.10 but then I used synaptic to install Kubuntu so that I can use kile with it. I am using a latex format which has some external files that do not come with the default installation of Latex, and I am trying to add these to the Texlive folders  by downloading them from CTAN website. My problem:

I dont know how to install these....

1) I tried to copy the files in to they texmf/ folder but I dont know which one it is that I have to use as there are several of them

Read [http://latex.silmaril.ie/formattinginformation/chapter5.html#pkginst](http://latex.silmaril.ie/formattinginformation/chapter5.html#pkginst)

> 2) After a few googling of the internet I read I should try installing TexLive 2007. But this is giving me headache trying to install it. I tried following the instructions on [http://www.tug.org/texlive/doc/texlive-en/live.html#x1-120003](http://www.tug.org/texlive/doc/texlive-en/live.html#x1-120003) but the computer says no to the very first line I have to do..

Can some one please point out to me where I have gone completely wrong?.

You don't say *what* this "first line" is, so I can't help you there.

If you have an up-to-date (Gutsy) Ubuntu, install TeX-Live from the package manager.
Otherwise (older Ubuntus) you probably have tetex...remove it (all of it) and download and burn the TeX Live CD from tug.org and install from that.

P

---

