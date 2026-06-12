---
title: "How do I install a package placed on my computer using aptitude?"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by djRob on 2007-06-17
Hi everybody

I want to install a .deb package that I downloaded to the current directory, but how to do it using aptitude? I want to use aptitude because I read that Ubuntu doesn't like standard Debian packages.
When I try to run this command 
sudo aptitude install pdfedit_0.3.1-1_i386.deb

I get an error
Couldn't find any package whose name or description matched "pdfedit_0.3.1-1_i386.deb"

---

### Post by linfidel on 2007-06-17
> **djRob said:**
> Hi everybody

I want to install a .deb package that I downloaded to my computer, but how to do it using aptitude? I want to use aptitude because I read that Ubuntu doesn't like standard Debian packages.
When I try to run this command 
sudo aptitude install pdfedit_0.3.1-1_i386.deb

I get an error
Couldn't find any package whose name or description matched "pdfedit_0.3.1-1_i386.deb"I usually run aptitude in interactive mode, then search for packages.  You can search for pdfedit, then check what you want.  Or you can search with Synaptic first, then run aptitude.

But I suspect your reasoning may be flawed.  Ubuntu is based on Debian, and the package you are trying to install is a Debian package (.deb).  Synaptic and aptitude both use apt, I've been told.  But I have heard that aptitude handles uninstalling dependencies better - that is, it cleans up unused files better.  But I was told elsewhere in this forum that there are other ways to clean up, if needed, after the fact.  So, I'd use whichever one is easiest.

---

### Post by ajgreeny on 2007-06-17
"I want to use aptitude because I read that Ubuntu doesn't like standard Debian packages."

I think that is an oversimplification of the situation but one that is basically correct.  However, I think the only way to do what you want would be to copy the .deb file to **/var/cache/apt/archives** and then use aptitude (or synaptic) or even apt-get.  The system will find the package and deal with dependencies, but you may still have some difficulties with the package not working properly if it is a debian rather than a ubuntu .deb file.  Give it a try, and if it's a no-go you can easily uninstall it.

---

### Post by djRob on 2007-06-18
> **ajgreeny said:**
> However, I think the only way to do what you want would be to copy the .deb file to **/var/cache/apt/archives** and then use aptitude (or synaptic) or even apt-get.  The system will find the package and deal with dependencies, but you may still have some difficulties with the package not working properly if it is a debian rather than a ubuntu .deb file.  Give it a try, and if it's a no-go you can easily uninstall it.

I did that but I am still getting the same error. :neutral:

---

### Post by splot on 2007-06-20
Try dpkg -i blah.deb...I just tried it, seems to work but I won't know for sure til I get the actual app setup.

there's an option to use apt to do it too, but I don't remember the flags...prolly more likely to handle dependencies properly, if you can get someone to give you the flags/syntax. :)

Good Luck!

---

### Post by diatribe on 2007-06-20
splot is correct, you can also just doubleclick the deb and gdebi will install it; I've not had problems wth any debian .deb packages

---

