---
title: "Installing gcc keeps asking for Breezy Badger CD!"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by gbacich on 2006-04-26
Im a total noob...so please forgive such a (probably) simple question.

I am trying to install a c compiler (hence, gcc) and my search has led me to the synaptic file manager. However when I select gcc and the other components for it it asks me to insert the breezy badger cd.

It also does this when I try to install a downloaded debian package.

I am assuming I am doing something wrong because I am connected to the internet and installed Ubuntu from the internet. So I am assuming I can install packages from the internet without the use of a cd.

Am I correct in assuming I dont need to burn an installation cd of Ubuntu and can just download these packages? Moreover, how can I resolve this problem and install gcc?

Thank you all very much,
GB

---

### Post by Sef on 2006-04-26
To solve your problem do this:

From Synaptic, download build-essential

or

From the terminal, Applications > Accessories > Terminal

sudo apt-get update

sudo apt-get install build-essential

---

