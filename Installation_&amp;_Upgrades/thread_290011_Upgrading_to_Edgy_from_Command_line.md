---
title: "Upgrading to Edgy from Command line"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by danbh on 2006-10-31
Well, it seems there are two official methods to upgrading.  One is from the command line, and the other is using the gui update manager.  Both claim that the other is buggy, and will fail.  I don't know the truth.  Regardless, when I tried to upgrade from Hoary to Dapper, the gui crashed on me, and I didn't know what to do.  So, I had to reinstall from scratch.  Now, I am wiser, and I will never trust a gui to a system upgrade again.  GRrrrrr
Anyway, even though this isn't the "right" way to do it, this is the collected experience of how I did it, over three computers, the toughest was a laptop.  I am offering my experience, maybe in case others run into trouble.  Maybe you are trying to do it from the command line from the beginning.  Maybe the gui has crashed on you.  Whatever.  
The following worked on an Xubuntu laptop with a broken CD drive, so it was either succeed or bust.  (I know, risky, but I was bored.)  Be forewarned, I am an Ubuntu newbie, so use follow the following at your own risk.

Let's get started.

First, make sure vanilla Dapper is installed:
Reset your respositories to something standard.  Use the directions [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories"), and don't worry about PLF.
Next, install regular ubuntu:
```
sudo apt-get install ubuntu-desktop ubuntu-standard ubuntu-minimal
```

Make sure there are no problems, as we are about to start the actual upgrade.  Now is the time to work out any problems with dapper.


The UPGRADE :???: 
Here we go.  Change your repos to edgy, which can be found [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories").

:!: Now, if you haven't already, I would suggest dropping down to the command line with Alt+Ctrl+F1 (not even a terminal in X).  This is the point of no return.  When I did this, X was uninstalled, and it crashed.     So, I suggest forgetting about X for now.  

These next two commands do %90 percent of the upgrade:
```
sudo apt-get update && sudo apt-get dist-upgrade
``` 
Sit back, or go get a cup of coffee.  Its gonna take awhile.

...

Great, its finished!  Its broken!  Let's fix it.  Run these commands repeatedly, till the computer will install no more.
```
sudo apt-get dist-upgrade
sudo apt-get install -f
sudo apt-get dselect-upgrade
```

Ok, now, make sure ubuntu is fully installed (hint: its not) by running:
```
sudo apt-get install ubuntu-desktop ubuntu-standard ubuntu-minimal
```
Also install any other flavor of ubuntu that you were using.  Ie, for me:
```
sudo apt-get install xubuntu-desktop
```

Go back a step, and rerun those apt-get-upgrade commands, just in case.

Now, if you have nvidia (ati too??) drivers installed, you may have to reinstall them.  See [here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29").
[HTML]
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

    * Should the above not enable the new driver, you can enable it manually by opening the X config file: 

sudo gedit /etc/X11/xorg.conf

    * and replacing "nv" with "nvidia"[/HTML]
:KS Ok, now reboot, and hopefully you can get into your system.  (If not, I'm sorry, my advice has failed you.)

We aren't done yet.  Now, once you log in, fire up Synaptic Package Manager.  Try to fix the remaining anomalies.  The following is what I did. YMMV.  (For example, these directions will uninstall any non-repository programs; like opera.)
Sort the packages by "Status".
Uninstall everything under "Installed (local or obsolete)"
Then upgrade anything else that can be upgraded.
AND FINALLY, make sure the package ubuntu-desktop (and xubuntu-desktop,or whatever) is still installed.  If not, re-re-install it.  

Done.


Thats my experience.  Hope this is helpful.  Of course, you can always try just:```
gksu "update-manager -c"
```

---

