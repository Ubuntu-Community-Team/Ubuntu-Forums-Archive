---
title: "Problem with installing SKype"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by MicroBoy on 2008-03-26
When I try to install skype-debian_2.0.0.63-1_i386.deb on my ubuntu it says: "Error: Dependency is not satisfiable: libasound2", I updated libasound2 I reinstalled it but it's the same problem again.

---

### Post by Pumalite on 2008-03-26
Try Synaptic

---

### Post by MicroBoy on 2008-03-26
[B]It doesn't find me anything with the name "skype"

my ubuntu is 6.06 LTS[/B]

---

### Post by fela on 2008-03-26
you could enable the medibuntu repository (it has skype in it), howto [here]("https://help.ubuntu.com/community/Medibuntu")

then you could just ```
sudo apt-get install skype
``` and your done...

---

### Post by MicroBoy on 2008-03-26
> **fela said:**
> you could enable the medibuntu repository (it has skype in it), howto [here]("https://help.ubuntu.com/community/Medibuntu")

then you could just ```
sudo apt-get install skype
``` and your done...**Thnx a lot :**)

---

### Post by fela on 2008-03-26
> **MicroBoy said:**
> **Thnx a lot :**)

did it work? remember to click the thanks button if someone gives a solution...it's polite :D

---

### Post by MicroBoy on 2008-03-26
**How can i upgrade Skype because this version is too old.**
***Yes it works and I clicked the button ok.***

---

### Post by fela on 2008-03-26
I reckon you have an old version of skype cause your using a old version of Ubuntu (dapper, right?). Skype's closed source, so you can't compile from latest source code version. That means, IMO, that the easiest way to upgrade skype is to upgrade your system.

And i think it'd be time for an upgrade anyway right? you're 2 releases (nearly 3) outta date...

---

### Post by MicroBoy on 2008-03-26
> **fela said:**
> I reckon you have an old version of skype cause your using a old version of Ubuntu (dapper, right?). Skype's closed source, so you can't compile from latest source code version. That means, IMO, that the easiest way to upgrade skype is to upgrade your system.

**And i think it'd be time for an upgrade anyway right? you're 2 releases (nearly 3) outta date...Aha ok Thnx i started the upgrade to 6.10 soon I will upgrade to 7.10 ok**

---

### Post by fela on 2008-03-26
> **MicroBoy said:**
> Aha ok Thnx i started the upgrade to 6.10 soon I will upgrade to 7.10 ok[/B]

ok well i thought you can go straight from 6.06 (or any old version) to the latest? i don't think you have to use all the other versions as stepping stones...anyway

---

### Post by MicroBoy on 2008-03-26
> **fela said:**
> ok well i thought you can go straight from 6.06 (or any old version) to the latest? i don't think you have to use all the other versions as stepping stones...anyway[B]I didn't see on the internet from 6.06 to 7.10. Just from 6.06 to 6.10 etc.. Using the internet I mean.
[/B]

---

### Post by simonlugi on 2008-04-05
I have tried to install skype using Xubuntu and followed the advice given in this thread.

I get the message shown below in Terminal

The following packages have unmet dependencies:
  skype: Depends: libqt4-gui (>= 4.3.2) but it is not going to be installed
E: Broken packages

Please can some one help a beginner.
Thanks simon

---

