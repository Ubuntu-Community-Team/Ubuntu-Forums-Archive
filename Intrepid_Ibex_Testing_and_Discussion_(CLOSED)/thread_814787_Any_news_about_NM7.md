---
title: "Any news about NM7?"
date: 2008-06-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-06-01
Anyone know what is happening with Network Manager 7? I was testing a early version around the first of the year & when I updated to Intrepid I needed to roll back to 0.6.6......I'd like to run 7 again, it works better than 6.

---

### Post by gnomeuser on 2008-06-01
Upstream are very active, NM7 is regularly synced in Fedora so I can tell you that progress is being made and it rocks harder than ever.

---

### Post by Eclipse. on 2008-06-01
Meh, I could never get the source to build.

Always got crazy errors and never had the time to get it working.

---

### Post by plun on 2008-06-01
Well... this thread can be useful, howto install SVN

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

About NM
[http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo)

Mailing list for details
[http://mail.gnome.org/archives/networkmanager-list/2008-May/thread.html](http://mail.gnome.org/archives/networkmanager-list/2008-May/thread.html)


Debian Sid is also still on ver 0.6
[http://packages.debian.org/sid/network-manager-gnome](http://packages.debian.org/sid/network-manager-gnome)

---

### Post by Eclipse. on 2008-06-01
> **plun said:**
> Well... this thread can be useful, howto install SVN

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)

About NM
[http://live.gnome.org/NetworkManagerToDo](http://live.gnome.org/NetworkManagerToDo)

Mailing list for details
[http://mail.gnome.org/archives/networkmanager-list/2008-May/thread.html](http://mail.gnome.org/archives/networkmanager-list/2008-May/thread.html)


Debian Sid is also still on ver 0.6
[http://packages.debian.org/sid/network-manager-gnome](http://packages.debian.org/sid/network-manager-gnome)

Sweet!

Thanks going to try that out now

I went to try and get the sid packages after I couldn't get it to build, was quiet surprised to find it still has 0.66

---

### Post by autocrosser on 2008-06-01
Hey Eclipse--

Please post if it works for you--I was looking at the depends & am getting a error about libdbus-1 not being installable.  I look in Synaptic & see libdbus-1.3 installed---just don't know if it will work with the "newer?" version....

---

### Post by Eclipse. on 2008-06-01
You need the dev package aswell.

---

### Post by autocrosser on 2008-06-02
Got everything set--how is it working for you?

---

### Post by plun on 2008-06-02
Well, my little report...

- Intrepids repo, installs after little package findings


- Wired connection works just fine 


- Wireless with a D-Link DWL-G122 not....

Just to follow manual procedures
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)


- UMTS with a bluetooth connected cell phone, "out of order"...

wvdial works OK.

:)

---

### Post by syxbit on 2008-06-03
NM 0.7 'almost' made it into hardy.
i'd imagine with the goal of seamless internet, NM 0.7 should be a high priority.
i hate looking at outdated websites!
the NM site shows 0.65 being the latest. 
hardy has 0.66, and fedora has 0.70 (though beta/alpha, obviously)
what's the state of this?
is this likely to make it in?

---

### Post by plun on 2008-06-03
Well, I must change my report

Auto connected "Wireless" works just fine today.  :)

Something must be set during manual connections

> sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface> 

mode Managed... ?

--------------

Connect UMTS (3G) is delivered with all Nokia and Sony-Ericsson cell phones, Windows software at least for the european market.

It must be rather easy to fix also this for NM 0.7  ?

---

### Post by autocrosser on 2008-06-03
Mode Managed?

HMMM--I use ad-hoc--been busy so I haven't tried it yet. I'll setup tonight or tomorrow eve...Thanks for the update!!

---

### Post by plun on 2008-06-03
> **autocrosser said:**
> Mode Managed?



Well, it was more what mode Managed is....:confused:

I checked Gentoos docs and found this

> Note: If you're using the host-ap driver you will need to put the card in Managed mode before it can be used with wpa_supplicant correctly. You can use iwconfig_eth0="mode managed" to achieve this in /etc/conf.d/net.   

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=4&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=4&chap=4)



I have seen this before and it is confusing.  This morning the wireless connection was directly up in "Automode"....

NM 0.7 works ...:)

---

