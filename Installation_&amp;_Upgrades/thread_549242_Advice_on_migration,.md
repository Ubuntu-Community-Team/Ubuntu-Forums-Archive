---
title: "Advice on migration,"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Uriel2006 on 2007-09-12
Hello, 

i was using Ubuntu 7.04 on my AMD64 laptop until the last week , for daily work. I was using th 64 bit one.

Now my company gave me a different laptop (one new one), but the problem is this is a 32 bit one.

So i can't simply do a disk dump, and i'm installing the feisty fawn on the new laptop using the CD.

Now my problem is: what about softare i installed on the old system? I would like to repeat installations, but they're a lot of software from a lot of repositories.

There is one way to export the list of the installed software, put it in the new system and then  download the same software (using the same sources.list, of course)? I mean, with the official/standard way to install (i even used synaptic/apt to install)

thanks in advance,

Uriel

---

### Post by Irihapeti on 2007-09-12
In Synaptic, there's an option under the "file" menu to "save markings". If you check the "save full state, not only changes" box, Synaptic produces a list of everything that's installed in your system. You can later import that list by using "Read markings".

I've used the function myself (without that option checked) only on a set of packages I wanted to install, not the whole system, so I can't say for sure how it would go. The markings file, by the way, is just plain text so it's easy to read through beforehand if you need to.

HTH
Irihapeti

---

