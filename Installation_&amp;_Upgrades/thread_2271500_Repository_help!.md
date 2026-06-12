---
title: "Repository help!"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by Kenneth_Benson on 2015-03-30
I have a disconnected pc with Ubuntu on it (dual boot with win 7). I bought a set of dvds with the 14.04 repository on them. Can anyone tell me how to create a repository _directory_ from those dvds? As in copy the stuff off the dvds to a directory on the machine that aptitude/apt-get/synaptic will believe is a repository and use it instead of online? I know that is approx. 60GB of stuff but I have the space. I want to keep the dvds stored to keep them from getting scratched.

---

### Post by grahammechanical on 2015-03-30
Go to System Settings>Software and Updates>Other Software tab and click Add Volume to add the DVDs as a repository or click Add to put in a location of the repository.

Regards.

---

### Post by ian-weisser on 2015-03-31
> **Kenneth_Benson said:**
> Can anyone tell me how to create a repository _directory_ from those dvds? As in copy the stuff off the dvds to a directory on the machine that aptitude/apt-get/synaptic will believe is a repository and use it instead of online?

Use the local package cache instead of a 'repository directory'
Copy packages you wish to install to /var/cache/apt/archives . Apt looks there first.
I suppose you could copy all 60GB of debs to that directory, if you really want to.

---

### Post by Kenneth_Benson on 2015-03-31
@ grahammechanical, actually I don't want the dvds to BE the repository, I want to take the files off the dvds and make THEM the repository.
@ ian-weisser, thanks, I'll use that till I get the other figured out.

---

### Post by Kenneth_Benson on 2015-04-06
Ok, I'm not positive but this might be the answer I (and others) need. There is a package called reprepro that looks like it might do what I need. I'm downloading it and looking for docs to read up on it.
I'll let you know if it's the answer.



<What's the answer to Life, The Universe and Everything?> :lolflag:

---

