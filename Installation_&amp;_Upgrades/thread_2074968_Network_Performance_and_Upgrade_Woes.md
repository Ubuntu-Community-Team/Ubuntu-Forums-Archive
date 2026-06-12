---
title: "Network Performance and Upgrade Woes"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by technoholic on 2012-10-22
It has been a trying past few days. I have been running 11.10 for some time and the network performance has gotten worse over time. The PC has an onboard Realtek RTL8111/8168B network adapter. Reasoning it was the 8169 driver causing the problem, I decided to begin with an online upgrade to 12.04. That ended in disaster. No problem, I thought and downloaded the 21.10 DVD to install directly from it. That also ended in disaster.

To make a long story short, I fell back to 11.04 and replaced the 8169 driver with the 8168 version. Still network performance was terrible. In all instances, it acted like the ISP's DNS was out to lunch but I don't think that was the issue because other machines on the network were working OK. A post on this forum mentioned doing a cold boot to reset the LAN adapter. It was for a different chip set but it was midnight and I was desperate so I unplugged the machine and called it a night. This morning, the machine, still with 11.04, is running like gang busters with the reportedly  problematic 8169 driver. 

Now I'm really confused. Apparently the 8169 driver is not the problem. If the machine continues to perform like it is now, I will be a happy camper. I guess the thing to do now is just wait and see what develops. BTW, this is not a dual boot system. I hate MS windows!

---

### Post by technoholic on 2012-10-23
Update, this morning I updated to 11.10 using the online update procedure. It went off without a hitch. Network performance is still good and still with the r8169 driver for the onboard Realtek NIC. 

Now comes the scary part, going to 12.04. Reading this forum, it seems the best way to go is to do a complete install from the DVD. That is the route attempted earlier. One thing I encountered that time was the network connection dropping just before the installation began and I suspect that contributing to the trouble I had. 

Has anyone else encountered the network connection dropping at install condition?

---

### Post by technoholic on 2012-10-23
This must be my lucky day. I just performed an upgrade to 12.04 online and it went perfectly. After reboot, everything was as before; desktop, email, startup apps, bookmarks and cookies and network performance is still good even with the reportedly problematic r8169 driver.  This PC also has a Nvida display adapter. It too acquired the correct driver and is working error free.  

Lesson learned here seems to be the importance of having a good network connection with internet access for installations or upgrades to complete successfully. Just wish I could explain what was causing my network wierdness over last weekend.

---

### Post by technoholic on 2012-10-23
Even though I don't have a good explanation for what happened, this thread is being marked as solved, there's nothing more to add. Hope this experience is useful to somebody.

---

