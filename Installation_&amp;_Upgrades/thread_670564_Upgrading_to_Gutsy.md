---
title: "Upgrading to Gutsy"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by newbiexubunt on 2008-01-17
I'm finally running Feisty Fawn on my laptop, but I don't know how to upgrade successfully to Gutsy Gibbon *without* crashing.  Can anyone help?:)

---

### Post by linuxwizard on 2008-01-17
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by zvacet on 2008-01-17
I will do it with alternate CD,because if something goes wrong you allways have disc to do fresh install.But this is just one of options.

---

### Post by Pumalite on 2008-01-17
Another option is this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by newbiexubunt on 2008-01-20
Oh, I forgot to mention, I have no Internet on my laptop.  Also, the laptop suddenly doesn't type ' (apostrophe) anymore even though it worked fine before.  Please help soon!

---

### Post by zvacet on 2008-01-21
If you can not bring internet to laptop,can you bring laptop to the internet?

---

### Post by Pumalite on 2008-01-21
You can get wired anywhere if you want it bad enough.

---

### Post by newbiexubunt on 2008-01-21
Thanks everyone.  I just had an idea an hour ago:  I downloaded the most recent version of Puppy Linux.  Will it work?

---

### Post by Pumalite on 2008-01-21
Puppy is great as a light, small distro, but is not Ubuntu.

---

### Post by newbiexubunt on 2008-01-27
> **Pumalite said:**
> Puppy is great as a light, small distro, but is not Ubuntu.
I know it isn't Ubuntu, but I'm getting, well, desperate. Could I use Kubuntu, or do I need a lot of memory?  Sorry I'm bothering everyone!

---

### Post by Pumalite on 2008-01-27
What is it?. You don't like Feisty?

---

