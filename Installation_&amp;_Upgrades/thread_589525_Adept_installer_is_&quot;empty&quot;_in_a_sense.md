---
title: "Adept installer is &quot;empty&quot; in a sense"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by komarov on 2007-10-24
There is the following problem with the Adept Installer: it doesn't have almost any packages to insatll inside!!!

The only thing i can see in side is the installed packages and a very few not installed, but they are really few!

I have reinstalled Kubuntu 7.10 just yesterday and this problems has appeared. 

A brief prehistory:

2 days ago adept was working perfectly!

yesterday in the morning adept started throwing a message :"There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages" to any effort to install somthing.

After reinstallation of Kubuntu Adept has lost any ability to install anything, because it doesn't show any packages (except for the installed ones), though i can easily download any package from packages.ubuntu.com. 

Does anyone know what's going on with Adept?

Or at least does anyone know where does the Adept "looks to" in order to see packages for instalation? Because at this place he sees nothing...

PS: after having install Kubuntu i updated Adept as it proposed.

---

### Post by lespaul_rentals on 2007-10-26
Well, if you re-installed Kubuntu simply because of problems downloading packages, that might have been a bit hasty.  Sometimes the repository servers are not functioning correctly, be it because of high usage or maintenence.  It's obviously too late to go back now, though, so let's address the issue at hand.

Are you behind a proxy?  You must configure your network to recognize the proxy or else it simply won't connect.  Maybe you are connecting to a Wi-Fi network.  If so, make sure you're connected to the right one.  If you are accidentally connecting to someone else's (especially a business) they might have a proxy you don't know about.

Are you connected to the Internet properly?  If using a wired connection, does KNetworkManager (which I assume you are using) pick it up and join it?  If you go into Manual Configuration, do you have your connection set to DHCP?  Are there any incorrect default gateways or DNS hosts in the list?  If so, make sure you correct them.

Do you have an Internet connection through your browser?  If so, go into the terminal and run:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Then try to go back into Adept and use it again.  I think there is a bug in the kubuntu-7.04-i686.iso that is being distributed, as I always have this same problem whenever I first install Kubuntu.  The updates and upgrades *usually* fix it, though.

---

