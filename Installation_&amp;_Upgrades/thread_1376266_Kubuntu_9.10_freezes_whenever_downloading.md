---
title: "Kubuntu 9.10 freezes whenever downloading"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Tturbo on 2010-01-09
Ok, I'm completely new to Kubuntu and Linux in general, a friend convinced me to start using Kubuntu and like I was tempted I installed it... 

 I think it's needed to know, that I installed it on a notebook (recent) that came with vista 32 bits which I changed later for seven, 32 bits too. I gave a 20 Go partition for Kubuntu 9.10 64 bits. :???:

 Now that Kubuntu is installed I tried to upgrade the OS (using th command line: sudo apt-get update (then upgrade)). But every time it starts downloading something after a certain percentage (random one actually) the entiere OS _freezes!_ Impossible to move even the cursor of my mouse, it's stuck on the desktop, I can't do anything else then shut down the computer... I later tried installing software such as Firefox or Pidgin, using sudo apt-get install Firefox (then Pidgin) and the same problem occured.
 If someone could help me somehow, I talked about it with my friend, he helped me install too, and he doesn't know what's happening... Apart from that the basic Kubuntu (without upgrade, without drivers or software other than the basic) works, at least I think, I tried it a little and it was working...
 So I'll be waiting if someone can help me...:(

---

### Post by WindPower on 2010-01-09
I happen to be the friend mentioned in the above post, and would like to add that it's indeed a hard freeze, not just an interface freeze; can't switch TTY's with Ctrl+Alt+F1-F6, can't move mouse, screen is frozen, hard drive and CD stop spinning. It happens whenever apt-get is downloading packages.
This prevents installations and upgrades, and it's really hard to fix anything without being able to do that... :(
This is a fresh 9.10 install on an ext4 logical partition, with no upgrades and no extra drivers (because nothing can be installed or upgraded!). Also, the only way to connect to the Internet is by wireless, because the Ethernet controller doesn't work, as I reported [here quite a while ago](http://ubuntuforums.org/showthread.php?t=1207928).

---

### Post by Tturbo on 2010-01-12
After a certain time I decided to try upgrading using Ethernet, eventhough Windpower said it didn't work (which was true because we tried together and it failed). But at home I tried again with another network, another cable another ethernet, and it worked perfectly! I manage to update, upgrade en even install pidgin with no glimpse of a problem...
 But still when I try to download something using the wireless connection, the entire OS freezes... Does someone have an idea why is this happening? ](*,)

---

### Post by Tturbo on 2010-01-15
After posts on another forum, someone told me the problem, is due to the network controler... It was exactly the same bug as here: [https://bugs.launchpad.net/network-manager-applet/+bug/426130](https://bugs.launchpad.net/network-manager-applet/+bug/426130) ...
 The solution is to install Wicd.

---

