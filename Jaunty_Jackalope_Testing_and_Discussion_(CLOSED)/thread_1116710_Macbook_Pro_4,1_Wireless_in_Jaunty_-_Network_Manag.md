---
title: "Macbook Pro 4,1 Wireless in Jaunty - Network Manager doesn't give an option"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xyverz on 2009-04-05
I'm running 64-bit Jaunty beta on my 4,1 MacBook Pro, and according to System -> Administration -> Hardware Drivers, the Broadcom STA wireless driver is not only installed, but active.  Sadly, the Network Manager does not show any wireless connection at all.

I've gone into the system preferences and added my wireless networks, but again, Network Manager does not give me the option of choosing my wireless network.

lspci returns:```
0b:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)

```

lsmod shows the wl module loaded, but I don't have any other network devices available other than eth0 and lo.

I'd really like to get this thing going - I'm enjoying using Jaunty on my desktop box so far - but not being able to use the wireless will kill any chances of runing this on my trusty MacBook Pro.

Sadly, these forums are almost impossible to search. Google has provided a few hits, but nothing related to my plight.  Any help would be greatly appreciated. :-)

--X...

---

### Post by xyverz on 2009-04-05
Well, this was interesting...  I decided try deactivating then reactivating the driver.  After a reboot things seemed to work well.  The one thing that's bothering me is that after the wireless started working, it kept prompting me for my WPA/WPA2 password.  I was finally able to connect after selecting my network from the list.

I guess we can mark this one as solved for now.

---

### Post by xyverz on 2009-04-05
Network Manager *still* keeps asking for my password.  I *KNOW* I've entered it in correctly.

I've even gone so far as to trying WICD.  It's all an effort in futility.  I don't understand why - even though I know it works - it has to taunt me with past successes and tell me to take a hike.

Jaunty, you kill me.

---

### Post by xyverz on 2009-04-08
Well, it looks like the problem is more with wpa/wpa2 - more likely the wpasupplicant package.  When I have my WAP set to WEP or no security at all, everything works just fine.

I understand that it was working just fine in one of the alphas, but for some reason with the beta it's broken again.

---

### Post by Eclipse. on 2009-04-08
> **xyverz said:**
> Well, it looks like the problem is more with wpa/wpa2 - more likely the wpasupplicant package.  When I have my WAP set to WEP or no security at all, everything works just fine.

I understand that it was working just fine in one of the alphas, but for some reason with the beta it's broken again.

Report a bug, regressions are taken very seriously.

---

### Post by xyverz on 2009-04-11
I'm pretty sure there's one filed.  I've seen the launchpad info for this package, and it's currently given high priority under Jaunty.

---

