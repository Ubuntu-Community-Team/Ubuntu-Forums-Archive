---
title: "PPA can be a problem for Lucid?"
date: 2010-02-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by markinf on 2010-02-07
Guys I have about 18 PPAs (Most added by Ubuntu-Tweak, 12), so I was thining when I had PPAs on Hardy and Intrepid both my upgrades failed :'(

This time I'm scared do you think that the breaking will happen again because of the ppa's?

And I hate do to clean install :'(

Any Ideas of what I can do to not have this problem anymore?

---

### Post by sudoer541 on 2010-02-07
dont use ubuntu tweak, or at least ask the UT author about this because it could be a bug in the proggy

---

### Post by Warpnow on 2010-02-08
If your PPAs don't support lucid, then upgrading them via changing the word will result in update errors. If you leave them at Karmic, it could result in dependency problems.

The PPA will only break Lucid if the PPAs lack support for Lucid.

---

### Post by cariboo on 2010-02-08
The upgrade process should disable your ppa's. It would probably be a good idea to backup your sources list, as the upgrade process will over-write it.

---

### Post by juancarlospaco on 2010-02-08
PPA added by the ppa: command will be auto-disabled, 
but added by third party app or manually editing the sources not.

---

