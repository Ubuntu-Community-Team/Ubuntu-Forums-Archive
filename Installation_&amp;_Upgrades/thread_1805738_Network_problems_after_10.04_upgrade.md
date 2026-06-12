---
title: "Network problems after 10.04 upgrade"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by cabfare on 2011-07-16
Hi, I'm new here and am having an issue with Ubuntu 10.04.  Quick backstory - I'll try to remember the relevant points.

I set up a little home network with Ubuntu 10.04 running pretty much only as a backup file server for my photo files.  I work the files on a Win7 machine and store them on two HDDs on the Linux box.  I kept getting crashes and had a lot of instability.  Chasing down the problem, I tried a number of things, eventually (should have tried this first) found a bad RAM card.  Once removed, the system has been running mostly very well, with the following issues.  During this process I even tried going to 11.04, but obviously that wasn't the problem.

Once the RAM was removed, I stayed with 11.04 and it was great for a while.  Then I started to fidget with the box, wanting to learn more about Linux and use it to set up a wordpress blog.  During this process something I ran while following an online tutorial caused the system to crash, resulting in a "stopping system v runlevel compatibility" error.  After this, I could not get Ubuntu to boot up again, even after doing a fresh reinstall of 11.04.

For grins, I went back to 10.04, and it loaded and worked fine for a short time, until I allowed the installation of some of the "important security upgrades."  I don't know which upgrade was the problem, but I now have no network connection.  Previously it would auto-detect eth0 and start up, no problem.  Now I don't even have the up/down arrows network symbol on the taskbar, just a wireless network symbol with a red X.  I've tried disabling/enabling the network connection through the GUI as well as with: 

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManger.state
sudo service network-manager start

I've tried to set my ip address manually, but nothing I have tried is working.

At that point I tried to install 11.04 again (grasping at straws) and it wouldn't load b/c the machine has no network connection, which the installer says it needs.  So instead, I reinstalled a clean 10.04, thinking it would undo whatever upgrade disabled the network connection.  It installed cleanly, but there is still no network connection.  So whatever happened seems to have had some permanent affect on the NIC.

Any suggestions I can try?  Thanks.

---

