---
title: "Linux error, dont know much"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by johnjohn87 on 2008-05-08
i just got the new linux and i cant see any video on the web or streaming video.  and when i try to install any updates this pops up.  


 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

can anyone help?

---

### Post by divague on 2008-05-08
go to Applications->Accessories->Terminal and type

sudo dpkg --configure -a

it'll ask for your password enter it, and this should fix your update problem

---

### Post by johnjohn87 on 2008-05-08
sweet thanks, its workin now.  i dont know anything about computers really.  will that fix my streaming video too?

---

### Post by divague on 2008-05-08
No, for the videos you have to install the codecs.Go to System->Administration->Synaptic package manager , click on the reload button when it finishes click on search and look for ubuntu-restricted-extras and install it, i think that should do for the videos.

---

### Post by johnjohn87 on 2008-05-08
huh, i did all that and still no video. on youtube it says i either turned javascript off or dont have the latest flash player. any ideas?

---

### Post by divague on 2008-05-08
try restarting your browser

---

