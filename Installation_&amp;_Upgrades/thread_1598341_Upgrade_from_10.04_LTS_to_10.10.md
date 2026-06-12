---
title: "Upgrade from 10.04 LTS to 10.10"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by Shibbir on 2010-10-16
I'm running 10.04 LTS on Dell Inspiron N4010 notebook. Can I upgrade from Ubuntu 10.04 LTS to Ubuntu 10.10? If it is possible then can I still have the LTS facility?

Network Manager Applet 0.8 is disable from the panel. But it is runnig in background. The startup applicatios shows that Network Manager is enabled in startup. How can I see the actual network manager interface and bring back to the panel?

---

### Post by TBABill on 2010-10-16
Yes you can upgrade to 10.10 from 10.04. In a terminal:

> update-manager -d

You won't have LTS with 10.10. Only LTS versions (6.04, 8.04, 10.04 and the future 12.04, for example) offer 3 years support. You only get 18 months with versions between LTS versions. 

I am looking for the other answer and will post back if I find it (network mgr on the panel).

---

### Post by jleach on 2010-10-16
My only comment is that if Lucid is working well, you might want to wait. I upgraded to Maverick netbook edition and it was slower, crashed and no where near as good.  I have spent this afternoon putting Lucid back on as it works well, is fast and stable!

---

### Post by mionescu on 2010-10-16
To bring back NetworkManager, try to press Alt-F2 and then run "nm-applet".

---

### Post by TBABill on 2010-10-16
I'm with jleach. One machine upgraded fine and another was a horrible experience. Different brands, but the one that went poorly was a fresh install. Wireless would not work even though it detected my network. It would just not connect and nothing I found anywhere could get me past that. Wired was fine but I couldn't leave a cord lying across a room till the problem with 10.10 was figured out. Many are suffering the exact same problem with various brands of wireless devices so I believe it is worth waiting for. 

I usually give an upgrade a month but this time I jumped in. One worked, one did not, so I reinstalled 10.04 on both and will wait a while till the bugs are worked out.

---

