---
title: "Installation of Rsyslog Source Files"
date: 2012-03-22
forum: Installation &amp; Upgrades
---

### Post by discovery101 on 2012-03-22
I have recently installed Ubuntu 11.10 and I understand that it comes pre-installed with a minimal and compiled set of files for rsyslog. 

I would like to make some modifications to the various plug-in modules.  However, I am unclear on how to install the rsyslog source code. I have downloaded the original software package (.tar.gz) from the ubuntu repository, but if I run the /configure steps, will that not just install a new copy of the program under usr/bin , usr/lib, etc. versus where the compiled code is currently located under <root>/lib , <root>/etc.? 

Or, asking the same question in a slightly different way, if I would like to make changes, do I need to inactivate the pre-installed version of rsyslog and just compile and operate a new installed version, or is there a way (let me clarify, and easy way for a new linux user), to install the source code using the current Ubuntu configuration?

Thanks for any advice or help in advance !

---

### Post by oldos2er on 2012-03-23
Installing from source *usually* will install to /usr/local/*. That is using the command **sudo make install**.

---

### Post by discovery101 on 2012-03-23
Thanks Ann.

The problem, as I understand it, is that when they compiled Ubuntu, they did not install rsyslog into that location. It looks like they made it part of the base OS. 

So, if I do the sudo make install, I think that I will be installing a 2nd copy. What I would like to do, is modify the installed base copy.

I appreciate your help.

---

### Post by oldos2er on 2012-03-24
I'm sure there's a way to modify the existing rsyslog, but if I were you I'd take the easy way out: uninstall rsyslog using 'apt-get remove', then compile and install the source code version.

I am not a programmer, so it might be best if you wait for a second opinion!

---

