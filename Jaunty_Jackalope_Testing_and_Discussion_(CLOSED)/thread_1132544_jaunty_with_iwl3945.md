---
title: "jaunty with iwl3945"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by johnn1949 on 2009-04-22
Jaunty with iwl3945.  My wireless will not try to auto connect on boot.  It shows the wireless icon in the panel with a red x on it. 

 If I left click the icon, choose connect to hidden wireless and choose auto(mywireless) from the drop down menu for connection, it will connect.

What do I need to do to get it to try to connect on boot?  Intrepid always did it.  Its a clean installation not an upgrade.

Thanks
JOhn

---

### Post by caryb on 2009-04-22
Had the same in Kubuntu I had to turn off the hidden SSID in the access point for my PC to autoconnect.


Cary

---

### Post by johnn1949 on 2009-04-22
I don't have a hidden network. ssid broadcast is enabled.  Some times I see it when I left click on the wireless icon, and then I can connect by choosing it.

---

### Post by MacUntu on 2009-04-22
There is a problem somewhere between NetworkManager and the wireless kernel driver. Intel devs say it's a NM problem (after some testing without NM installed I think they are right) but NM devs are not so sure about that, oh well...

On my machine it takes up to 60 seconds after a cold session start until the connection is available (but it always connects). After warm session logins the connection is there immediately.

Install the [COLOR="Red"]linux-backports-modules-jaunty [/COLOR]package. It contains a newer wireless driver which somehow works (for me it connects faster in most but not all cases).

---

### Post by chili555 on 2009-04-22
> Intel devs say it's a NM problem (after some testing without NM installed I think they are right)I think so, too. I have an iwl3945 card and have uninstalled NM. My wireless connects first time, every time. In my opinion, NM is a good idea which is not yet correctly implemented.

---

### Post by MacUntu on 2009-04-22
> **chili555 said:**
> I think so, too. I have an iwl3945 card and have uninstalled NM. My wireless connects first time, every time. In my opinion, NM is a good idea which is not yet correctly implemented.

And I had zero problems with it in 8.10. :(

---

### Post by lithorus on 2009-04-22
I also have an iwl3945. However I have absolutely no problems with NM.

---

### Post by johnn1949 on 2009-04-22
First I tried patience and the keyring came up after about 2-3 minutes.  

I installed the backports suggested above and now it comes up right away after boot.

Thanks. I think its solved.

---

### Post by MacUntu on 2009-04-23
Seems to be fast again with 2.6.30-rc3 kernel (maybe updated driver - had no time to check), so I'm positive Karmic will work fine again.

---

### Post by Eversmann on 2009-04-23
i have the intel 3945 card on my advent 4211 and had no problems since i upated from 8.10 to 9.04 alpha 6.

It's true that with 2.6.30rc3 works faster.

---

