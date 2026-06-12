---
title: "No network after putting Jaunty on EeePC 900"
date: 2009-03-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dave-B on 2009-03-01
Hi,

I upgraded my EeePC 900 from Easy Peasy to Jaunty yesterday and now 
it can't get wired or wireless network connection.

The modules appear to be loading and the hardware working - both atl2 and ath5k are present in lsmod. NetworkManager can see my wireless network, but fails to connect to it, and I get notifications of failing to connect with wired network as well.

Where should I be looking to identify the problem?

Cheers,
Dave.

---

### Post by tahina on 2009-03-02
Since nobody has said anything yet, I'll volunteer my possibly off-topic and misleading observations...

I have an EeePC 701 and I must *de-activate* the proprietary atheros-driver from System>Administration>Hardware Drivers and then reboot to get working wifi. 

Your problem doesn't sound exactly the same, with the Ethernet not working, for example, so my solution does probably not fit your problem, but since nobody else has anything to say, I thought I'd reply anyway.

---

### Post by nyarnon on 2009-03-02
Hi there I'm running a 1000h and after installing Jaunty I have to update through wired network first before the wifi comes available. Did you try that? I did notice that some modems with strong encryption can be a problem to connect to. Try stepping back to wep. Just to see if that works. Not as a solution.

---

