---
title: "nvidia...solaris yes LL no"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rtalcott on 2010-02-06
After having my grub disaster I managed to recover...pre-disaster nvidia 190 (nvidia-current I believe) and 195 (sevenmachines ppa) worked. Post-disaster I reinstalled using the Feb. 3 daily build and get nothing but lock-ups after I install any nvidia or nouveau.  The current OpenSolaris Alpha installs nvidia 190 and that runs without a problem.

I am using an evga 730a board...any suggestions would be appreciated...AND...this machine ran nvidia drivers fine when I had 9.10 on this machine...

rt

---

### Post by dagrump on 2010-02-06
Remove plymouth, oh don't hit the enter key till you do or it will freeze. 
Again, still, more...

---

### Post by rtalcott on 2010-02-06
Tried a reinstall with the latest daily build...gives me nothing but graphical garbage on start-up...guess I'll go back to the feb. 3 iso....
rt

---

### Post by rtalcott on 2010-02-06
Mr. dagrump...
Thank You...that worked...removing plymouth!
And...I will try to stay off the lawn!
rt

---

### Post by dagrump on 2010-02-06
You're welcome, & the lawn is covered w/ snow.

---

