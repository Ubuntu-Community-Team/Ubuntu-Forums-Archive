---
title: "Desktop or Server"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by shendric on 2006-07-10
Hi all,

I'm wanting to install Ubuntu 6.06 on my desktop (I already had it installed on my laptop), and I'm not sure which CD to use.  I come from a Fedora Core background, but I've been pleased with Ubuntu on the laptop.  I need to be able to have a LAMP environment, but I also need all the other things a desktop needs, such as openoffice, email, etc.  Do I use the Server CD, and if so, will I need to install all the other things I need using Synaptic?

Sean

---

### Post by Maggot on 2006-07-10
Unless you want to run a non-GUI server, don't install Server. You will want either Desktop or Alternate. Desktop is a Live CD with the option to do a hard drive install as well. I used it with no problems.

---

### Post by Rule on 2006-07-10
you could do a server install which has a LAMP installation option, then once it's all setup you can install either ubuntu-desktop (Gnome) kubuntu-desktop (KDE) or xubuntu (XFCE).

---

### Post by shendric on 2006-07-11
> **Maggot said:**
> Unless you want to run a non-GUI server, don't install Server. You will want either Desktop or Alternate. Desktop is a Live CD with the option to do a hard drive install as well. I used it with no problems.

So, the Alternate sounds like the best way to go, I guess.  Does it give the option of installing Apache, MySQL, and PHP?

Sean

---

### Post by shendric on 2006-07-11
One other thing: the main reason I'm thinking of the alternate install CD is that I've already got a partition on the drive I'm wanting to install Ubuntu on.  I'd like to keep that partition safe, and I wasn't sure how much control over partitioning that the Desktop installation would give me.  Is that the case, or would the Desktop installation work just as well?  I just read documentation for how to install LAMP on Ubuntu once it's installed, so that seems straightforward.

---

### Post by Maggot on 2006-07-11
> **shendric said:**
> So, the Alternate sounds like the best way to go, I guess.  Does it give the option of installing Apache, MySQL, and PHP?

Not during the install but you can use the program Synaptic to install it afterwards from the repo's.

> **shendric said:**
> I wasn't sure how much control over partitioning that the Desktop installation would give me.  Is that the case, or would the Desktop installation work just as well? 

I 'believe' Desktop/Alternate give you the same options for partition. If you have existing partitions make sure you select manual partitioning no matter which one you use.

---

### Post by shendric on 2006-07-11
> **Maggot said:**
> Not during the install but you can use the program Synaptic to install it afterwards from the repo's.



I 'believe' Desktop/Alternate give you the same options for partition. If you have existing partitions make sure you select manual partitioning no matter which one you use.

Maybe I'll just go with the Desktop, then, if Alternate won't give me anything more than Desktop, in terms of my needs.  I choose manual partitioning, and then I'll be able to just select which partition I want to install on, right?  I've read the docs, but it doesn't ever say that, specifically (at least I couldn't see it), just tells you how to resize partitions, which I don't need to do.

---

### Post by Maggot on 2006-07-11
> **shendric said:**
> I choose manual partitioning, and then I'll be able to just select which partition I want to install on, right? 

Correct.

I'm always paranoid when installing linux with the 'automatic' partitioning....I prefer to be in control that way I can only blame myself :mrgreen:

---

### Post by shendric on 2006-07-11
> **Maggot said:**
> Correct.

I'm always paranoid when installing linux with the 'automatic' partitioning....I prefer to be in control that way I can only blame myself :mrgreen:

Me, too.  I'm backing everything up, just in case.  Thanks.

---

