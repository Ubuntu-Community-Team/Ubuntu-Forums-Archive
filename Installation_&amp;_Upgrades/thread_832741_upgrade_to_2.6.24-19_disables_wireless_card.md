---
title: "upgrade to 2.6.24-19 disables wireless card"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by haiiyaa on 2008-06-18
Hi, 

I have ubuntu Hardy. On a Dell Laptop XPS M1530. This morning the automatic updates upgraded my kernel to 2.6.24-19. After the upgrade my wireless network stopped working. It is not connecting to my home network and when i click on the network icon in the task bar, i don't see the list of available networks under wireless networks. 

I am still learning the ropes in linux slowly, so I would appreciate some guidance. 

thank you

---

### Post by nilpill on 2008-06-19
I can confirm this problem.

Checking the hardware drivers window, my wireless driver (Support for Atheros 802.11 wireless LAN cards.) appears to be enabled, but not in use (and the driver, "Atheros Hardware Access Layer (HAL)" seems to be missing altogether). Also, when I checked iwconfig, no wireless devices appeared whatsoever.

---

### Post by CMEPTb on 2008-06-20
I confirm a problem with the said kernel and said device. When I go to "Administration->Hardware Drivers" it says that 
```

Support for Atheros 802.11 wireless LAN cards - Enabled /*check*/ - /*but then red button and "not in use"*/

```

Any check change requires a reboot which completes the vicious circle.

A previous kernel loads BOTH that "Support for Atheros 802.11 wireless LAN cards" and "Atheros Hardware Access Layer (HAL)" /*  Not even visible with the 2.6.24-19 */, but, alas, I cannot connect to any network, even the one I'm connected to right now in order to write all this stuff. Thank god I got 6 computers in my place :). 

Somewhere in the beginning of the boot (right after gfxboot-grub screen) I saw a device communication error or something like that, which in the half a second it was on screen did manage to suggest me to use another driver. Couldn't catch which, sorry; I just remember it was the same name as the failed one but had a suffix *too at he end. Plus, I have no idea how to actually change that driver, and Ubuntu help center is not in any way better than Windows F1 crap, which still amazes me even now, when I'm convinced that Ubuntu is the most user-friendly and bendable system in terms of its settings.

I'm sorry that I sound so frustrated, - I haven't had much sleep lately, and to add insult to the injury I was forced to fix my friends Windows problem for about 4 hours, and then this crap kicked in.

If someone would at least point me in the direction of the boot log /*the stuff Ubuntu shows before loading X */ I would be really greatful, since I feel like a complete n00b after I skimmed through the whole /var/log folder.

Nothing like a network problem in linux to make you feel like a complete sucker, huh?

At this point I have to admit: I am a n00b and have very basic knowledge about how this system works. I am a quick learner, though :)

Thanks for reading this rant, hope someone has an idea how to fix this problem.

EDIT: I got a Fujitsu Lifebook P1510d

---

### Post by Heronuser8.04 on 2008-06-20
I too, had trouble with my wireless. I followed the guides I found here: [COLOR="Red"]https://help.ubuntu.com/community/Wi...358e4b611353c0[/COLOR] and selected my device. I got it up and running, but it crashed after changing something else. The good news is that I have found a better solution!

I do not install the "generic" module anymore, but use the "openvz" packages. After installing these, my system worked exactly like it did before the update. I hope it can solve your problems as easily as mine.

--------------------------------------------------------------------------
Compaq Presario V2000, Turion 64 X2 TL52, 2GB, 120 GB, Dual boot XP PRO - ubuntu 8.04 version 19.

---

### Post by CMEPTb on 2008-06-23
Sorry Heronuser8.04, but openvz did nothing for me.

ndiswrapper did let me detect wireless networks and even their signal strengh, but even router pings go unanswered. Also, I noticed an error while rebooting Ubuntu, something to do with Network Manager, but for the love of Zombie Jesus I can't find a log file for load or unload of the system, so I can't be more specific.

I hope a solution would present itself soon, 'cause being chained to the modem sucks donkey balls.

---

