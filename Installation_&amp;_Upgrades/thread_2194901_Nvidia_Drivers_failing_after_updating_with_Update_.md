---
title: "Nvidia Drivers failing after updating with Update Manager"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by The Phone on 2013-12-21
I'm currently using Ubuntu 12.04 LTS 64-bit. After installing all available updates for my system, and a reboot, the following error message shows up:

```
    Starting load fallback graphics devices [fail]
```

I couldn't run any commands, and the system didn't respond to Ctrl + Alt + Del. But if I pressed the power button on my computer the system responded and shutdown the system successfully. After powering up again, the only sign of life was a blinking underscore.  Lucky me, **I had a backup** that I restored. I understand that it's probably the Nvidia drivers that's "broken". So, after restoring my backup, I'm willing to make a successful system update, and preferably without needing to restore my backup.

 About a year ago or so when I installed Ubuntu on my computer, the Additional Drivers Windows looked like this:



[IMG]http://i.stack.imgur.com/3LT2o.png[/IMG]


I installed the Recommended version. Now, a year later, my Additional Drivers windows look like this:


[IMG]http://i.stack.imgur.com/E3nG4.png[/IMG]


The bottom two is identical, while the top two is two different versions, 304.108 and     
304.88. Here's the description of the four different drivers: [http://pastebin.com/j2RD1mD4](http://pastebin.com/j2RD1mD4)

The latest driver according to the description(s) is number 2.

What should I do? Or more like, what would you do? Should I install all updated except the Nvidida ones, or should I try to install the latest one from the Additional Drivers, or what? The ultimate would be to have the latest Nvidida drivers installed, together with a fully updated system.

The following Nvidida related updates is available in the Update Manager, and one/some of them is probably the reason why the graphics is malfunctioning.

[IMG]http://i.stack.imgur.com/4ISr1.png[/IMG]

Thanks in advance!

---

### Post by TheFu on 2013-12-21
Try:
[B]sudo update
sudo apt-get --reinstall install nvidia-current[/B]
from a terminal.

---

### Post by efflandt on 2013-12-22
I have been using nvidia-expermental-310 since January (steam recommended experimental drivers), although, I reinstalled 64-bit 12.04.3 in July after replacing a failed hard drive. For me **Additional Drivers** is as shown below (which is actually 319.32). I did not install anything vdpau specific since I thought that was included with nvidia drivers now (libvdpau1 is installed). Nvidia X Server Settings does show correct driver version and VDPAU info. Not sure why your Additional Drivers looks different, so you cannot even tell which version each is from that.

Strangely dpkg-query longer lists nvidia drivers, but they are there:```
efflandt@xps8100-1204:~$ dpkg-query -l nvidia*
No packages found matching nvidia-pkgs.txt.

efflandt@xps8100-1204:~$ ls -d /usr/src/nvidia*
/usr/src/nvidia-319-updates-319.32
```Maybe you have remnants of more than one version. See what you get for: **ls -d /usr/src/nvidia***

---

