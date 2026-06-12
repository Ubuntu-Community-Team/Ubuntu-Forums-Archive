---
title: "FIXED: new xserver-xorg-core breaks old nvidia kernel module"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by mimithebrain on 2008-01-19
This morning, my machine would log in GNOME, then back out to the login screen.

After much troubleshooting, I've brought back my machine from the console.

The old nvidia drivers released in September of last year does NOT work with the lastest xserver-xorg-core update that was released yesterday.

If anyone else has the same problem that I did, the solution is to download the lastest driver off the NVIDIA website, and update the kernel module.

In addition, the configuration application that comes with the package has been improved: it's worth the update :biggrin:

And just this instant, I've discovered that this new driver permits to adjust the contrast outside the TTY! (that been said, don't forget to edit your /etc/modprobe.d/nvidia file to remove the "adjust brightness" setting if you have added it! Nvidia won't load with that option anymore!)

---

### Post by samkline on 2008-01-19
I'm having the same problem

[http://ubuntuforums.org/showthread.php?t=672054](http://ubuntuforums.org/showthread.php?t=672054)

I'll try updating the drivers and see if it helps. I was just about to reinstall GNOME!

---

### Post by samkline on 2008-01-19
OK, even though I already had the newest version (169.07), I reinstalled it anyways, and that fixed it. Which really pisses me off because I've been working on trying to fix it for several hours :/ I'm really starting to dislike nvidia.

But thanks mimithebrain!

---

### Post by Fraktyl on 2008-01-19
Actually, just reinstalling the Nvidia drivers that are in the repository will fix the problem.

It looks like the Xorg update from yesterday trashed a symlink that pointed to your Nvidia gl libs.

For people uncomfortable with building kernels, and making modules, you can use Synaptic to reinstall.  Open Synaptic, click search, put nvidia in the search box.

Find the driver that's currently installed (more than likely, nvidia-glx-new).  Right click it, select reinstall.  Click apply at the top.

For those who are comfortable installing their own kernels and such, feel free to use the updated drivers from Nvidias site.

Edit:  Just realized, if you can't get into X, you won't be able to run Synaptic.  If that's the case do this from a Console terminal (CTRL-ALT-F1)

$ ls /var/cache/apt/archives/nvidia*
Note the output of this, there are several nvidia drivers on the repositories.  The output from mine was: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb

Now enter the following command:
$ sudo apt-get install --reinstall nvidia-glx-new

Use the name of whatver the output was from the LS command previously, without all the numbers at the end.  You should be able to log into X at this point.

---

### Post by mimithebrain on 2008-01-19
> **Fraktyl said:**
> 
Edit:  Just realized, if you can't get into X, you won't be able to run Synaptic.  If that's the case do this from a Console terminal (CTRL-ALT-F1)


I had created another username using the commandline, then I logged in using that username. I then opened the NVIDIA control panel, and stepped through the menus until getting glxinfo crashed the session. It was at that point that I knew that the kernel module was at fault.

That being said, an Xorg session using NVIDIA but not DRI won't be affected, although there isn't much purpose in having a blob for no DRI.

I hope they fix this soon, if it's not done already. Commandline is scary for the average user.

---

