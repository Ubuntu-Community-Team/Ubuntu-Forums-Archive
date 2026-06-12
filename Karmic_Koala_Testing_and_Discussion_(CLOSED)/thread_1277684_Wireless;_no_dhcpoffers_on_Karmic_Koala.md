---
title: "Wireless; no dhcpoffers on Karmic Koala"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dabbi2000 on 2009-09-28
I have a D-link USB wireless at home and which worked fine on 9.04

Now made a fresh install to 9.10 alpha 6

The device is found and the SSID of my network shows up in network manager but after about 20secs of trying to connect it gives up

so I try manually with dhclient wlan0 and it gives up returing

"No DHCPOFFERS received"

Nothing changed on router, only upgraded to 9.10


How can I debug this?

---

### Post by Michael.Godawski on 2009-09-28
Moved to Karmic. ;)

---

### Post by tommcd on 2009-10-03
> **dabbi2000 said:**
> 
...so I try manually with dhclient wlan0 and it gives up returing
"No DHCPOFFERS received"
How can I debug this?
First, make sure the proper drivers are being loaded for your wireless card. Then try using **wicd**. Get online with a wired connection if you can and install wicd. Note that this will remove network-manager.
I had problems getting online with my wireless in Karmic beta. Network manager did not even find my wireless card. Wicd got me online right away with no problems.

---

### Post by wilee-nilee on 2009-10-03
So I did a upgrade to Karmic today and no wireless with NW manager or wicd. I then used a fresh Karmic install with a daily release about a month old which has NW manager working and switched to wicd before updating so far so good, it is updating now I suspect this is going to work, I will post tomorrow whether it does.  Edit: This method worked,fully updated with wireless.

---

### Post by dabbi2000 on 2009-10-04
I'm completely clueless, I found out it was more unstable after waking up from suspend but now it doesn't matter any more. Completely random! I really think it has to do with unstable Karmic Koala driver.

I'll try wicd.

Can I then install network-manager again from Synaptic?

---

### Post by Bucky Ball on 2009-10-04
You are aware Karmic is testing? If you're testing, great. If not, 8.04 LTS is the most stable release (at the moment) if you are looking for stability. :)

---

### Post by wilee-nilee on 2009-10-04
> **dabbi2000 said:**
> I'm completely clueless, I found out it was more unstable after waking up from suspend but now it doesn't matter any more. Completely random! I really think it has to do with unstable Karmic Koala driver.

I'll try wicd.

Can I then install network-manager again from Synaptic?

 After the upgrade I tried wicd and still had no wireless, but I am not very skilled at this part of setting up wireless or ethernet. What worked was the older install, then installing wicd before the update.  If your ethernet is working then plug in and you should be able to install wicd, then back to network manager, now I was able to due this with the upgrade but, I still had no wireless. and I can't guarantee that it will work for you.

---

### Post by tommcd on 2009-10-04
> **dabbi2000 said:**
> I'm completely clueless, I found out it was more unstable after waking up from suspend but now it doesn't matter any more. Completely random! I really think it has to do with unstable Karmic Koala driver.
I'll try wicd.
Can I then install network-manager again from Synaptic?
Follow the steps I suggested in my last post:
First make sure the proper drivers are being loaded. Type lsmod in terminal and look for your wireless drivers in the output. If they are there then install wicd. Launch wicd and see if it detects your wireless and allows you to connect.

If you wish to reinstall network manager then wicd will be removed since network manager and wicd conflict. So you will have to choose between network manager and wicd.
This is my first time using wicd. I usually just use the terminal to configure my wireless, but it would only connect about 25% of the time for some reason. Removing network manager and installing wicd got me online straight away.

---

### Post by dabbi2000 on 2009-10-19
did as you suggested, tried Wicd and it worked just as network manager did but after a few hours of usage it was just the same

It's an Atheros wireless card using the ath9k driver, guess there must be some bugs in Karmic for that driver

---

### Post by tommcd on 2009-10-20
> **dabbi2000 said:**
> did as you suggested, tried Wicd and it worked just as network manager did but after a few hours of usage it was just the same
So what exactly is happening? Are you getting online and then loosing the connection after a while? If this is true, then try reloading the ath9k driver and see if it gets you back online:
```
sudo rmmod ath9k
sudo modprobe ath9k
```
Then see if wicd can connect.
> **dabbi2000 said:**
>  It's an Atheros wireless card using the ath9k driver, guess there must be some bugs in Karmic for that driver 
The ath9k driver is relatively new. At least it is newer than ath5k. It is possible the driver is buggy. If your wireless was working fine in 9.04 then this may indeed be the case. There is a bug report about this on Launchpad for the 2.6.31 kernel that is in Karmic:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/379096](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.31/+bug/379096)
If nothing else works, then perhaps do a clean install of 9.10 when the final release is out in 9 days. Since you said you installed from Karmic alpha 6, perhaps this issue will be fixed, or at least have a work around, by the time Karmic final is released.
Also, try installing the **linux-backports-modules-$(uname -r)-generic** package, and perhaps the ** linux-backports-modules-wireless-karmic-generic ** package. These are modules that will be backported to Karmic after Karmic is finalized. Perhaps these backported modules will include a fix for this.
EDIT: I think all of these backported modules are included in the **linux-backports-modules-karmic** package. The lauchpad link suggests trying that package. There is no mention whether it works or not though.

---

### Post by xombie on 2009-10-20
Same problem with my dads new laptop. It uses the ath9k driver. The connection comes up on boot and then after a random amount of time (2 minutes to an hour) the connection drops and can't be reconnected with NM without a reboot. I had to install jaunty which seems to be able to stay up for days.

---

### Post by dabbi2000 on 2009-10-28
seems the drivers have got more stable (not perfect but much better) in some of the automatic updates since Koala Beta. Will be interesting to see what happens now in the final release.

---

