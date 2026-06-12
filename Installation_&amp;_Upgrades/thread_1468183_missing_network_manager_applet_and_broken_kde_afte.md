---
title: "missing network manager applet and broken kde after upgrade to Ubuntu 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by cmit37 on 2010-05-01
I was running Ubuntu 9.10 on my HP G70 laptop and did an upgrade using upgrade manager to Ubuntu 10.04.

Since I haven't been able to get wifi connection or wired working. The Network Manager applet is missing from the notification area and if I try to run nm-applet manually it says it is already running. I tried killing the process and then running it manually in the terminal and although the process appears to be running it is missing from the panel.

Booting into the live cd has the applet working fine so something in the upgrade process must have failed.

I tried changing the theme to see if it displays in other themes but had no luck.

I also tried to log into kde but kde seems to be broken. When I log into it after the splash screen all I get is a black screen with only my mouse pointer.

Any help getting these problems fixed would be greatly appreciated.

Thanks

---

### Post by Filiprino on 2010-05-02
I'm having the same problem (upgrade from 9.10 to 10.04). If I stop Network Manager service then the applet appears but obviously tells me that the manager is not active. When I restart NetworkManager service the applet disappears.
:-/

---

### Post by GiladGressel on 2010-05-02
I am also having exact same problem

applet has vanished.  Wireless is working though.

just can't see what i'm connected to

would love to fix this

-gilad

---

### Post by cmit37 on 2010-05-03
I was able to fix it by adding a notification area to the panel. When I added it the network manager applet just appeared in it.

---

### Post by GiladGressel on 2010-05-03
yea thanks

i fixed it also by adding the notification area

also had to add the indicator applet for the sound icon to return


took me a while to figure out because I was looking for "network manager" to add, not "notification area"

thanks

---

### Post by harpsound on 2010-05-06
nOOb

Missing the sound dongle and am missing the internet network applet after a 10.04 install.

What is a notification area? indicator applet?
I am Windoze proficient.
Am on the Linux learning curve with several drives.
Thanks
Stephen

> yea thanks

i fixed it also by adding the notification area

also had to add the indicator applet for the sound icon to return


took me a while to figure out because I was looking for "network manager" to add, not "notification area"

thanks

---

### Post by harpsound on 2010-05-06
I have resolved my Menu Icon issue

Just want to get the sound toggle button/slider onto the top menu bar.

I am ecstatic with the whole Linux changeover - I have waited several years and made the leap last autumn on several computers.
This is my first upgrade cycle - gone extremely well except for n00b issues.

---

### Post by PrototypeAlex on 2010-05-21
I seem to have a similar problem but not as easy to fix as what has been said above.

The networking icon is there but is a blanked out white square, no wifi connection, tried re-installing madwifi, no success, tried uninstalling madwifi and installing wicd, no success.

Any suggestions?

---

