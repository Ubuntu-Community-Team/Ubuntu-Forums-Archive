---
title: "Can't startx after trying to install lm-sensors"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Rich1386 on 2007-07-22
I used this thread to try and install lm-sensors.   [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

I had a problem that many others have posted about.  My output of "sudo sensors" was always that no sensors were found, even though they had been added to etc/modules.  At this stage, I would have to be in recovery mode, because trying to boot the normal kernel resulted in a blank screen.  

In the text that scrolls before recovery mode is fully booted, it used to say that "setting sensor limits...failed" but I don't see it anymore.  Doing "startx" in recovery mode results in error messages about the NVIDIA driver (100.14.11) and how no screens were found, then this "fatal IO error 104 lm-sensors".

I tried commenting out the added entries to etc/modules, and purging lm-sensors, but I still can't get back to normal.

Thanks

---

### Post by rocknrolf77 on 2007-07-23
Try ```
sudo nvidia-xconfig
```

or

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And then ```
sudo /etc/init.d/gdm restart
```

To start gdm

---

### Post by Rich1386 on 2007-07-23
The X server fails to start and i get an error message 

Error:  API mismatch:  this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match.  Please make sure that the kernel module and all NVIDIA driver components have the sme verison.

---

### Post by Rich1386 on 2007-07-23
Anyone?

---

### Post by rocknrolf77 on 2007-07-23
After the xserver fails to start you are in the shell/terminal?

If so, log in with your username and password. 


Then type ```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.6-0ubuntu2_all.deb
```

Then

 ```
sudo dpkg -i envy_0.9.6-0ubuntu2_all.deb
```

Then

```
sudo envy -t
``` 

Follow the instructions to install the nvidia driver. It will take care of everything for you. When it's finished say yes to configure your xserver and follow the other instructions.

Hoping this will work for you :)

---

### Post by Rich1386 on 2007-07-23
Thanks, it got it going!!

There were a bunch of errors when doing the command to configure envy, but it all ended up fixing it.

Many thanks

---

### Post by rocknrolf77 on 2007-07-23
The errors are nothing to worry about. It's just the script checking out what to do :)

If for some reason the same thing happens again, just run sudo envy -t and things will work again.

---

