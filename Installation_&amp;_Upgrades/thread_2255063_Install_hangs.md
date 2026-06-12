---
title: "Install hangs"
date: 2014-12-01
forum: Installation &amp; Upgrades
---

### Post by russell11 on 2014-12-01
I tried to install dropbox but it hangs in the installation process.  I can't install anything else while this is going on.  I have rebooted several times.  I tried   ps ax | grep dpkg  and then sudo kill <number> and when I do apt-get update it says that the dpkg was interrupted and to so dpkg --configure -a but that just then tries to do the install again in the terminal but once again stalls after the download.   I have tried to uninstall dropbox but can't do that either.  I tried sudo apt-get remove dropbox but it again tells me to do the --configure -a.  So I seem to be chasing my tail here.
Any help would be very much appreciated!

Russty.

---

### Post by russell11 on 2014-12-02
I think I have fixed it!  (fingers X'd)
I tried to install Synaptic package manager and as before it wouldn't install, so I used the terminal commands as I mentioned previously to identify and kill the dropbox install and everytime I did this the Synaptic install continued, so after several kills of dropbox, Synaptic finally was installed.  Then I was able to use Synaptic to remove dropbox and all appears to be working perfectly.  The dropbox stalled install was constantly using 100% CPU.  I still don't know WHY it was a problem though!!

Russty.

---

