---
title: "NVIDIA Problem after 8.10 upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by the_nite_owl on 2008-05-06
Posted this once but it never showed in the forum.  Sorry if it shows up twice for some reason.

I upgrade 7.10 x86 to 8.04 last night and everything went well except for the video driver.
I have an nvidia GeForce 6100.
After reboot the system prompted me to adjust the video settings and it had defaulted to a generic VESA driver at 800x600.
I could not find the GeForce 6000 series in the driver list so I tried GeForce 6 but that forced me back to 640x480.

I tried installing the glx-new drivers which is what I did when I installed 7.10 but it did not help.  Enabling the restricted driver causes the video to drop from 800x600 to 60x480.
I have removed and reinstalled several times with the same results.

Anyone know a good step-by-step tutorial for installing/enabling the nvidia drivers?  I see a lot of others having issues with their nvidia setup though none are exactly the same as mine and either their solution did not work for me or they have not yet posted a solution.

Thanks.

---

### Post by ztirffritz on 2008-05-06
Have you tried using EnvyNG?  It is in the Synaptic Repos now.  If you're using Gnome, then use EnvyNG-GTK.  For KDE use EnvyNG-QT.

---

### Post by the_nite_owl on 2008-05-06
> **ztirffritz said:**
> Have you tried using EnvyNG?  It is in the Synaptic Repos now.  If you're using Gnome, then use EnvyNG-GTK.  For KDE use EnvyNG-QT.

Made some progress.  It turned out that it was my monitor settings that were off so it would never give me the higher resolutions as options.
On my last boot the login screen was WAY off with the ID window almost off the bottom edge of the screen but after logging in I was at an 800x600 desktop and was able to change to 1280x1024.
I have to reboot again and see if the login screen has adjusted or if I have to tinker somewhere to get that straightened out.

---

### Post by Takmadeus on 2008-05-06
I have exactly the same problem. got to install the nvidia driver, but there is no way it will allow me to have my login screen out of 800x600x24

this is driving me crazy

thanks in advance

Found the solution!

[http://ubuntuforums.org/showpost.php?p=4897595&postcount=2](http://ubuntuforums.org/showpost.php?p=4897595&postcount=2)

Hope that helps anyone ;)

---

### Post by the_nite_owl on 2008-05-07
Takmadeus, thanks for the info.  It solved my problem.
My original problem had to do with setting the monitor settings.
My monitor was connected through a KVM and I dont think it could be auto-detected to set it up.  I had to manually select a monitor type that fit my monitor's specs.  After that I was able to set my video settings to higher resolutions.
The info you provided the link to fixed the secondary problem with the login screen being way oversized.

Thanks.

---

### Post by shaoxuan on 2008-05-08
Hello the_nite_owl, 

My monitor was connected through a KVM too. But I'm a totally beginner in using ubuntu, I can't find any way to manually select a monitor type that fit my monitor's specs. Can you shine your wisdom on me? 

Thanks.

---

### Post by the_nite_owl on 2008-05-08
> **shaoxuan said:**
> Hello the_nite_owl, 

My monitor was connected through a KVM too. But I'm a totally beginner in using ubuntu, I can't find any way to manually select a monitor type that fit my monitor's specs. Can you shine your wisdom on me? 

Thanks.

When I booted my machine it would bring up a dialog box telling me it was running in low graphics mode and has an option to configure.  Once in the configuration it has a button with the monitor type listed. Mine was listed as Plug n Play.  I clicked on it and it brings up a list of monitor types on the left and max resolutions on the right.
My monitor supports 1280x1024 so I left the left panel setting on a generic option and changed the right side option to 1280x1024.  I saved the settings and when I got into Ubuntu I was able to change the resolution.

I do not know how to get to the screen that makes those changes if it does not come up automatically at boot except that after trying to re-install my video drivers and turning OFF the restricted driver under System/Administration/Hardware Drivers the dialog box would come up at the next boot.

---

### Post by shaoxuan on 2008-05-08
Hello the_nite_owl,

Thank you for your really helpful advise.:)

---

### Post by RgnadKzin on 2008-05-08
I had to unplug my monitor from the KVM and plug it directly into the ubuntu box.  I then rebooted in recovery mode and used the xfix option.  After that I was able to reboot and the screen resolutions were back.

---

### Post by roboa1983 on 2008-08-11
Hi
I have been battling this problem on and off for about two or three weeks now. 
For some reason, although I have manually installed the nvidia driver executables for the GeForce 6100, I cannot enable it on 
System->Administration->Hardware Drivers.

However, I (finally) decided to use the oldest version of the xorg.conf file I had saved (it included the right measures for the screen), did Ctrl+Alt+Backspace and finally, the correct resolution was included.

Therefore my problem is half-fixed, since now I have the proper resolution, but my nVidia system is not fully operational (I have tried Envy and downloading nvidia-glx(-new) cannot download).
Thanks for the tips.

---

### Post by Rebelli0us on 2008-08-11
That happened to me too, also I lost the sound. I tried fixing it but in the end I just did a clean re-install and it works fine now.

---

### Post by Shrav on 2008-10-30
Hi all
I also had issues with the beta and my on board GeForce 6100. Upgrade and clean install gave me the black screen with 2 pixels at the top. Yes probably KVM related here too. Did get to the desktop but no menubars etc with Compiz. Been Googling for days.. has anyone got the Geforce 6100 to work properly? I'm almost to the point where I'm thinking of buying a new video card but I haven't seen a definitive thread of what actually is working. Can we purge the old hardware threads and make a new one on Intrepid? Who really cares what works with Badger or Eft at this point LOL

---

### Post by the_nite_owl on 2008-10-31
Interestingly after a recent set of software updates from a couple weeks ago when I rebooted my machine it came up in 800x600 mode and would give me no higher resolutions.  I rebooted again and it came up in the full 1280x1024.

The issue is a combination of settings for your video card and settings for your monitor.  I have never found anything comprehensive to fix both problems.  But somehow the problem resolved itself for me.

Let me know if you need me to post my xorg.conf file, it may help you get part of the way anyway.

---

