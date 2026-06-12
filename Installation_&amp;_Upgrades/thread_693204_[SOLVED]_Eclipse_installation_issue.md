---
title: "[SOLVED] Eclipse installation issue"
date: 2008-02-10
forum: Installation &amp; Upgrades
---

### Post by Fistols on 2008-02-10
Hi, I am trying to install eclipse. I downloaded it from the web site and tried to install it using the Command Line and I couldn't get it to work. So then I tried doing it with Add/remove software, and it tells me there is a software conflict and to use Synaptic package manager. I dont know what it wants me to do. Please Help.

-Derek

---

### Post by varnil on 2008-02-10
Ensure that you downloaded the linux version for amd 64 (guessing you did that )
extract it somewhere (in nautilus right click extract here). open the terminal. cd to the place you extracted it. then ./eclipse
If this doesn't work check your dependencies (YOU DO HAVE JAVA RIGHT???). Those are your ONLY possible sources of error
PS: Since add/remove is telling you there's a conflict dependencies must be the problem, thus close add/remove open synaptic (system>admin>synaptic package mangager) search for eclipse, mark it for install a popup should show up telling you what else must be installed and finally hit ok and wait for install to finish

---

### Post by Fistols on 2008-02-11
Ok, that did it. Thanks for your help.

---

### Post by www.rzr.online.fr on 2008-02-13
Are there unofficial "repack' latest eclipse packages available in .deb format somewhere ?
--
[http://rzr.online.fr/q/SWT](http://rzr.online.fr/q/SWT)

---

