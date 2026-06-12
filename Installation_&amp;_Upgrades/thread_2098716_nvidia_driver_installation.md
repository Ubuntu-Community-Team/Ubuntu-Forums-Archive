---
title: "nvidia driver installation"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by Caesum on 2012-12-27
Hi,

I'm using 12.04 64-bit ubuntu and after the last few upgrades I've now noticed that my nvidia drivers are no longer being used. I tried to install them from the command line but installation didn't work and the driver isn't being used. So I then removed the driver and tried from the 'additional drivers' in the system settings. but this comes up with an error saying that the installation failed and more details can be found in the jockey.log, see attached. I'm not sure what to do now as I have now tried different versions of the drivers and tried removing them, etc.

Thanks!

---

### Post by WierdKid on 2012-12-28
Could you post which commands use were using to install via terminal?

---

### Post by Caesum on 2012-12-29
I was using this:
```


        sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
        sudo apt-get update
        sudo apt-get install nvidia-current


```

It says it's installed but then as soon as I go into NVidia X server settings it says 'you do not appear to be using the NVidia X driver' and that I need to run nvida-xconfig as root, so I do 'sudo nvidia-xconfig' and it tells me that it's written a new config file, but when I reboot and go back into the settings I just get the same message again.

---

### Post by WierdKid on 2012-12-29
You can give these two a try, they got my NVidia drivers to quit causing compatibility problems, though I haven't tried to use X Server settings.

```
sudo apt-get purge nvidia-*
sudo apt-get install ubuntu-desktop nvidia-common
```

---

