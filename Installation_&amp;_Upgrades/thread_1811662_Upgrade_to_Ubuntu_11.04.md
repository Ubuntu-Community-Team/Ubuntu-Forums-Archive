---
title: "Upgrade to Ubuntu 11.04"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by techtabu on 2011-07-25
I am new to Ubuntu, So I end up in asking this questions. I have Ubuntu 10.10 installed inside windows as dual boot. Now 11.04 released, if I upgrade to 11.04 will it work as it works now? Or will it change any boot loader in Windows? Since I am using HP with Windows 7, I can't do parallel boot to maintain the warranty. Thanks in advance.

---

### Post by ~!geek!~ on 2011-07-25
You installed ubuntu 10.10 after getting your system. So you have already made max changes that you had to have ubuntu. Now upgrading it to 11.04 will only write on the bootloader that previous version had already done on. So either you already lost your *warranty thing* you mentioned or you can't lose it by upgrading. 

*The above statements are only logically correct to the extent I know, may differ in reality, So wait for some more replies as its about your warranty.*

---

### Post by Mark Phelps on 2011-07-25
> **techtabu said:**
> I am new to Ubuntu, So I end up in asking this questions. I have Ubuntu 10.10 installed inside windows as dual boot. Now 11.04 released, if I upgrade to 11.04 will it work as it works now? Or will it change any boot loader in Windows? 
Since you said "inside", I'm presuming you installed using Wubi.  It's generally a BAD idea to upgrade such installations to new Ubuntu versions. You would do better removing the installation you have and installing Ubuntu again from scratch.
> Since I am using HP with Windows 7, I can't do parallel boot to maintain the warranty. Thanks in advance.
The interpretation of warranty "breakage" is almost entirely in the hands of the warranty provider, so no one can really say how they will interpret what you did.

But ... that said, since you installed Ubuntu the same way you would install any other application, for them to say that broke your warranty, would be no different from them saying that installing Firefox or Chrome broke your warranty.

---

### Post by techtabu on 2011-07-25
> **Mark Phelps said:**
> Since you said "inside", I'm presuming you installed using Wubi.  It's generally a BAD idea to upgrade such installations to new Ubuntu versions. You would do better removing the installation you have and installing Ubuntu again from scratch. 
Yeah, That's what I did. And that's what I wanted to know. Every time I check upgrade options, Ubuntu asks to upgrade to 11.04. But I don't want it to screw up the Windows boot loader. 

> 
The interpretation of warranty "breakage" is almost entirely in the hands of the warranty provider, so no one can really say how they will interpret what you did.

But ... that said, since you installed Ubuntu the same way you would install any other application, for them to say that broke your warranty, would be no different from them saying that installing Firefox or Chrome broke your warranty.

I think I was kind of bizarre in explanations. Since I installed Ubuntu using wubi, it does not break my warranty as you said. I wanted to keep all the crap softwares HP installed and the partitions (Still I can make partitions, but only as extensions which I think Linux does not identify as a partition for installation) they made for their system files to keep their warranty. Last time when I did I made partition from within Ubuntu and end up meshing up with Windows bootloader, and warned by HP not to do so again if I need to keep the warranty. 

I think now my option is uninstall previous version and to install it again?

---

### Post by dino99 on 2011-07-25
you only have to decide if you still want to be their slave (pure marketing scaring)

---

### Post by blackbird3216 on 2011-07-25
Well, I am not very familiar with wubi, but it seems that the general consensus is that you will need to remove (id est uninstall) your current installation before you upgrade to Natty. Although the builtin upgrade tool may work, I have found that I don't have much success with it. 

As for "breaking your warranty," I really wouldn't worry about it. The only thing you might want to do is backup the "backup" partition, which is usually an OEM substitution for not having to provide backup discs like they used to do. Unfortunately, these backup partitions generally have crapware (e.g. HP utilities), so it might be a great idea to call up HP to see if they are willing to provide a Windows 7 (I'm assuming) disc free of charge. 

If you do decide to have Windows and Linux run side by side, it is generally not an issue, because Grub and other linux bootloaders are designed to accomodate the usage of Windows. What many users seem to think is a problem is when they install or upgrade windows after they have linux on their computers, and then they claim that their booting sequence is broken.

---

