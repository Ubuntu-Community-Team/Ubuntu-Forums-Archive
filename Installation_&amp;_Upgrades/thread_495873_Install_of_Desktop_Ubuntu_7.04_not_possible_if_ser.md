---
title: "Install of Desktop Ubuntu 7.04 not possible if server 7.04 is already running"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by acrossglobe on 2007-07-08
I had initially installed Server version of Ubuntu 7.04 on my system. Needed a GUI based interface hence downloaded desktop version of Ubuntu 7.04. Somehow the system is always booting up to hard drive only and not bringing up the desktop install. 

Please let me know what I should do to install the desktop version or enable the GUI interface on my server install.

---

### Post by aysiu on 2007-07-08
Well, there's a difference between enabling a GUI for a server and installing the desktop version.

If all you want is a GUI for the server, install a minimal amount of packages for this: ```
sudo apt-get update
sudo apt-get install xorg icewm menu xterm firefox synaptic gksu
sudo dpkg-reconfigure xserver-xorg
startx
``` If you want the full desktop, you can install the *ubuntu-desktop* metapackage: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

### Post by acrossglobe on 2007-07-12
Thank you very much. I just got back from a trip. 

The update command says it cannot resolve the web address. My wireless is still not operational. Hence the desktop CD is the only option but somehow the system boots directly to login. It bypasses the CD. Is there any way this can be done with a CD instead of being connected to the net.

---

### Post by aysiu on 2007-07-12
The Desktop CD does not have the packages needed to add to an existing installation. You would need the Alternate CD for that.

The Desktop CD should be able to install itself over your current server installation, though. If it's bypassing the CD, you probably have to set your BIOS to boot from CD. Or is it possible that the CD was a bad burn or corrupted during download?

---

### Post by acrossglobe on 2007-07-12
I will try cutting another CD. It does recognize my server install CD but does not recognize my Desktop install CD. Thanks for pointing it out.
Let me try it again.

---

### Post by acrossglobe on 2007-07-12
Cut a new Cd but the server system still does not recognize the desktop install CD,  it does recognize the server install CD. 

I am loading from a DVD ROM drive. It is an old system hence maybe it has some capacity issues. 

I did try the desktop CD on my laptop and it loaded just fine. Only difference I see in the to install ISO is file size difference. Any more thoughts on this is greatly welcome. 

Otherwise the next approach is to setup my wireless network on the machine and try from online. Reading through the post that is an avenue to try, the wireless install seems tough. Any install links that are useful are greatly appreciated. I have WEP setup and ASCII key and non broadcasted SSID.

---

