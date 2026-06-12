---
title: "Network manager drops connection"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by motang on 2009-10-14
After today's update on Karmic network manager drops my connection at home. Similar thing was happening in 9.04 (final release for me at my college so I worked around it by replacing network manager with wicd).  Any suggestions how to fix this with wicd (as I really like the new network manager) and why this would happen after today's update?

---

### Post by Mooty on 2009-10-15
Hi, not sure I'll be much help, but if you're using VirtualBox this might be the problem that's noted here [http://blogs.gnome.org/dcbw/2009/10/14/public-service-announcement-virtualbox-3-hal-and-networkmanager/](http://blogs.gnome.org/dcbw/2009/10/14/public-service-announcement-virtualbox-3-hal-and-networkmanager/)

---

### Post by celticbhoy on 2009-10-15
I have a similar problem, and also tried using wicd instead. Every time I re-boot wicd auto connects to a wired network, the only problem is that there is no connection to a wired network. I think that you should check and see if the you have the same issue, and if so we should file a bug.

---

### Post by motang on 2009-10-15
Just tried out wicd on my laptop and it's the same as network manager. It keeps dorpping the connection so I am out of luck for both this time around. :(

---

### Post by motang on 2009-10-16
I think we should file a bug report!

---

### Post by maheshasolkar on 2009-10-16
There's a bug for a specific hardware/driver (Intel Pro/Wireless 3945BG (driver: iwl3945)):

  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/429035)

But I use Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05) with ipw2200 Network Driver, and I see the same issue. Although, sometimes I am completely unable to connect to my wireless network.

I also started seeing another problem along with random disconnects around the same time. I don't intend to pollute this thread, but I thought I'd mention this just in case it is remotely related:

  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/450097)

---

### Post by motang on 2009-10-16
Well my notebook uses broadcom wireless, and this wasn't a problem 3 days ago, just started 2 days ago after an update.

---

### Post by mitchellcipriano on 2009-10-16
I am having a similar problem on a wired connection. It seems to happen when I am connected to a CIFS share. My network connection does not disconnect, but access to the share does.

Any ideas?

---

### Post by psychok7 on 2009-10-25
got the same dropping of connection problem in karmic release candidate with all updates(shouldn't be happening stuff like this by now)..this needs to get fixed by the final release (without workarounds),i have managed to convert some windows users to ubuntu recently, but im pretty sure they will change back if this thing isn't fixed

---

### Post by motang on 2009-10-25
> **psychok7 said:**
> got the same dropping of connection problem in karmic release candidate with all updates(shouldn't be happening stuff like this by now)..this needs to get fixed by the final release (without workarounds),i have managed to convert some windows users to ubuntu recently, but im pretty sure they will change back if this thing isn't fixed
Is you connection using WEP or WPA/WPA2? Try turing it off and see if you can stay connected. Let me know what you find out please, as I can only stay connected if I turn of off WEP or WPA/WPA2.

---

### Post by psychok7 on 2009-10-26
> **motang said:**
> Is you connection using WEP or WPA/WPA2? Try turing it off and see if you can stay connected. Let me know what you find out please, as I can only stay connected if I turn of off WEP or WPA/WPA2.

Im using WPA/WPA2, haven't actually tried any other connection

---

### Post by Trespasser on 2009-10-26
Same thing here on my Sony VGN-S360 with an Intel Pro Wireless 2200bg. I'm running WPA2 on my home network. The meter shows an 87% connection strength but nothing is coming through (Firefox, updates). It generally happens when I boot up the laptop but it has happened even while I was surfing or updating. Only a reboot will, a majority of the time, fix it. I switched from Network Manager to WICD but still the same problem. It's a bit frustrating.

Later...

---

### Post by motang on 2009-10-26
I honestly don't think it's the app problem so it's not Network Manager or WICD. I would try to run it w/o any security just to make sure it works for you guys. I am doing that right now it and it's fine. But I am at a risk since I am not using anything like WEP or WPA/WPA2. :(

---

### Post by maheshasolkar on 2009-10-26
Looking at my logs, I reckoned the issue was with DHCP. So I setup the router so that my laptop's MAC address always gets a static IP. This fixed the issue for me - my laptop connects again.

Although, I believe this is an issue in general. DHCP should work.

Can someone else with similar issue confirm this?

---

### Post by james_xxx on 2009-10-26
Could your problems be connected with this bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757")

---

### Post by motang on 2009-10-26
Ok let me try that when I get home from school and I shall let you guys know if that worked or not.

---

### Post by maheshasolkar on 2009-10-26
> **james_xxx said:**
> Could your problems be connected with this bug?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/417757")

I doubt, because this bug is about DNS lookup delays, which would come into picture when I have a working internet connection and am trying to navigate to a website. I wasn't getting a wireless connection because the router or my laptop (I don't know which, really) was having trouble negotiating an IP address via DHCP.

---

### Post by motang on 2009-10-26
Nope, even with static IP from my router it won't work. So I have to go back to not having any security just an open connection. :'(

---

### Post by dunbrokin on 2009-10-27
I have the problem with wireless and with wired.....wired is worse. I have tried all combinations of static/no static IP and with dns....all to no avail.....this is so frustrating....I hope it is fixed tomorrow.

The other problems I have are the screen resolution - when I set it to 1280 x 1024, the top and bottom panels get lost...this was not the case under Jaunty. Also, Sun Virtualbox non-free does not work properly, there is a kernel driver error.

For me, I would have to say that Karmic is a big disappointment compared to Jaunty.

---

### Post by psychok7 on 2009-10-28
I realized the problem is at least with Wpa/Wpa2 .. it connects and works without any problem when the theres no protection (at least that i tried)..come on 1 day to the release and no solution yet?

---

