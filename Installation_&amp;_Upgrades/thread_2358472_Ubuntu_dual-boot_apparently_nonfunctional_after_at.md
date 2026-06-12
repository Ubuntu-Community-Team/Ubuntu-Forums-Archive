---
title: "Ubuntu dual-boot apparently nonfunctional after attempted NVIDIA Cuda install"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by reesej2 on 2017-04-13
I'm running a dual-boot of Windows 10 alongside Ubuntu 16.10. I attempted to install the Nvidia CUDA development kit and drivers (for Ubuntu 16.04, which in retrospect I suppose was a bad decision), with the result that I don't seem to be able to get to any sort of login screen. When I boot into Ubuntu, the loading screen appears briefly, and then is replaced by a black screen. Attempts to enter the terminal using Ctrl-Alt-F1 and similar have no effect. Naturally, I booted into recovery mode and purged everything Nvidia (apt-purge nvidia*) and, just to be sure, tried installing Nouveau again (apt-install xserver-xorg-video-nouveau) and rebooted. This had no effect. I've also seen suggestions that I try hitting e in GRUB, editing the Ubuntu start file by adding nomodeset before "quiet splash". This does have an effect, but the only result is that it skips the loading screen entirely and goes directly to the black screen.

My guess, based on little to no experience with Ubuntu, is that my graphics drivers have gotten mixed up. The natural fix, if I could get in, would be to manually uninstall and reinstall all graphics drivers; but since this didn't seem to work from recovery mode, I'm not sure where to go from here. Is there a way to do it from the Windows partition? Or is there something else entirely I can try?

---

### Post by efflandt on 2017-04-14
Which nvidia card do you have and which nvidia driver package did you install? If you used a run file from nvidia.com instead of an Ubuntu package I am not sure how to remove that.

If you have a fairly recent card like GTX 10xx series you might need a newer driver than is in the standard repos and need to add the graphics-drivers ppa. Note that Ubuntu 16.04 and newer can use "apt" instead of "apt-get", but either works.```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-378
```Or the most recent is nvidia-381 which I have not tried yet. I am using nvidia-378 with CUDA things installed for my GTX-1060. I don't even think the nouveau driver supports my card, although live/install version worked, maybe frame buffer mode. So I had to install nvidia driver from recovery before I could even boot to gui login and have it work.

So you may need to do that from recovery boot, if you can get networking to work (which also remounts the drive read-write) and then go to root console (where you do not need "sudo"). The easiest tool to install other things is "synaptic" because that tells you which version packages are which Ubuntu Software Center does not.

---

### Post by ubfan1 on 2017-04-14
I did briefly test the CUDA 16.04 download under 16.10, and basically just had to add a gcc5, since the gcc6 was the default.  I was using the 375.39 driver, which did cause some screen artifacts around the boarders, but that's the 375, drop back to 367 to avoid that.  See the bug and questions to avoid the artifacts (kill compiz or force the 367 driver).

---

### Post by reesej2 on 2017-04-15
I have a 940MX card; I installed the .run file from nvidia.com for the latest driver (I think 381). After trying your suggestions, I'm presented with a related issue: networking doesn't seem to be working. When I run the lines you suggested, I get (in order) a complaint that user "~graphics-drivers" does not exist, "temporary failure resolving us.archive.ubuntu.com", and a whole string of "E: Failed to fetch..." in response to attempting to install nvidia-378. Trying to get networking to work, I tried a suggestion I found elsewhere, running "ifconfig wlan0 up", which gave the error message that there is no such device. iwconfig shows one wireless device, wlp3s0, which it says is using the correct essid; ifconfig says this device is up, but also seems to think it's an ethernet connection (if I'm reading this correctly). This machine does not have an ethernet port. I also tried "service network-manager start", which hung for a while before aborting the task without starting the NetworkManager because it had timed out. Is there any good resource I could consult for connecting to the internet from recovery mode?

---

### Post by efflandt on 2017-04-16
When you boot to recovery mode if you just go to a root console any partitions are mounted read-only. So you either need to know how to remount everything read-write and start networking, or if you enable networking from the recovery menu, it remounts everything read-write for you and enables networking. But for wireless, that assumes that you already have wireless configured with security settings to function properly. Sometimes when you enable networking from there and some device is not recognized it may hang and if that happens I am not sure how to get back to the recovery menu.

I don't know why they came up new confusing names for network devices. It used to be simple eth0 was your first Ethernet device and wlan0 was your first wireless device. Now my Ethernet is enp5s0 and my wireless is wlp4s0. The **ifconfig** command would show if your wireless got an automatic IP address and **route -n** would show if you have a default route to your router (the UG route). I have a wireless bridge that I sometimes use when installing Linux, because then I do not have to find and enter wireless security settings. I normally use the gui for NetworkManager (from applet at top of screen) to edit network connections, so I do not know exactly how to configure files in /etc/NetworkManager/system-connections/ manually.

---

### Post by reesej2 on 2017-04-16
All right, I got it! Thanks. For future reference, what was preventing me from getting networking working was that WEP and WPA/WPA2 are handled differently, so a WPA2 network needed a completely different sequence of instructions for connection. I found an excellent tutorial at [http://linuxcommando.blogspot.com/2013/10/how-to-connect-to-wpawpa2-wifi-network.html](http://linuxcommando.blogspot.com/2013/10/how-to-connect-to-wpawpa2-wifi-network.html) . Once I'd done that, the sequence of commands you gave me to begin with worked like a charm.

---

