---
title: "Attempting to install Ubuntu 10.10 NETBOOK, never works"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by weregoingunion on 2011-01-17
I have been trying since 10.04 to install the Ubuntu Netbook Remix on my Dell Mini 10 for months now and have tried again several times after 10.10 came out.

It installs just fine, but the problem is the Netbook GUI doesn't come up.  I want to install it alongside Windows 7, and when I do it shows it as Ubuntu Netbook on the GRUB menu, but when it boots it shows the Desktop screen I am used to seeing on my other computers.

I don't know if the Netbook version is basically just a skin or GUI or if it is a completely different type of install, but I am very confused as to why this won't work.

I downloaded my most recent copy from BT from [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) using ubuntu-10.10-desktop-amd64.iso.torrent  and then loaded it with the wubi.exe from that same site.  The .iso is in the same folder as wubi.exe and it does use that .iso rather than downloading a different one.  I chose Netbook install too.

So why does it boot to the Desktop version every time?  Is there something I can do now that it is already installed to "switch" to the Netbook look or do I need to a completely different install?  Any help would be greatly appreciated because this is driving me nuts.  I have tried this SO many times and in so many different ways and I have yet to see the Netbook "look."

---

### Post by weregoingunion on 2011-01-18
I guess I figured out my own problem...

At the login screen, you are able to choose to boot into the Desktop or Netbook version.  The netbook version is not working on my Dell Mini 1010 yet because it is lacking a driver required for unity.

Now that that is solved, I have bigger problems apparently.  First I plugged in an ethernet card (need to manually dl the wireless and graphic card drivers), and I went to install all updates (about 199MB worth) and it asked me to authenticate, as usual, so I put in my password....nothing happened.  The circular timer icon was showing when I moved my mouse over the previous update screen, but the authenticate box became stuck.  Nothing happens.  I click cancel and nothing happens.  I go to power off or restart and nothing happens.

So I reboot by holding down the power button and turn it back on and try again - same thing.  So I try to download the additional proprietary drivers and, again, it asks me to authenticate.  It gets stuck again.  I have rebooted 4 times now and tried to download drivers/updates and every single time it gets stuck at that screen...

I'm thinking Ubuntu is not meant to work on my netbook.  Was looking for a simple OS to run on it but Win 7 works fine on it, I suppose.  At least the regular Ubuntu Desktop works fine on my main, home laptop.

Any suggestions would be appreciated!  Would love to download updates and a 3d driver to get the netbook "skin" working.

---

### Post by mikewhatever on 2011-01-18
You could try downloading and installing updates from a terminal using the command below. 
```
sudo apt-get update && sudo apt-get upgrade
```

As for the 3d driver, it could also be done, but you'll have to reveal the GPU model.

---

