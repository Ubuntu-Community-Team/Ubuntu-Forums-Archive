---
title: "error uninstalling wine"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by rhxht on 2008-03-18
Hey, I'm pretty new to Ubuntu but so far I've been able to figure out my issues with this site, google and trial and error. I cant find anything that helps me with a problem that just came up however.

Basically I installed Warcraft 3 with wine and found out that I couldn't get on Bnet. After googling it, I found that apparently the latest version doesnt work with Bnet or somesuch and I decided to get an older version. So I download it and start to remove the old version with synaptic but the removal hangs at the end for a couple of minutes and then tells me:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then ran sudo dpkg --configure -a and i get this:

Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135

Ive tried a lot of things from other threads but out of literally all of them the only command that doesnt result in "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" is 'sudo apt-get clean' which does nothing apparently.

Any ideas :confused: ??

edit: Also wanted to note that Wine still shows up in Applications, but only programs, no configure or browse etc.

---

### Post by rhxht on 2008-03-18
Bumping before bed

---

