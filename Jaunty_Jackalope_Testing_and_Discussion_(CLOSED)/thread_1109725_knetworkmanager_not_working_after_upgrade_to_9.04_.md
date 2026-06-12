---
title: "knetworkmanager not working after upgrade to 9.04 beta"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deepspring on 2009-03-29
After upgrading to Kubuntu 9.04, KNetworkManager no longer opens on startup.

It also fails to configure wireless connections correctly.



**-- Edit 30/03/2009 @ 1:45pm --**

Manually configured wireless network through the network control panel. "knetworkmanager" is still broken.

---

### Post by rinouw on 2009-03-29
Hi 
I'm occuring your same issue..with gnome wifi work, with kde it doesn't start.
Any adwise?

---

### Post by SuperSonic4 on 2009-03-29
Doesn't kubuntu jaunty come with a plasmoid for networkmanager?

---

### Post by deepspring on 2009-03-29
> **SuperSonic4 said:**
> Doesn't kubuntu jaunty come with a plasmoid for networkmanager?

Indeed it does, but mine was disabled for some reason and didn't show up until I manually created the Wireless connection.

---

### Post by deepspring on 2009-03-29
> **rinouw said:**
> Hi 
I'm occuring your same issue..with gnome wifi work, with kde it doesn't start.
Any adwise?


[LIST=1]
[*]Go into "System Settings" -> "Network Settings" -> "Network Management", click on the "Wireless" tab. Click the "Add" button.
[*]When the "Add Network Connection" window opens, Enter a name for the connection, then select "Connect automatically".
[*]You can either manually enter your wireless networks SSID in the "SSID" box or you can use the "Scan" button to locate it.
[*]Click on the "Wireless Security" tab. Select the type of security (WEP, WPA-PSK, WPA-EAP) you have enabled on your network from the drop down list, enter in your security details.
[*]Click the "OK" button. Then click the "Apply" button on the "Network Settings - System Settings" window.
[*]Close the window.
[/LIST]


With any luck, and after a few seconds an icon should appear next to the clock widget on your panel (see attached screenshot, (hint: its the icon on the left)).

---

### Post by vishalrao on 2009-04-04
Some apparent issues with network manager in KDE like no WPA2 for Wifi, VPN/PPTP missing, no static IP support etc.

So I removed the plasmoid and installed network-manager-gnome (nm-applet) heh, after some fiddling around looks like everything works for me.

I was going to abandon Kubuntu for Ubuntu due to these issues but now I can stay with KDE since 4.2 is the sweetness.... :D

---

### Post by sparagnauss on 2009-04-19
> **deepspring said:**
> [LIST=1]
[*]Go into "System Settings" -> "Network Settings" -> "Network Management", click on the "Wireless" tab. Click the "Add" button.
[*]When the "Add Network Connection" window opens, Enter a name for the connection, then select "Connect automatically".
[*]You can either manually enter your wireless networks SSID in the "SSID" box or you can use the "Scan" button to locate it.
[*]Click on the "Wireless Security" tab. Select the type of security (WEP, WPA-PSK, WPA-EAP) you have enabled on your network from the drop down list, enter in your security details.
[*]Click the "OK" button. Then click the "Apply" button on the "Network Settings - System Settings" window.
[*]Close the window.
[/LIST]


With any luck, and after a few seconds an icon should appear next to the clock widget on your panel (see attached screenshot, (hint: its the icon on the left)).

On my Kubuntu 9.04 I have to follow those steps every time I restart my system.
Even if I select the "Connect automatically" option, it doesn't.
I have to go into the Network Manager, then click "Modify" on my last wi-fi connection and then click "Ok" (without changing anything) and the internet goes. The icon in the tray doesn't come up. 
Before upgrading from 8.10, it automatically connected to my home wi-fi, without doing anything.

Any suggestions to make it work on 9.04 too? Thank you.

---

### Post by deepspring on 2009-04-19
> **sparagnauss said:**
> Any suggestions to make it work on 9.04 too? Thank you.

I sincerely wish I had a solution for you, but I don't.

---

### Post by CyberMando on 2009-04-20
The most reliable solution is
sudo aptitude install wicd
I here it will be included in KDE 4.3

---

