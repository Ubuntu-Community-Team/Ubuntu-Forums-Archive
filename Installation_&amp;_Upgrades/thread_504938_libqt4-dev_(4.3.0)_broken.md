---
title: "libqt4-dev (4.3.0) broken?"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by seth.jackson on 2007-07-19
hi all,

my system (feisty) (kubuntu)  recently upgraded from libqt4-dev 4.2.3 to 4.3, and in doing so seems to have broken qt+opengl rendering in a project of mine.  i have tried to force the synaptic package manager to downgrade to 4.2.3, but it greys out and turns back into version 4.3.0. 

aptitude reports that libqt4-dev (4.3.0) is "iB"...   i need it to be not broken!  or, i need it to be 4.2.3!  


any advice?

thanks,

seth

---

### Post by davidjmayo on 2007-07-20
In synaptic have you tried edit==>fix broken packages?

---

### Post by seth.jackson on 2007-07-20
unfortunately nothing happens when clicking 'fix broken'



ah...   the adept updater says a new version is out already!   so the package itself was broken.  a new version replaced it today ( only took 2 days!  Ubuntu community rocks! )

i think that synaptic couldn't fix the install because the package itself had been broken.  all is well now.  

thank you.

---

