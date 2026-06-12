---
title: "Is it possible to use packages from Ubuntu 10.10?"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by KaiZ51 on 2010-09-14
If so how?

I have a few things I want to have at the latest stable versions, like GIMP, and others.

---

### Post by howefield on 2010-09-14
> **KaiZ51 said:**
> Is it possible to use packages from Ubuntu 10.10?

In Maverick ? yes.

What version are you running ?

Using them elsewhere might mean dependency issues.

Most applications will have a repository that you can use to get the latest version number.

---

### Post by sxmaxchine on 2010-09-14
Im pretty sure they are all debian based programs so they should work fine on lucid as well.

However as for doing it, that could be a bit tricky.

You can try downloading the source for new gimp and then installing it from that.

or if you just want the standard already released stable version of gimp just open a terminal and type sudo apt-get install gimp

---

### Post by KaiZ51 on 2010-09-14
> **howefield said:**
> In Maverick ? yes.

What version are you running ?

Using them elsewhere might mean dependency issues.

Most applications will have a repository that you can use to get the latest version number.

Sorry, forgot to mention. I use 10.04.

Is there a way to fix those dependency issues?

Also, the repository you're talking about is PPA's, right?

> **sxmaxchine said:**
> Im pretty sure they are all debian based programs so they should work fine on lucid as well.

However as for doing it, that could be a bit tricky.

You can try downloading the source for new gimp and then installing it from that.

or if you just want the standard already released stable version of gimp just open a terminal and type sudo apt-get install gimp

Well, I didn't really want to have to compile anything...

---

### Post by howefield on 2010-09-14
> **KaiZ51 said:**
> Also, the repository you're talking about is PPA's, right?

Yes, that what I was referring to, although not all are a PPA. You mentioned gimp, I believe there is one for that but I haven't looked to deeply. Gimp is one that I can live with being slightly out of dateh.

---

