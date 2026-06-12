---
title: "Problems with WOL (Wake On Lan)"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by MortenSJ on 2012-10-21
I installed WOL on my Ubuntu server and it works fine. The only problem i have is that every second time i shutdown my computer it reboots instead of shutting down?

I shutdown and it reebots, i shutdown and it stays down. I wake it with WOL and it boots. I shutdown and it restarts, i shutdown and it stays down. Why is it only doing it every second time?

---

### Post by MortenSJ on 2012-10-21
Okay. It got i to wake up everytime, but every second time i shutdown my computer it restarts?

I added these lines in my /etc/network/interfaces

post-up /sbin/ethtool -s eth0 wol g
post-down /sbin/ethtool -s eth0 wol g

---

### Post by coockiejr on 2012-12-06
> **MortenSJ said:**
> Okay. It got i to wake up everytime, but every second time i shutdown my computer it restarts?

I added these lines in my /etc/network/interfaces

post-up /sbin/ethtool -s eth0 wol g
post-down /sbin/ethtool -s eth0 wol g



I have the same problem, did you manage to find a solution?

Thanks.

---

### Post by madkazas on 2013-03-13
> **coockiejr said:**
> I have the same problem, did you manage to find a solution?

Thanks.
I have Realtec LAN  8111E  and my solution for that problem :
    Get new drivers form [realtec.com]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168<br>RTL8111C/RTL8111CP/RTL8111D(L)<br>RTL8168C/RTL8111DP") (I get ver 8.035.00 from 2012/12/21) 
    and install it :)

Work perfectly for me - second and more shutdown and zero computer restarts [COLOR=#000000][/COLOR]

---

