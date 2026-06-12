---
title: "HELP!  Lost Network Manager - Need offline install"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by bluebrave on 2012-02-21
I screwed up (royally) and completely removed network manager.  Now I have no way to connect to the internet.  I'm using 10.04.

This help site: [http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection](http://askubuntu.com/questions/55805/how-do-i-re-install-network-manager-without-an-internet-connection) 
lead me to find some deb files to the [network-manager package]("http://packages.ubuntu.com/lucid/network-manager") and [network-manager-gnome package]("http://packages.ubuntu.com/lucid/network-manager-gnome").

However, it still isn't working (no applet).  I'm sure I'm missing other packages.

I also noticed that nothing happens when I go to System > Preferences > Network Connections (the Network Connections window doesn't open)

How can I get network manager back?

Please note I've very new to this and need my hand held (please make things simple to understand).

I've tried a command line connection to the internet but have failed (I think having the wpa2 encryption on my wireless is what is the problem)

---

### Post by bluebrave on 2012-02-22
Solved!:popcorn:
Whew!  Since I didn't see any responses, I kept digging and found installers for connman and indicator network in an effort to get some internet connectivity on my Ubuntu machine.

I downloaded the deb files from the launchpad site ([http://launchpad.net/~indicator-network-developers/+archive/daily-ppa):](http://launchpad.net/~indicator-network-developers/+archive/daily-ppa):) 
Select you package (Lucid, in my case) and hit "Filter".  
Take note of the package versions for your Ubuntu version.
Then, click "View package details" on the right.
From there, click on the package(s) you noted above and click on the "deb" file (64 for 64 bit systems, 386 for 32 bit systems).

Once I had that done, I ran the deb files and found that I was missing required dhcp3-client and dhcp3-common versions.  I searched the web for the versions I needed and downloaded their deb files*.

After installing them, I was able to install the connman and indicator network (in that order) packages and voila! I had internet access.

I then loaded the ppa for network-manager and installed it and went to "Ubuntu Software Center" and installed the network manager applet.  Which also re-updated my dhcp3 packages as I had to revert to an older version to get connman etc to install.

After reboot, I noticed that network manager wasn't operational (the applet stated networking was disabled) and "Network Connections" was still missing under "System > Preferences" but assumed it was because connman and indicator network were interfering**. I took a leap of faith (plus I still had the connman/indicator deb packages if things failed) and removed connman and indicator network.  After reboot, network-manager was operational and "Network Connections" was back in the Preferences menu.:P

*Note: on the dhcp3-common I had an error that I had a newer version on Ubuntu, so I had to go to Symnaptic Package Manager and remove installed dhcp3-common.  Thereafter, I ran the deb package.

**Note: I also followed the instructions here:  [http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217) (use "sudo" before the  commands) before removing connman/indicator but don't know if that is  necessary or not.

---

