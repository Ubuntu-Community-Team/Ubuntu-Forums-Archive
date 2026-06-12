---
title: "flatpak install nuvola eu.tiliado.NuvolaAppGoogleCalendar"
date: 2019-12-15
forum: Installation &amp; Upgrades
---

### Post by jgw on 2019-12-15
My problem started with "flatpak install nuvola eu.tiliado.NuvolaAppGoogleCalendar".  First I was told to "sudo add-apt-repository ppa:atareao/atareao" I did that. The install seemed to work just fine but then I was told to "flatpak run eu.tiliado.NuvolaAppGoogleCalendar" but there was no nuvola. Then it just got worse.  I then went to ubuntu forums to see if there was any activity on this stuff - there was.  The problem is that the newest was over a year old and it went waaay back.  

So....  I had google calendar up and running before I started all of this stuff and its running fine.  What I was trying to do was to start google calendar up when I turned on my machine.  I now have yet another mess.
Here is some terminal stuff:
```

[sudo] password for greg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 calendar-indicator : Depends: gir1.2-handy-0.0 but it is not installable
                      Depends: yaru-theme-gtk but it is not installable
E: Unable to correct problems, you have held broken packages.
greg@gregdown:~$ sudo apt install flatpak
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flatpak is already the newest version (1.0.9-0ubuntu0.1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I also checked synaptic and the missing dependencies are not available there.

So, any thoughts would be appreciated (be kind)...........

---

