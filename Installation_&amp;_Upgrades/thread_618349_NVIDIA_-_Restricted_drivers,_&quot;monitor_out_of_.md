---
title: "NVIDIA - Restricted drivers, &quot;monitor out of frequency&quot;"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by tiger.woods on 2007-11-20
I just did a fresh install of Gutsy 7.10 and all was good until I decided to install the Restricted Drivers now it's just a black screen at boot with the error "Out of Frequency" on my monitor.

My monitors native resolution is 1400x900 -  I'm assuming that is what is creating the problem I'm also am running an FX5200 AGP card . 

I've been able to reboot and log in for editing of my xorg.conf but I'm not sure what will fix it? I've read a lot of posts with different suggestion, anyone have a fix for this?

Thanks,

---

### Post by taurus on 2007-11-20
You can reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tiger.woods on 2007-11-20
If I recall correctly the last time I ran that utility it didn't include the correct screen resolution of 1400 x 900 in the list of resolutions to select.

How do I go about adding the correct information for my monitor?

Thanks,

---

### Post by taurus on 2007-11-20
If you want to edit it by hand, just run

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by tiger.woods on 2007-11-20
I'm OK with editing it by hand but I don't know what to put in it... kind of the gist of what my problem is.

Thanks.

TW,

---

### Post by taurus on 2007-11-20
Scroll down until you get to the Screen section and just add your desire resolution in there.

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "LM201XD"
        Defaultdepth    24
        SubSection "Display"
        Modes           **"1400x900"** "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection

```
Save it and either reboot or restart X again with <Ctrl><Alt>Backspace.

---

### Post by tiger.woods on 2007-11-20
Thanks I'll give that a shot and post back.

TW,

---

### Post by tiger.woods on 2007-11-20
> **taurus said:**
> You can reconfigure your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


I was able to get the system back up and running with the above, thanks.

I modified the Xorg.conf file to include 1440x900 which is the correct settings not 1400x900 I'm now faced with a little bit of over scan, is that normal? should that be removed using the monitor or the OS?

Thanks,

[EDIT]

The monitor won't adjust it out so it has to come from the Xorg.conf somehow...

---

### Post by tiger.woods on 2007-11-20
Just wanted to post the final solution.

After getting the system back up with 'sudo dpkg-reconfigure -phigh xserver-xorg' I went into "Screens and Graphics" selected "Model" used "Generic" and the correct resolution and made sure to check the box labeled "WideScreen Monitor".

I rebooted and the over scan issue had been corrected and the picture is excellent, just for kicks I opened the Xorg.conf and it had been highly modified with actual Modelines in the "Monitor" section and the SubSection "Display" also had modifications to the modes with an appended @60 e.g. "1440x900@60"


Thanks for the help.

TW,:)

---

