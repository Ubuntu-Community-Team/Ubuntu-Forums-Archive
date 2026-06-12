---
title: "installing transmission 3.0"
date: 2022-06-05
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-06-05
I have installed transmission 3.0  I could not make a connection and I never figured it out.  I have now cleared my system of all things transmission and am ready to try it again.  I have been using transmission for years with no problem and then the 3.0 update came along and I am screwed.  My problem is which one to install. Here are some of them:
cli
Common
Daemon
gtk

I suspect there are even more.  Some of the above might be addons to another (I have no idea)  I have spent a couple of days on this one and, I think, mightily screwed it all up.  I need to know just what I should install.  I fully expect that I am also going to have a problem with connecting as well.  I have searched the net for installation stuff and confusion reigns.  What I need is somebody to aim me in the right direction and also the right installation instructions.  There are a LOT of this stuff and just about every one is different from the other.

Any help would be appreciated ............

---

### Post by sudodus on 2022-06-06
Your OS: Ubuntu 21.04 Gnome: 3.38.5 has passed end of life. So you had better dist-upgrade or re-install the new version 22.04 LTS or if problems with that version, install 20.04.4 LTS. Then it should work with the default version of transmission from the repositories.

- In my Ubuntu 20.04.4 LTS it is transmission-gtk version 2.94-2ubuntu3.

- In my Ubuntu 22.04 LTS it is transmission-gtk version 3.00-2ubuntu2.

In general new LTS versions may have some rough edges before the first point release (late July or early August after the release in April). After that period it will usually be rather well debugged and polished. I have not used Transmission version 3.00 yet, because my main computer is still using version 2.92-3ubuntu2. But I know that several other programs have problems with the graphics when running Wayland, so I have switched to the classic Xorg in 22.04 LTS.

---

### Post by jgw on 2022-06-06
thanks for your reply.  I noticed my ubuntu 21.04 which I changed back to 20.04 right now.  I screwed up and have been back to 20.04 for a long time now and not, obviously paying attention.

---

### Post by Impavidus on 2022-06-07
On Ubuntu 20.04, you can install Transmission 2.94 from the repositories. It comes in several packages, depending on the interface you want: transmission (a metapackage), transmission-common (common to all interfaces), transmission-gtk (using gtk GUI, best on Ubuntu or Xubuntu), transmission-qt (using qt GUI, best on Kubuntu and Lubuntu), transmission-cli (using a command line interface), ...

If you really wish to install Transmission 3.0 on Ubuntu 20.04 (has it got an important new feature?), you need some source for it. If you found a good PPA for transmission, it should simply upgrade the packages already installed. If you found it somewhere else, it depends on how it's packaged.

I'm not sure what you're trying to do. Could you explain a bit?

Edit: If the upgrade to Transmission 3.0 was just a red herring and you want to reinstall the default transmission for Ubuntu 20.04, install the package transmission-gtk. It will automatically pull in transmission-common.

---

### Post by jgw on 2022-06-07
Thank you for the reply...............

My problem is pretty simple.  I had been running transmission for quite a long time without a problem.  I had 2.94 and decided to update to 3.0  This seemed pretty simple to me.  So, I installed transmission 3.0 over 2.94   Turned everything on and gave it a whirl.  It could not contact.  I checked how transmission was setup (it wasn't) so I went to preferences and got it to deal with firefox and and I still couldn't get a contact so I spent some time reading all the stuff I could find on firefox, transmission and contact.  Tried a few things, etc.  The problem is that there is a LOT of stuff about transmission and I just screwed everything up.  So, now, what I want to do is to just delete all of my existing transmission and start over from scratch.  Hopefully that will fix my problems.  This time, however, I want to do that right so I need to know which of the installations, for transmission as there are a lot of them and they all have different stuff.  

Oh, I currently have nother transmission on my system.  

That's pretty much it.

---

