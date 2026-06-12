---
title: "How do you install Nvidia's proprietary drivers?"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by Gildon on 2014-02-03
Hello. I am trying to install Kubuntu on my system with a Geforce GTX 780. Originally, when I try to log in, its appears as if I succeeded but then the resolution gets messed up and I get kicked back to the log in screen. I have a feeling this has something to do with my graphics drivers but I can successfully log in when in recovery mode. Anyway, I downloaded Nvidia's driver NVIDIA-Linux-x86_64-331.38.run. I boot into recovery mode in hopes of not interfering with the X server or other OpenGL applications. I then run the following commands and get the following:
```
# chmod +x NVIDIA-Linux-x86_64-331.38.run
chmod: changing permissions of 'NVIDIA-Linux-x86_64-331.38.run' : Read-only file system
# sudo ./NVIDIA-Linux-x86_64-331.38.run
Unable to create temporary file in /tmp
```

I have tried looking in other forums to try to find a solution to this /tmp problem with no prevail. Any help would be greatly appriciated. Thanks.

---

### Post by TheFu on 2014-02-03
Are you running from a livecd?

Also - installing any software outside the package manager sorta defeats the main reason for using Debian/Ubuntu - the fantastic package management and update processing.  With GPU drivers and Linux, newest is seldom the best.  I'd recommend using a PPA.

Anyway - [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) should explain.

---

### Post by Gildon on 2014-02-03
When I try to install the proprietary drivers with the Additional Drivers app, I the download of the package just hangs at 0%. I have tried numerous ways at installing the driver and now it seems that I just have to disable nouveau. I have blacklisted numerous ones including nouveau and vga16fs already but I think nouveau is stored inside initramfs which requires a complete rebuild. Can anybody confirm? I have also heard that it works if I go into recovery mode and drop into the console. With I go to a lower runlevel with ```
init 3
``` it askes for my kpassword and for some reason my user password will never work. I have absolutely no idea what to try at this point.

---

### Post by TheFu on 2014-02-04
There is something very wrong. /tmp should NEVER be read-only.  That is why I asked the first question.  Did the system ever work? Is it installed to a normal HDD?  Anything unusual about your hardware?  UEFI, SSD, which Ubuntu release?

I think it is unrelated, but usually way to change init states is with "sudo telinit 3" - you shouldn't need that - I haven't needed it in may years and never for anything related to GPU.

---

### Post by LukasLeon on 2014-02-04
Have you tried to install it as a root? aka, you type "sudo su" in terminal and after that you try to install the driver.. Also as said above, it is not recommended to use the drivers from geforce site, it is better to use additional drivers, or by ty typing following to terminal: 

sudo apt-get update
        sudo apt-get dist-upgrade
sudo apt-get nvidia-current

This will install the latest drivers provided by ppa.
Also you can use an unnoficial ppa, which works better in some cases.

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
        sudo apt-get update
sudo apt-get dist-upgrade
        sudo apt-get install nvidia-current

Learn more about all ways of getting nvidia drivers here [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

---

