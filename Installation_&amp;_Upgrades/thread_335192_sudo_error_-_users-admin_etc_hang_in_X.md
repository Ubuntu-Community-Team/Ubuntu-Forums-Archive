---
title: "sudo error - users-admin etc hang in X"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by hlu on 2007-01-09
Hi all

I am newbie in Ubuntu or debian world although I have been using redhat for many years. 

This sudo etc security issue is killing my installation for Xubuntu 6.06 LTS version.  I tried twice, install and wipe out disk and re-install and still got same results. 

First of all, this machine is low end, 128 MB, 350 MHz CPU. I was able to install whole bunch of stuff without difficulty, X, xubuntu-desktop,  pine, vsftp, telnetd, ssh, vnc4server etc. 

sudo in console still works right now. But at end of my installations after vnc4server,  user-admin,  services etc  sudo required X-window administrative jobs hang. They would prompt for a password, and then hang there running forever, or gave me a error, the first time was "CAPS LOCK needs to be activated" error. The second disk-wipe out re-installation error today was  "running forever"  hanging for those sudo required amin jobs in X-window. 


I do not know what I did to cause this problem. It could be the vnc4server because this hanging problems started after I login into vncserver, and tried to use admin under vncserver.   I even tried deleting xubuntu-desktop and reinstall, still fail. I tried removing vnc4server, the sudo password lock/error in X-window still exist. 

I am exausted on ideas on this issue.

Any help will be greatly appreciated. 


------------------------
Henry

---

