---
title: "Removing OOO programs"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by iv76erson03 on 2010-02-17
I'm running a netbook with limited hard drive space and I don't want OOO base or math on my computer. I tried removing these through synaptic and none of them work. Can someone tell me the best way to remove base and math while keeping the other programs? Thanks.

---

### Post by mikewhatever on 2010-02-17
What do you mean by 'none of them work'? What's was the problem exactly? Could it have been that the said programs didn't work after you removed them? If so, isn't that an expected behavior?

---

### Post by gdonwallace on 2010-02-17
Not being familiar with the netbook remix, I can only say what I know about the normal install.  If the remix has the add/remove (Software store) and OOO was pre-installed, then you should be able to pick and choose what applications from OOO you want to remove.  In Ubuntu, each OOO app is installed separately, and the software store has a way to remove each individual app.  

In the remix, I don't know.  You might try to remove OOO completely, reinstall and do a custom and see if it gives you the option to choose the applications that you want.

Thats the only advice I can think of.

---

### Post by iv76erson03 on 2010-02-17
I guess I should have been more specific, sorry:

I upgraded too OOO 3.2 because there was a feature I needed. Using the .deb package from the OOO website, it installs every module they have. I went into synaptic and attempted to remove base and math, only to find out that calc and writer no longer worked. Must have gotten the wrong thing. When I do a custom install, each module doesn't show up in the Ubuntu software center like the original install did. I was hoping someone knew a terminal command or something to just remove base and math. 

sudo apt-get remove openoffice.org-base 

didn't work.

---

### Post by Hagar Delest on 2010-02-17
Anyway, you won't spare much room. Most of the code is made of shared libraries. Base is around 10MB and Math much less.

---

