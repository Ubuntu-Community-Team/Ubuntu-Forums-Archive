---
title: "Display trouble"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by x1a4 on 2007-11-13
Hi,

After upgrading to Gutsy my main user account, the one I used to upgrade, works more or less fine, but whenever I switch X displays, regardless of what desktop I'm running, the screen is blank and I have to open an application or switch workspaces to see what's on the screen.  

Also, I cannot set Nvidia settings except on the main account.  On any other I get a message I'm not using the Nvidia X driver and should run nvidia-xconfig.  I've run it to no avail.  According to the Restricted Drivers Manager nvidia is running, and in xorg.conf the driver is set to 'nvidia'.  

How do I fix this?  

Thank you.

---

### Post by raashell on 2007-11-13
This is just a hint that might be of help to you.  I believe that Gnome keeps separate settings for each user.  How and why this happens, I'm still figuring it out.  I had a problem where even though I saved nvidia-settings with one user to a resolution, whenever I logged out and back in the settings wouldn't stay set.  It turned out that in my user's home directory was a hidden directory called  /.gconf .  (type ls -a in your home directory to see if you have same)  Inside this directory were settings specific to that user in xml files.  To view the files for different settings you can use cat  (i.e.:  cat %gconf.xml).

I'm sure a more experienced user can say whether or not this could be the problem and if there is a way to use Gnome's interface to correct it.

Hope this is of some help.

John

---

### Post by x1a4 on 2007-11-23
Thanks for the effort but that's not it.  For one I don't use Gnome, and second, the problem persists regardless of which GUI I'm using--Xfce, FVWM-Crystal, AfterStep or WindowMaker.

---

