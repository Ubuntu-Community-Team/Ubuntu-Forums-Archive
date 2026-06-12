---
title: "CLI Install, use cdrom to install poackages ?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Muskoka on 2010-05-13
Ok, trying to educate myself.

I have managed to do a minimal install with Lucid 10.04 alternate cd (64 bit). Everything went fine, and I can login without issue. 

My problem is, I don't have a wired connection, wireless only. I'm trying to follow a guide from the internet and now need to do a set of commands starting with sudo apt-get update which finds nothing because I don't have a wired connection. I found a post about setting up a wireless connection, the instructions were to edit etc/network/interfaces and add:

auto wlan0
iface wlan0 inet dhcp

which I did and my network is now active when I reboot (the wireless light comes on, it didn't before). It still won't connect to the internet though. I'm sure there's more I need to do, and will get to it.

What I was wondering and the reason for this post is can't I use the cd I installed from to install the packages I want. I found another post showing how to add a cdrom to the repos from the command line which I did (sudo apt-cdrom add) and the disk was recognized (it spun up). I still can't do any updates/adds and I don't know what to do now. The commands I was trying to do are:

sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
sudo service gdm start

Some off these are probably not on the cd. How would I go about getting some of these installed so I can at least have a desktop with synaptic to work with. Any help would be greatly appreciated.

Thanks Glen

---

