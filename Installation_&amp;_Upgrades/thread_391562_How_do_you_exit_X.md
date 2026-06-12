---
title: "How do you exit X?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by Orinoco on 2007-03-23
I am trying to install NVDIA drivers on my new laptop to match the wide screen.  
The default screen resolution is 1024x768 (or 1.33 to 1) and my laptop's screen is 1280x800 (or 1.6 to 1).  

I downloaded the NVDIA driver installer and ran it but it told me I had to exit X.  I did a search, and found the recommendation that I type Ctrl+Alt+F1 to open a terminal and exit X.  However, when I type Ctrl+Alt+F1 as recommended, my screen goes blank and nothing happens. This behavior occurs whether or not I've opened a terminal first.

I have installed Edgy from a CD. The application programs that come with the install (OpenOffice.org, Gimp, Totem) all seem to be working.  I've downloaded Blender and VLC (two of my workhorse programs) but Blender, while working, stretches everything out across the screen because the default resolution isn't wide enough, and the VLC player needs a proper screen resolution to show videos correctly.  

What should I do?

---

### Post by upbeat.linux on 2007-03-23
Take a look at: ```
/etc/x11/xorg.conf
```

Add the following lines under the "Devices" section if it does not already exist:

```
Option "ModeValidation" "NoEdidDFPMaxSizeCheck"
```

Then run

```
nvidia-settings
```

from the terminal

Restart X with:

```
Ctrl+Alt+Backspace
```

This may take up to 20 seconds. It will also bring you back to the logon screen.  Restarting your computer should have the same effect.

System >> Preference >> Screen Resolution and set appropriately. For wide screen you may need to lower the Refresh Rate.

Reference point:

[http://ubuntuforums.org/showthread.php?t=280683&page=2]("http://ubuntuforums.org/showthread.php?t=280683&page=2")

---

### Post by AndrewBarber on 2007-03-23
Try exiting to virtual terminal 2, ctrl + alt +f2.

If you get to a virtual terminal the command to kill X basically would be ```
sudo pkill gdm
```
You could even try this from a terminal emulator too actually..

Also a good little guide can be found on the help.ubuntu wiki site. [BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto).

---

