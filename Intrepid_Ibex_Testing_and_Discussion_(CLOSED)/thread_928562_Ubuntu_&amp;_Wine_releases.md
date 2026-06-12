---
title: "Ubuntu &amp; Wine releases"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2008-09-24
I've searched the forums and can't find any information on what version of Wine Intrepid will ship with.

I've checked launchpad and the latest version seems to be 1.0.0, whereas the latest Wine released is 1.1.5.

When in the Ubuntu release cycle is the version of Wine fixed for released, and what version will ship with Intrepid?

TIA

---

### Post by Sand &amp; Mercury on 2008-09-24
I'd assume it won't ship with Wine, but they'll put whatever is latest in the repositories when it's time to launch.

---

### Post by prshah on 2008-09-24
> **Col-1023 said:**
> 
I've checked launchpad and the latest version seems to be 1.0.0, whereas the latest Wine released is 1.1.5.


Why not just add the wine repositories to your system? ([Instructions]("http://www.winehq.org/site/download-deb")) That way you will always have the latest release of wine delivered through update-manager```
wine --version
wine-1.1.5

```

---

### Post by Col-1023 on 2008-09-24
Thanks for your replies.

I hadn't looked into adding Wine to the sourcelist since I thought there were problems with doing that in the past, namely newer wine versions conflicting with ubuntu and then you had to go through all sorts of trouble to revert to an earlier wine version.

Is updating Wine using the sourcelist a fairly painless process now?

---

### Post by prshah on 2008-09-24
> **Col-1023 said:**
> 
I hadn't looked into adding Wine to the sourcelist 
Is updating Wine using the sourcelist a fairly painless process now?

It always was/is for me. Never had a problem.

---

### Post by MALEADt on 2008-09-24
> **prshah said:**
> It always was/is for me. Never had a problem.

Same in here, the WineHQ repository always worked flawlessly.

---

