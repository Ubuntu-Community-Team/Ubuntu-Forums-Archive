---
title: "Attempt to upgrade to Maverick renders the computer unbootable"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by utkjamie on 2010-10-01
I tried to upgrade Kubuntu to Maverick this afternoon. Because the download was going so slow, I had to leave for appointment so I left it going. When I returned there was an error about a service that had to be restarted and apparently this halted the installation.

When I tried to run *dpkg --configure -a* I received a string of errors for several apps that couldn't be configured because they depended on other apps that also hadn't been configured. I eventually traced the problem back to debconf.

When I tried to configure/reconfigure debconf, I got an error that the config.dat file was locked by another process. fuser -v on the "locked" file showed nothing was holding it open so I had no choice but reboot.

Since the upgrade hadn't completed, I went into recovery mode to try to get things working from there. I tried *dpkg --configure -a*, *apt-get upgrade*, *apt-get dist-upgrade, apt-get install -f*, etc. to get things moving. All of these gave me errors. I started to make some progress with *aptitude* but then my screen filled up with a repeating error stuck in an endless loop, so I rebooted.

Now recovery mode boots to:

> [ 1.818740] Console: switching to colour frame buffer device 175x65It goes no further. If i hit ctrl+alt+F7, I see:

> init: readahead-other main process...terminated with status 4If I boot normally, I'm taken to the login screen but neither the keyboard nor the mouse work so I can't login.

I've been using Kubuntu since early 2007, Edgy, and this is the first time an upgrade has trashed my system to the point of making it unbootable (I can't even boot into my Windows partition because an earlier GRUB upgrade overwrote the MBR on the Windows partition, rendering that unbootable).

If anyone has a solution other than me having to start from scratch, I'd love to hear it. I've been growing increasingly frustrated with bugs in Kubuntu since Intrepid and am thinking it may be time for me to give up on the Ubuntu family and just give Debian a try.

---

### Post by utkjamie on 2010-10-03
Two days later and I'm still down.

After a ridiculous amount of effort, I was finally able to get Kubuntu to actually boot and get to the login prompt, after which it would hang. I could ctrl+f1 and get to a command prompt login and things worked fine if I was cool without the GUI.

dpkg --configure -a had no fixes to perform. Apt-get upgrade/dist-upgrade showed nothing else to install. Kubuntu was telling me everything was installed and nothing needed configuring yet was hanging after taking my username and password.

I finally gave in and tried to reinstall from the LiveCD. That crashed, leaving my computer unbootable.

My opinion of Kubuntu has never been lower than it is right now.

---