### Post by MagisterJoe on 2008-06-23
I can also confirm wireless problems with kernel 2.6.24-19.  I have a Dell 600m with a Broadcom wireless card (B43 driver).  The card is detected and allows brief (~1 minute) connection to wireless networks and then stops responding.  Everything works just great with 2.6.24-18, so I'm just booting that kernel for now.

---

### Post by kimi2013 on 2008-06-23
Hi,

have the same problem after kernel update. wlan find the router but i didnt get a ip adress.

soluten for me:
edit /etc/udev/rules.d/70-persistent-net.rules 
and delete everything for the wlan card.
reboot


greetings

kimi
ps.: sorry for bad english

---

### Post by boteeka on 2008-06-24
My wireless got screwed up only today, with the installation of linux-ubuntu-modules-2.6.24.19. I can still see the wireless networks around, but it keeps dropping the connection every few seconds. It is sad, because for about a month I had no problems with wireless connections at all. I have an Inspiron 1525, with intel wireless chip. Did somebody already filed a bug on launchpad?

---

### Post by CMEPTb on 2008-06-25
It seems that I found a "ducttape over an open gunshot wound" solution, atleast for myself.

I tried ndiswrapper with no luck, tried all the other kernels like rt, openvs, xen (which failed to start at all), rolled back to *-16-generic kernel, and was utterly frustrated with my n00bness. 

Then, I just installed madwifi using this awesome script found here: [http://ge.ubuntuforums.com/showthread.php?t=798485]("http://ge.ubuntuforums.com/showthread.php?t=798485")

The drop-down selection of a network did nothing, but going into "Connect to Other Wireless Network..." in gnome-panel's Network Utility applet and typing the name and the password of my home network seems to have fixed the problem. I am online and can go resume my meaningless zombie surfing.

I have no idea why this worked, (dang, I think it cured my athlete's foot, too!), since no logs show any hardware problems whatsoever. I suspect some funky business between the kernel and the Network Manager, so maybe building that thing from source is a good idea. Since I'm too lazy and I am cool with typing the network name every time I log in, I'll leave you guys to figure this out. Otherwise, what's the point? There's gonna be a kernel update in a week or something, and that might just break something else, like my X11 or keyboard. That would be fun to fix. Nothing teaches and ubern00b like me about linux like some major malfunction catastrophy. 

This time, I learned how to use dmesg | grep "something" | less

In a year, I'll be programming kernels.

Peace you all, I think I had a few too many Jack-n-Cokes. CMEPTb out.

---

### Post by orthorim on 2008-07-13
Upgrading Ubuntu to version 8 (HH) and kernel 2.6.24-19 also disabled my wireless. This is a laptop with a standard Intel WiFi chipset. 

My solution was to use the alternate boot and boot with kernel 2.6.22-14. WiFi works perfectly. I really wonder how they managed to screw that up, and also why this is tied to the kernel - seems like a bad idea to me.

---

### Post by Rallg on 2008-07-13
My Dell Vostro 1000 had no problem. Life went on as usual, after kernel upgrade (uses B43 driver). I only mention this to show that there is something system-specific going one.

---

### Post by haiiyaa on 2008-07-14
A few days after I reported this problem, i don't recall doing any new changes except maybe installing some more udpates. Now my wi-fi card has started working on this kernel. 

strange...

---

### Post by Mic_Droz on 2008-09-01
Mine is still not working - I only installed the -19 kernel just recently... is there anything I can do to fix it, other than to connect the laptop to the modem via a wired connection?

---

### Post by Mic_Droz on 2008-09-02
> **nilpill said:**
> I can confirm this problem.

Checking the hardware drivers window, my wireless driver (Support for Atheros 802.11 wireless LAN cards.) appears to be enabled, but not in use (and the driver, "Atheros Hardware Access Layer (HAL)" seems to be missing altogether). Also, when I checked iwconfig, no wireless devices appeared whatsoever.

ah hah! that is my total and exact same problem... did you manage to get the HAL back? or has it been removed due to some other solution?

I'm frustrated and curious, all at the same time...

---

