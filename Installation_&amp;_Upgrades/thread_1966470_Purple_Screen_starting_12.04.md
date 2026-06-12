---
title: "Purple Screen starting 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Senior_Buckethead on 2012-04-27
Hi all,
I did a fresh install of 12.04 (32 bit) on my Asus Laptop. It behaved when I was installing it, but after all was done and I rebooted it, all I get is a purple screen and the hard disk light is on continuously. When I force shutdown and reboot in recovery mode, I run dpkg to try and find any broken packages (most of the other options go nowhere at all), the program tells me that I need to download some packages, but can't reach the network.
This is strange because the network is set up to work in Ubuntu. So after waiting for the packages to download, which they don't, I control+c and Ubuntu loads the desktop. 
When I 
```

Sudo apt-get update

```I am told that no packages need to be installed. I run update manager and the same, I don't need any packages.

What do I need to do to get a network connection for dpkg?

28 April Update----
12.04 logs on, loads the desktop background picture but no more.

Glenn.

---

### Post by Senior_Buckethead on 2012-04-27
After loading OS and Logging In, under the cinnamon theme, I got a background picture and no more, so I ctrl+alt+delete, logged out of cinnamon, re logged in under gnome classic, no problems.
Anyone know how I can troubleshoot the cinnamon theme?
I know from reading the cinnamon theme page that its dodgy under 11.10, and 12.04 must be no different.

Glenn

---

### Post by Senior_Buckethead on 2012-04-29
The problem was fixed by a fresh reistalling 12.04. Once I logged in, using apt-get to get rid of that dreadful unity:
```

sudo apt-get install gnome-session-fallback

```
I logged out, then logged in under gnome-classic. (Logging in by first clicking on that little gear above log in name and selecting gnome-classic).
I then installed cinnamon
```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
sudo apt-get update
sudo apt-get install cinnamon

```
And it all installed fine.

Problem fixed.

---

