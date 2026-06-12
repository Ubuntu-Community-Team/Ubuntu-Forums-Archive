---
title: "xorg.conf ignored at boot"
date: 2011-06-29
forum: Installation &amp; Upgrades
---

### Post by lbthrice on 2011-06-29
Hi all,

I have an nvidia card that gave me problems at install.
To escape a blank screen after installing ubuntu-server-10.04 I had to put "nomodeset" into my GRUB flags.
This enabled me to login and install nvidia-current driver.
After reboot, things worked pretty well.

Today, I am trying to configure dual monitor display.
I used the command:
```
sudo nvidia-xconfig --twinview
```
to automagically generate an /etc/X11/xorg.conf file.
...after restarting X everything looked great!

Alas....upon reboot I was back to single monitor view.
HERE IS THE STRANGE PART: simply restarting X invokes X to read the xorg.conf and dual screen awesomeness is restored.

Can anyone think of a reason why my /etc/X11/xorg.conf would be ignored at boot time?

Thanks for your help!

---

