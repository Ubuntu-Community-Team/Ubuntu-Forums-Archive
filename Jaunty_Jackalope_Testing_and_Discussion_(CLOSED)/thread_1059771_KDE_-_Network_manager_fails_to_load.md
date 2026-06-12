---
title: "KDE - Network manager fails to load"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by W2IBC on 2009-02-04
on my KDE desktop network manager fails to load. 

now on gnome network manager works fine.

(I have both gnome and kde installed on this 9.04 box)

any ideas?

---

### Post by Tich666 on 2009-02-04
Just add the new plasma network management widget (called "networks") to your desktop or KDE panel and add your wireless network again.

This component got upgraded recently and it seems it doesn't get added to your desktop automatically.

---

### Post by inportb on 2009-02-04
Indeed -- the new plasmoid kicks butt and seems on track to interface smoothly with all/most of NM 0.7.

---

### Post by garba on 2009-02-04
great this means they're getting rid of the old crappy knetworkmanager and replace it with a plasmoid?

---

### Post by felix.rommel on 2009-02-04
> **garba said:**
> great this means they're getting rid of the old crappy knetworkmanager and replace it with a plasmoid?

I think so. The new Networkmanager Plasmoid works reliable here.

One problem which occured with latest updates a few hours ago is that the icon for established connection isn't showing any more. But apart from that it works stable here.

---

### Post by W2IBC on 2009-02-04
i like the looks of the KDE. (im still not a fan of the widgets thing) but its pretty solid.

ill have to play around a bit more tonight when i get my main work done.

---

### Post by W2IBC on 2009-02-04
the Networkmanager Plasmoid will not connect to wireless for me at all, its dead in the water

---

### Post by inportb on 2009-02-05
Hm... speaking of wireless, Jaunty has been awesome for me so far. Ath5k works very well out of the box with my AR5007EG and supports monitoring/injection too... and then this plasmoid looks awesome and does the job. The only problem I have with it is that some settings seem to be lost whenever it's upgraded.

---

### Post by W2IBC on 2009-02-05
> **inportb said:**
> Hm... speaking of wireless, Jaunty has been awesome for me so far. Ath5k works very well out of the box with my AR5007EG and supports monitoring/injection too... and then this plasmoid looks awesome and does the job. The only problem I have with it is that some settings seem to be lost whenever it's upgraded.

i know wireless is flawless on gnome, with kde i finally got it to connect. (after it sig11 me a couple times) but there is no "icon" to show its connected.

---

### Post by inportb on 2009-02-05
Do you have to do anything special to connect wirelessly, and what exactly do you mean by "dead in the water"?

---

### Post by Kevbert on 2009-02-05
Same problem here. I raised a bug on the knetworkmanager widget no longer worked and it was suggested that I remove and then re-apply the network widget. I can't get the icon to display unless I type ```
knetworkmanager
``` every time I start Kubuntu in terminal.  I've now found my (add) widgets is not working.

---

### Post by inportb on 2009-02-05
If you *must* use knetworkmanager, you could drop a link into your Autostart directory.

---

### Post by Kevbert on 2009-02-05
> **inportb said:**
> If you *must* use knetworkmanager, you could drop a link into your Autostart directory.
That's the only way I can get a network icon and wireless (WPA) to connect.
Is there another way to get the connection icon to show without having to install anything new in Kubuntu ?

---

### Post by inportb on 2009-02-05
> **Kevbert said:**
> Is there another way to get the connection icon to show without having to install anything new in Kubuntu ?

But surely if you're posting in this forum you're looking for new features? As indicated, the network manager plasmoid is the new way to get networked. It does not get you *the* connection icon of knetworkmanager; it gives you *a* connection icon.

---

### Post by Kevbert on 2009-02-05
I had the plasmoid for a short while then after a reboot I got a red square with a white cross in place of it. Had to try to remove and then re-install the plasmoid/program, and then that's where the problems started... On top of this, on a previous install of Kubuntu A3, I got a black space where the icon was supposed to be (a different reported bug), yet was able to use wireless.  Will try a new install of A4 shortly and see if that helps, as there seems to have been a few wireless updates, since A3 first came out.

---

### Post by inportb on 2009-02-05
If you've been keeping up with the updates, you should have Alpha4 by now. Also, when the plasmoid is upgraded it needs to be removed and added again.

---

### Post by Kevbert on 2009-02-05
Thought a clean install might solve the problem. I now have A4 plus 32 updates and have the same problem as before (a red box with a white cross in it).
Inportb, I might be doing something wrong, but can you guide me through removing and re-installing the network manager plasmoid.  I've tried removing the 'unknown networkmanager widget' and when I try to add a new networkmanager widget I get nothing displayed.

---

### Post by caryb on 2009-02-05
I added the plasmoid as per instructions & I get the icon in the taskbar but when I add the details for my wireless it wont connect nor will the the eth0 connection. I have added the entries back into my interfaces file & restarted the networking & I get connectivity & the widget says unmanaged interfaces?


Cary

---

### Post by W2IBC on 2009-02-05
I managed to get it working this am, when wifi is connected there is no icon (just blank space). 

as far as the plasmoid net/manager im not a fan of it.

---

### Post by Kevbert on 2009-02-06
> **KD8HHO said:**
> I managed to get it working this am, when wifi is connected there is no icon (just blank space). 

as far as the plasmoid net/manager im not a fan of it.

That is a separate bug which I've also seen. See [[COLOR="Red"]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/321649").

---

### Post by hardhu on 2009-02-06
With this new Network Management plasmoid the situation is even worser than before: it keeps saying to me that interface eth0 is disconnected even if I have activated it manually from a shell using ifconfig and route commands (because, of course, I couldn't activated using the plasmoid since it said that it was disconnected...).

---

### Post by Tom Mann on 2009-02-07
I seem to be having trouble with the AR5006G in my Aspire One - the network applet is there, but never shows any network connections, the icon updates fine for me when I plug a cable in.

NB: Hardhu, make sure that your /etc/network/interfaces file only contains an entry for lo:

auto lo
iface lo inet loopback


Any help or links appreciated,
Cheers,
T

---

