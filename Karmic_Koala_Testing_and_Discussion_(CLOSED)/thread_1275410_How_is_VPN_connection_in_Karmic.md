---
title: "How is VPN connection in Karmic?"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PGScooter on 2009-09-25
Has anyone had any success/failure with VPN connection in Karmic?

Does VPN connection come natively now on Karmic ("natively" meaning you do not have to install that PPTP plugin)?

Just curious,

Thanks!

---

### Post by Sophont on 2009-09-25
> **PGScooter said:**
> Has anyone had any success/failure with VPN connection in Karmic?

Yup. Installed Karmic 3 weeks ago and been using VPN (PPTP) ever since without problems.

I've also installed OpenVPN but not tested with Karmic yet.
VPN worked fine at least since Hardy (was broken on Intrpid for a while).

> **PGScooter said:**
> Does VPN connection come natively now on Karmic ("natively" meaning you do not have to install that PPTP plugin)?

You still have to install the plugin - it's a *plugin* after all. But why worry about it - it's just a few clicks and about a minute away.

---

### Post by KhaaL on 2009-09-27
just want to add in that on kubuntu its not as smooth if you want to use pptp - you'll have to go through kvpnc which is quite unstable. 

Also, for some reason, I seem to have DNS problems with vpn in karmic...

---

### Post by snaga on 2009-10-07
I just installed Karmic a couple of nights ago. It has broken my PPTP VPN ability. Not sure why yet. It doesn't even try to connect, from what I can tell right now. It errors out immediately telling me that it quit prematurely. I plan on working on it this evening. I had trouble with this when I upgraded to Jaunty. Should have taken notes on the fix...

---

### Post by sideffects on 2009-10-07
I've successfully installed PPTP in Karmic, and have added the VPN Connection to "Network Connections." Now, I can't figure out how to connect to it. Can anyone help?

---

### Post by snaga on 2009-10-07
Sideffects, if you have created the connection, then you should see it in the VPN Connections menu. Assuming that, what happens when you select that menu item?

---

### Post by sideffects on 2009-10-07
> **snaga said:**
> Sideffects, if you have created the connection, then you should see it in the VPN Connections menu. Assuming that, what happens when you select that menu item?

This is what I see
[IMG]http://img84.imageshack.us/img84/1466/screenshotnetworkconnec.png[/IMG]

---

### Post by snaga on 2009-10-07
You should have a network menu icon that you can pull down at the top. In that menu you should see a menu item of "VPN Connections", and in that should be the VPN connection you set up.

[IMG]http://img210.imageshack.us/img210/7725/screenshot005yu.png[/IMG]

---

### Post by sideffects on 2009-10-07
Ah! Thanks a ton!

---

### Post by snaga on 2009-10-08
Updated tonight and I can now connect to my VPN.

---

