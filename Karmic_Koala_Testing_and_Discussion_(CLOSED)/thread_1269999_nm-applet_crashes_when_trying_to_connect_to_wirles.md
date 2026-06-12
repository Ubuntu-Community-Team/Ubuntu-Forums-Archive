---
title: "nm-applet crashes when trying to connect to wirless on a fresh install"
date: 2009-09-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2009-09-19
I just reinstalled Karmic from the Alpha 6 image and I'm not able to connect to my wireless. When I click "Connect to Hidden Network" and enter the details and click connect it doesn't do anything. When I try to left click on the network icon to try again, it crashes. The weird thing is I've been using Karmic for about a week that was upgraded from Jaunty and I had no problem with the wireless. So this seems to only affect fresh installs. Anyone have and ideas or having the same problem?

---

### Post by tjeremiah on 2009-09-20
having the same problem.

---

### Post by cellerit on 2009-09-20
same here!

---

### Post by tjeremiah on 2009-09-20
I cant figure this problem out so i guess ill be using Vista until this problem is solved :(. Windows has no problem with my hidden network.

---

### Post by Roswellgrey on 2009-09-21
Umm - most strange.  I did a fresh Alpha6 install and had the same issue ( nm-applet crashing when trying to configure a connection to a hidden network )
A complete removal of network-manger via Synaptic, and then reinstalling network-manager (via Synaptic) appears to fix the issue -  it seems OK now.  

[ note: obviously, the wired ethernet interface doesn't work after removing network-manger - one has to set up the wired interface manually to be able to reinstall network-manager from the repository ... ]

Update: the above is quite wrong - nm-applet frequently segfaults on my install when trying to add a hidden network, so the above is no workaround at all :(

---

### Post by tjeremiah on 2009-09-21
> **Roswellgrey said:**
> Umm - most strange.  I did a fresh Alpha6 install and had the same issue ( nm-applet crashing when trying to configure a connection to a hidden network )
A complete removal of network-manger via Synaptic, and then reinstalling network-manager (via Synaptic) appeares to fix the issue -  it seems OK now.  

[ note: obviously, the wired ethernet interface doesn't work after removing network-manger - one has to set up the wired interface manually to be able to reinstall network-manager from the repository ... ]

how do you do so manually?

---

### Post by Roswellgrey on 2009-09-21
[http://ubuntuforums.org/showthread.php?t=527365](http://ubuntuforums.org/showthread.php?t=527365)

Post #8 in the above ...

---

### Post by swj on 2009-09-21
I resolved this issue by selecting 'enable SSID broadcast' (using an ethernet connection) within the router configuration.  Once I reconnected my wireless connection, I selected 'disable SSID broadcast'.

---

### Post by tjeremiah on 2009-09-21
> **swj said:**
> I resolved this issue by selecting 'enable SSID broadcast' (using an ethernet connection) within the router configuration.  Once I reconnected my wireless connection, I selected 'disable SSID broadcast'.

sigh, looks like im going to have to. Dont feel like going through all that again.

---

### Post by Roswellgrey on 2009-09-21
Looks like my remove/reinstall assumption was quite wrong.  Whilst my connection to hidden network #1 connects OK after reboot, trying to add another connection to another hidden network causes a segfault in nm-applet as before .....

---

### Post by tjeremiah on 2009-09-21
> **Roswellgrey said:**
> Looks like my remove/reinstall assumption was quite wrong.  Whilst my connection to hidden network #1 connects OK after reboot, trying to add another connection to another hidden network causes a segfault in nm-applet as before .....

I would create a bug report but I no longer get an error. I still cant connect but without a error, I cant easily create a report because I suck at doing so manually.

---

### Post by tjeremiah on 2009-09-21
> **swj said:**
> I resolved this issue by selecting 'enable SSID broadcast' (using an ethernet connection) within the router configuration.  Once I reconnected my wireless connection, I selected 'disable SSID broadcast'.

that works.

---

### Post by Roswellgrey on 2009-09-22
Looks like we had 2 issues here
1. nm-applet being unhappy , namely sometimes segfaulting when adding a hidden network
2. a general inability to connect to a hidden network, but nm-applet *not* segfaulting ( which I have seen randomly over most releases - seems to come and go ... )

I just updated my alpha6, and the segfault issues seems to have been fixed; it must have been something elsewhere as nm-applet itself didn't appear as an updated package.

---

### Post by gertpozzo on 2009-09-22
Same problem here. nm-applet is not segfaulting anymore, but I can't connect to hidden networks using network-manager. I've to use wicd or manual configuration of wpa_supplicant.  Glad too see I'm not the only one having this problem.

---

### Post by gertpozzo on 2009-09-22
I just installed the nm-applet from jaunty and it works great. So it's a problem with last nm-applet updates.

---

### Post by tjeremiah on 2009-09-22
I tried the method made by swj, it worked fine yesterday but did an update today and it fails to connect again. 

> **gertpozzo said:**
> I just installed the nm-applet from jaunty and it works great. So it's a problem with last nm-applet updates.

How do I install the jaunty nm-applet?

---

### Post by gertpozzo on 2009-09-23
Well, I've downloaded the jaunty version here: [http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb)

Then I uninstalled the karmic version using synaptic and finally I've installed the older version using the classic:

sudo dpkg -i network-manager-gnome_0.7.1~rc4.1-0ubuntu2_i386.deb

Then if you want you can block the updates for network-manager-gnome from synaptic.

---

