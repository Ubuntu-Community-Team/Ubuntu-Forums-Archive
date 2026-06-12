---
title: "gstreamer0.8-plugin install problem"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by relyf on 2005-11-30
hello, 
I currently tried to install the gstreamer0.8-plugins to get mp3 support.
But dpkg hangs every time I try to configure any gstreamer plugin (like gstreamer0.8-mad, gstreamer0.8-wavpack0). I am not able to remove or purge the packets and so I am not able to install any other packets which is very annoying.
I used strace to find the problem, but all I found out was that the packages all hang up in an waitpid(...) call.
Maybe this all belongs to my "confused" (in linux) cdrom-drive, which I am not able to mount (it also hangs up). 
I tried to set the packages to "installed" in /var/lib/dpkg/status (this helped once and mp3 worked fine at that time) but I didn't solve the problem now.

I really need help,
so if you have any ideas please let me know.
Thx, relyf

---

### Post by 23meg on 2005-11-30
Did you try installing via apt from the repositories?

---

### Post by adelcambre on 2005-12-04
I am having the same problem with gstreamer plugins.  The two that I am seeing hang are gstreamer0.8-faad and gstreamer0.8-lame.  

I originally attempted to install them with synaptic which hung on the configuring step.  I have since attempted to fix the problem with dpkg --configure -a, tried de-selecting the package with dselect.  Forcing the uninstall with apt-get -f install .

It always hangs on either 
Setting up gstreamer0.8-faad or
Removing gstreamer0.8-faad

Depending on what I am attempting to do.  This is very frustrating as I cant do anything else with apt while this is borked.

Edit: Another thing is that the dpkg processes won't respond to ^C, I have to kill the process from another terminal.

---

### Post by adelcambre on 2005-12-04
Apt started working for me again after a reboot. Not sure what was wrong but all is well in ubuntu land again.

---

### Post by mckemie on 2005-12-08
Same problem here.

I install gstreamer (either automatix or just apt-get install) and I get hung forever with "Setting up gstreamer0.8....."

No more apt stuff is possible after that.

Rebooting does me no good.  I have resorted to reinstalling twice.  Unless a solution appears soon I will have to just go to a netinstall of Sarge.

---

### Post by tzonenodarkfox on 2007-04-22
I had a similar problem when upgrading from Edgy to Feisty.

After some ps, I found out that the install was hanging during the execution of gst-compprep-0.8.

From *man gst-compprep-0.8*:
> By default, the registry is stored in /etc/gstreamer/compreg.xml

After looking for this file on my system, I found out that the /etc/gstreamer folder didn't exist. I simply created it,  ran gst-compprep-0.8 and everything started working.

---

