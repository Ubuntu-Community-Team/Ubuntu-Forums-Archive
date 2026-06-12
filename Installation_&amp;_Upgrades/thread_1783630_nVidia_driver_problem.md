---
title: "nVidia driver problem"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by CyClyst on 2011-06-16
I think I have a problem with my nVidia driver.

When I first tried installing my monitor did the No VGA input on boot (but I hear the little drum noise) when I reinstalled I did not install updates during install. This got me to boot into ubuntu. Then I tried to install NVidia accelerated graphics driver (version current) [recommended] but after reboot I got the no vga input on my monitor again. 

What should I do?

Also is there a way to mess around with installing video drivers such that if I install the wrong one I can uninstall it without having to reinstall linux all over agian? Thank you guys!

---

### Post by tommcd on 2011-06-16
You should be able to boot to recovery mode and run:
```
apt-get remove --purge nvidia*
reboot
```
This should reboot you into the default *nouveau* driver for nvidia.
What nvidia graphics card do you have?
Are you using multiple monitors or a KVM switch or something else besides a single monitor connected by VGA or DVI input?

I always install the nvidia driver from the terminal like this:
```
sudo apt-get install nvidia-current mesa-utils nvidia-settings
sudo reboot
```
then after rebooting run:
```
sudo nvidia-xconfig
```
And you should be good.

---

### Post by CyClyst on 2011-06-16
It is a laptop with a broken screen hooked up to an external monitor. The video card is a nVidia Geforce 8600M GT. 

I will try your suggestion when I get home tonight. Previously I had used ubuntus update driver utility to install the recommended driver. Then on reboot I had the blank screen problem again ;(

---

### Post by CyClyst on 2011-06-17
> **tommcd said:**
> You should be able to boot to recovery mode and run:
```
apt-get remove --purge nvidia*
reboot
```
This should reboot you into the default *nouveau* driver for nvidia.
What nvidia graphics card do you have?
Are you using multiple monitors or a KVM switch or something else besides a single monitor connected by VGA or DVI input?

I always install the nvidia driver from the terminal like this:
```
sudo apt-get install nvidia-current mesa-utils nvidia-settings
sudo reboot
```
then after rebooting run:
```
sudo nvidia-xconfig
```
And you should be good.


Sadly this did not work for me! I tried installing the driver the way you described and I got the same problem. Any other ideas?? I was however able to log into recovery mode and purge the nvidia driver so I did not have to re-install, thank you for that!

---

### Post by tommcd on 2011-06-17
Does Ubuntu run ok from the live CD?
Do you have the nvidia-current driver installed now? If so, the post your */etc/X11/xorg.conf* file. You should be able to mount your Ubuntu partition from the live CD, then post the file.
Assuming that Ubuntu is on /dev/sda1 just mount that partition from the live CD:
```
sudo mount /dev/sda1 /mnt
```
Then run: ```
cat /mnt/etc/X11/xorg.conf
```
and post the file here in between code tags if you can.

---

