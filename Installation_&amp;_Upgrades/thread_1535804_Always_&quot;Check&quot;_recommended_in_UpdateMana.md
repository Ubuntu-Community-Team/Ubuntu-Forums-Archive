---
title: "Always &quot;Check&quot; recommended in UpdateManager before &quot;Install Updates&quot;?"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by pstein on 2010-07-21
When I call Update Manager then there is a button "check".
I guess this button updates the local internal software version repository.
So it is always recommended to do a "Check" before the actual "Install Updates" ?
 
Why is there a "check" button at all?
 
Should this be that automatically included in the "Install Update" function?
 
Peter

---

### Post by tommcd on 2010-07-21
Open a terminal and run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If the updates install successfully then there is no problem. That "check" button runs the command "*sudo apt-get update*"
Write back if you need more help.

---

