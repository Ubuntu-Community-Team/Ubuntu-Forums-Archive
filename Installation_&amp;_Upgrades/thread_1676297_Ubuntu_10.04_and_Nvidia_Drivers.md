---
title: "Ubuntu 10.04 and Nvidia Drivers"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by sumdude616 on 2011-01-27
Hey how's it going.. I'm pretty new to Ubuntu and so far have loved it. I've ran into a problem tonight where I restarted my computer because my mouse wasn't responding. When I turned the computer back on everything started loading up properly and then the bottom half of the screen went black covering my wallpaper but when i run my cursor over Docky, Docky still comes up but with the black area still there Pictures will show what i'm talking about. I tried to restart my computer once again to see if maybe it was just an error but it kept doing the same thing. All of a sudden I get another error that the computer has to run in low graphics mode? (NOTE: When the screen first lights up to ask for my password the entire screen works, once I enter my password 5secs will go by and then the bottom half goes black again.) So i didn't know why it was doing this. I went to Systems>Admin>NVIDIA X Server Settings. When I clicked on that to maybe change the resolution or see if anything in there could fix the problem I was confronted with --You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.--

I tried re-downloading NVIDIA but I figure before I mess this up anymore than I already have I should just seek help from someone who knows what they are doing..Can I get any help Please and Thank You.[IMG]http://i57.photobucket.com/albums/g206/sumdude4663/Screenshot-3.png[/IMG][IMG]http://i57.photobucket.com/albums/g206/sumdude4663/Screenshot-4.png[/IMG]

Oh also when I tried to run nvidia-xconfig I go: 

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

---

### Post by Townley89 on 2011-01-27
Did you try installing from the nvidia download package or using the system>admin>additional drivers option? The latter's a pretty safe bet for a safe installation, but the former can help if the built-in method doesn't work.

What sort of a system are you running, and what is your card? Might not be related, but I had similar issues when my NVidia was conflicting with my integrated video, resulting in the comp crashing unless I ran it in low-graphics mode. Try disabling the NVidia card under additional drivers and turn off Docky to see if that solves the black bottom of the screen issue. If that's the problem, the fix might not be pretty and I still haven't got it quite working. Hopefully that's not the beast you're messing with. 

Also, have you checked that your visual effects are at "extra"? (system>preferences>appearance>visual effects>extra) Not having that can cause the screen/docky to do wacky things sometimes.

---

### Post by Sylos on 2011-01-27
> **sumdude616 said:**
> 

Oh also when I tried to run nvidia-xconfig I go: 

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.

Did you definitely run the comand as root. ie:

```
sudo nvidia-xconfig
```

---

### Post by runeh76 on 2011-01-27
Hi (This is for Ubuntu 10.10), but u could try it  ;)

Try this to uninstall and reinstall Nvidia:

1. Uninstall any previously installed Nvidia drivers:

```
sudo apt-get --purge remove nvidia-*
```

2. Install Nvidia

```
sudo apt-get install nvidia-current
```

3. Then restart you computer, run the command to create the configuration file:
```
sudo nvidia-xconfig
```
Log out and back in ,and you can now change nvidia settings by System &#8211; > Administration -> Nvidia X server Settings

---

