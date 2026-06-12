---
title: "Failed upgrade, Avahi service fail"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by DudleySmith on 2007-04-21
Disclaimer: I'm a linux noob, so I'm capable of almost any elementary error to do with this stuff.

Short version: Any network access freezes the console or desktop that attempts it.  I have a boot failure with Avahi DNS daemon.  There are no files in /etc/avahi/services.  What do I do now?

Long version:
I attempted an upgrade from Kubuntu Edgy to Feisty last night (I believe this to be an error specific to ubuntu so I'm posting here rather than the kubuntu forums), but it froze 13 minutes from completion and gave me an timeout error and froze.  After the dist-upgrade log showed two "Nothing's happened for 240 seconds argh" type errors I killed the update manager.  I tried to start up the adept manager again, but it was complaining that something else had a lock on the package interface.  

I tried kill -9ing stuff that had adept or apt in the name, but couldn't get the GUI interfaces to work.  I tried entering "apt-get upgrade", and it complained and told me to enter a dpkg configure type command.  So I did that, every time going back to apt-get upgrade and entering the command it told me to (There was another apt-get command with a -f switch, but I was mostly just doing what it told me to do). 

 Eventually it told me it thought that it thought it was up to date and so I rebooted.  The boot log (dunno what it's called, it has a list of services and daemons with [ok] or [fail] next to them) shows a failure for "Avahi mDNS/DNS-SD Daemon".  The KDE login screen comes up but then freezes just showing the wallpaper.  If I switch to one of my other consoles any network commands freezes that console: ping, ifconfig, ip addr show.  I've had a look in my network config file in /etc/networks, and it is the same as it was before the upgrade.

I then logged into it again in recovery mode, and had a look at some logs in /var/logs.  The following lines seem to be the bugbears:

No service found in /etc/avahi/services [I've looked and this directory is empty]
Can't open user face
Internal error: memory corruption detected.

Direct network access commands still freezes my shell in recovery mode.  

Now I could, of course, just kill the partition and reinstall feisty from scratch from a CD (which wouldn't be that awful for me), but I reckon I'll learn more by fixing this.  I guess I need to get this avahi DNS daemon thingy working again.  What's my best strategy for doing that?  Do I grab a .deb package from somewhere?

Thanks for any help you guys can give me.  I imagine I made countless mistakes after the auto upgrade fubared, but I need to move forward from the current state if possible.

---

### Post by DudleySmith on 2007-04-21
This forum is really busy, so I'm bumping this in the hope someone will see it.

---

### Post by BLTicklemonster on 2007-04-22
Sudo aptitude someone answer this thread.

:) Dude needs help.

---

### Post by kikazaru on 2007-04-23
I have the same problem. The upgrade process froze during the installing step, on the networking-gnome something-or-other package. I couldn't even switch to a text terminal so I had to hard reset. I tried apt-get upgrade and got an instruction to run dpkg with some options. That seemed to finish installing the remaining packages. When I rebooted I had no nerworking. apt-get upgrade just revealed one pacakge called nfs-something was not upgraded, so I apt-get install ed it but still no networking.

Help!

Only the avahi-daemon fails during start up.

---

### Post by kikazaru on 2007-04-23
I seem to have fixed it... see [https://answers.launchpad.net/ubuntu/+question/5230](https://answers.launchpad.net/ubuntu/+question/5230)

I just edited /etc/network/interfaces which looked something like this:


auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

and changed it to:


auto lo
iface lo inet loopback

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

