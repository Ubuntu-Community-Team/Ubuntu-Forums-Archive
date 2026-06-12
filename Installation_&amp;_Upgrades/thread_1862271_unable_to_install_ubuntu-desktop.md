---
title: "unable to install ubuntu-desktop"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by el_anticuado on 2011-10-16
I've just installed Ubuntu server 11.10 in Virtualbox (on my Windows 7 PC), and the installation was successful.  However, I can't seem to install any GUI (Unity, Gnome3, KDE).  Here are the commands that I've tried:

1) sudo apt-get update
2) sudo apt-get install ubuntu-desktop

After the system gets many files, I see 'Failed to fetch ...'.  I also tried 

  apt-get update --fix-missing

with no luck.  Have also tried installing gnome3 via the command:

  sudo apt-get install gnome-shell

but this produces the similar "Failed to fetch .." error messages.

Would appreciate help fix this issue.

---

### Post by MAFoElffen on 2011-10-16
> **el_anticuado said:**
> I've just installed Ubuntu server 11.10 in Virtualbox (on my Windows 7 PC), and the installation was successful.  However, I can't seem to install any GUI (Unity, Gnome3, KDE).  Here are the commands that I've tried:

1) sudo apt-get update
2) sudo apt-get install ubuntu-desktop

After the system gets many files, I see 'Failed to fetch ...'.  I also tried 

  apt-get update --fix-missing

with no luck.  Have also tried installing gnome3 via the command:

  sudo apt-get install gnome-shell

but this produces the similar "Failed to fetch .." error messages.

Would appreciate help fix this issue.
Since you are doing VirtualBox in Windows7... 
 - You just installed the OS.  Close it down.
 - Ensure that Win7 has no background updates going on.
 - Restart your Virtual Machine.
 - Install the virtual Additions.
 - Ensure you have an Internet connection:
```

ping http://www.google.com

```On losing your internet connection, I notice that happening evry once in a while with Win7.  Most of the time it seems to happen while it tries to do background updates.  

//
From here you can either try to use apt-get or aptitude... Since you are having problems and have Server installed, I would use the vga (somewhat graphical) version of aptitude... Aptitude is smarter than apt-get as it relates to dependencies.  You can use aptitude from the commandline just like apt-get --or-- you can use the vga interface.

The VGA interface brings it into the realm of a synaptic on Desktop for Servers that have basic graphics.

- You can start Aptitude by:
```

sudo aptitude

```*** I've done this- various desktops installed on Server --and-- server services installed on Desktop... What is your "goal?"

---

### Post by el_anticuado on 2011-10-16
Thank you for your suggestions.  They provided a very good "clue" to the root cause of the problem -- which was the Network settings in the Oracle VirtualBox.  

After I corrected the Attached to setting from NAT to Bridged Adapter and selected the connected ethernet controller, then the apt-get update worked fine -- and I was able to install the Ubuntu desktop GUI.

My installation issue is fully RESOLVED  -- Thanks again.

---

### Post by Dark Stain on 2011-11-12
hi, I also have a similar problem I'm trying to install a GUI in my Ubuntu server 11.10 but I can't I downloaded the GUI and its in my usb flash how do I install from there?, the GUI is AfterStep. also I cant seem to update im using proxy server but I dont know how to set it up.

---

### Post by raja.genupula on 2011-11-12
> **Dark Stain said:**
> hi, I also have a similar problem I'm trying to install a GUI in my Ubuntu server 11.10 but I can't I downloaded the GUI and its in my usb flash how do I install from there?, the GUI is AfterStep. also I cant seem to update im using proxy server but I dont know how to set it up.

[http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html](http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html)

---

### Post by Dark Stain on 2011-11-14
thanks raja and I have a question. What does this error mean? err http.... something wicked happened hostname cannot ...

---

