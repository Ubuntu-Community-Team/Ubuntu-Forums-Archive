---
title: "Alternate and core install"
date: 2012-05-19
forum: Installation &amp; Upgrades
---

### Post by old n grumpy on 2012-05-19
I am terribly sorry if this has been asked a thousand times already, but I have not been quite able to wrap my head around this issue.

Namely I am now convinced that Lubuntu is probably the way to go. I am rather conservative in my desktop preferences and tend to run older hardware- Lubuntu seems to be ideally suited for that.

That said, there is one feature of Linux distributions i do not enjoy: the bundling of applications in the default installation, the defaults never really work for me.

I could simply remove the applications after the installation, but I would be rather keen to not have them installed at all.

So the followings questions arise:

1. Can I control which applications are installed by using the alternate installer or do I need to go the core/minimal install route?

2. How difficult is the core/minimal install? (I can handle basic tasks, such as navigation, managing applications, using fdisk and so on. However,  I am not familiar with really managing the system from the command line.)

3. Does the minimal/core install omit any important system components, that would not for instance be automatically downloaded (marked as a dependency) when an application that requires them is installed? 

Any input on the matter would be greatly appreciated.:)

---

### Post by ajgreeny on 2012-05-19
The alternate install CD gives you exactly the same as the live CD, a full system, so that will not help your situation.

Use the minimal install CD and follow as much of the info at [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) as you want.

You can, if you prefer, simply install the packages you want, which I did once as a test on an old laptop.  From memory, I installed xorg, synaptic, the DE of choice, and a display manager, but do not install any of the ***ubuntu-desktop** packages or you will again end up with the full installation.  Once you have synaptic it is easy to see what else is being dragged in with the packages you choose, and using synaptic you can use the preferences to remove the option of treating recommended packages as full dependencies; that reduces the addition of things you might not want.

Having got to that point you will have a system but few applications, ie no browser, office apps etc etc, so make your choices and add them as you want them.

---

### Post by old n grumpy on 2012-05-19
> **ajgreeny said:**
> The alternate install CD gives you exactly the same as the live CD, a full system, so that will not help your situation.

Use the minimal install CD and follow as much of the info at [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall) as you want.

You can, if you prefer, simply install the packages you want, which I did once as a test on an old laptop.  From memory, I installed xorg, synaptic, the DE of choice, and a display manager, but do not install any of the ***ubuntu-desktop** packages or you will again end up with the full installation.  Once you have synaptic it is easy to see what else is being dragged in with the packages you choose, and using synaptic you can use the preferences to remove the option of treating recommended packages as full dependencies; that reduces the addition of things you might not want.

Having got to that point you will have a system but few applications, ie no browser, office apps etc etc, so make your choices and add them as you want them.

Mm, very interesting...

Examining the documentation once more, it would seem using the minimal install is the way to go.

Could anyone confirm the following:

Using the commands ([https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall):](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall):)
> 
sudo -i
apt-get install --no-install-recommends lubuntu-desktop
apt-get dist-upgrade
apt-get autoclean
rm /var/cache/apt/archives/*.deb
reboot



Will give me the "depends" packages, but not the recommends packages from [http://packages.ubuntu.com/precise/lubuntu-desktop](http://packages.ubuntu.com/precise/lubuntu-desktop)

*Ergo*, using the command yields a basically a normal Lubuntu desktop without the default apps such as Abiword and so forth. (+some utils of course)

---

### Post by ajgreeny on 2012-05-19
> **old n grumpy said:**
> Mm, very interesting...

Examining the documentation once more, it would seem using the minimal install is the way to go.

Could anyone confirm the following:

Using the commands ([https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall):]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall%29:")


Will give me the "depends" packages, but not the recommends packages from [http://packages.ubuntu.com/precise/lubuntu-desktop](http://packages.ubuntu.com/precise/lubuntu-desktop)

*Ergo*, using the command yields a basically a normal Lubuntu desktop without the default apps such as Abiword and so forth. (+some utils of course)
I think so, yes.  However, if you really want it lean and mean install lubuntu-core without the recommends.  That will give you the lxde desktop and almost none of the applications for browsing, office, music, etc etc.

---

### Post by daisyflower on 2012-05-20
I found that the trouble it takes to avoid the default installations instead of modifying them to not be better than the installed default and simply replacing them. ---- In fact, I used to be a 95% Windows user.  Since the 12.04 launch, I have tried out several different kinds of Ubuntu and I see pros and cons to all.I use Kubuntu on my desktop, and I did spend a few days tweaking it to see what was available and what I liked.  Now it is 95% better than Windows, but I still need to use Windows for the other 5%.  ---- This is a sticky point for Ubuntu to overcome, because I can use Windows to get 100% of what I need on a daily basis.  I am sure I am not the only user out there with this experience, not being able to find a Windows program capatible on Linux.I am using Lubuntu on my netbook which I have found to be really fast and good enough.  It comes with the Chrome browser, which I don't regularly use, but now I will.  It's easier to just adapt to the default I feel.Is there really a benefit to uninstalling Chrome and installing Firefox?  So far, I haven't seen it.  It's like a taxi.  Whether or not it is yellow, it still gets to me to the same sites and I am not missing anything. ---- Perhaps Ubuntu could have a checklist instead.  Think of Pidgin, when you go to add an account, there is a long pull down menu of possible messaging services.  Instead of having a default browser installed, we select at the installation time which browser we want as the default.  Then you could install Lubuntu with Firefox.In the end you won't have to install Chome, delete it, then install Firefox.  That's the way it is now.

---

### Post by mastablasta on 2012-05-21
here is a nice guide with pics and only a few short command lines to minimal install.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
 
replace firefox browser with something lighter...
 
and you can install LXDE package (instead of IceWM) if you need full desktop environment not just windows manager.
 
also i think there is an Ubuntu based distro that is based on IceWM.... :-)

---

### Post by mörgæs on 2012-05-21
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

