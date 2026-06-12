---
title: "Driver Issues after install"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by shabti87 on 2012-11-23
Hi all,

I recently upgraded to 12.10 from 12.04 and have been having some driver issues. (I'm pretty sure that's the only problem, because I can start up in run level 3 'text' mode and can run anything from there.) I have an Nvidia Quadro NVS 290 card installed, and for the time being I'll be happy with one working monitor. I tried all the typical things: purging all Nvidia related drivers, and reinstalling a new set (I've tried nvidia-current and nvidia-experimental-###), but every time I try startx from a command line, startx hangs on the line

Loading extension NV-CONTROL 

I looked around, but could not find any other issues that were not solved using the steps I already tried (purge + reinstall drivers).

Some added information:

lspci -vvnn tells me:

Kernel driver in use: nvidia
Kernel modules: nvidia_current, nouveau, nvidiafb

This worries me a bit because to get the drivers working well in 12.04 I had to blacklist both nouveau and nvidiafb in modproble/blacklist.conf

If I go right into graphical mode, I get a login screen with the correct resolution for the monitor, but if I try to log in, I get logged right back out almost instantaneously.

I should also mention that I have updated/upgraded every time I tried anything, so the system has all the latest everything else there is.

I'm not sure what other drivers to try

Thanks for any help on this!

---

### Post by 2F4U on 2012-11-23
Have you tried to blacklist the kernel modules nouveau and nvidiafb when using the nVidia proprietary driver?

---

### Post by shabti87 on 2012-11-23
Yes, those are both currently blacklisted, and I'm trying to use the nvidia drivers. I took a look through the log file, and I noticed a few other errors:

(EE) Failed to load module "nv" (module does not exist, 0)
...
(EE) Failed to load module "nv" (module does not exist, 0)
...
(EE) open /dev/dri/card0: No such file or directory
(EE) open /dev/dri/card0: No such file or directory
...
(EE) open /dev/fb0: No such file or directory
...

None of these seem to be bad enough to be a fatal error, but maybe they are a root cause.

Thanks!

---

### Post by NikTh on 2012-11-23
Hi , 
take a look at this thread please : [http://ubuntuforums.org/showthread.php?t=2084412](http://ubuntuforums.org/showthread.php?t=2084412)
oldfred's answer - post #3. 

Thanks

---

### Post by ashwinrao on 2012-11-23
I'm not sure if this helps or not.  Have you tried removing .Xauthority file from the home folder? I had a same issue which resolved by this method. Not sure about the relevance of this file. Some one will shed more light on it.

---

### Post by shabti87 on 2012-11-23
> **NikTh said:**
> Hi , 
take a look at this thread please : [http://ubuntuforums.org/showthread.php?t=2084412](http://ubuntuforums.org/showthread.php?t=2084412)
oldfred's answer - post #3. 

Thanks

Thanks. I tried this with both the nvidia-current-updates as well as the nvidia-experimental drivers, but neither seems to help. I tried again just now for good measure, but I end up with the same behavior. 

Using the nvidia drivers I can get a background screen and see the mouse on startx, but that is it. After a fresh reboot XINTERAMA also seems to be loaded.

...
Loading extension GLX
Loading extension NV-GLX
Loading extension NV-CONTROL
Loading extension XINTERAMA

---

### Post by shabti87 on 2012-11-23
> **ashwinrao said:**
> I'm not sure if this helps or not.  Have you tried removing .Xauthority file from the home folder? I had a same issue which resolved by this method. Not sure about the relevance of this file. Some one will shed more light on it.

I tried this just now. Unfortunately removing that file did not seem to help at all.

Thanks

---

### Post by shabti87 on 2012-11-23
Just an update.

I gave up on the drivers I get through apt-get, and I got the drivers directly from NVIDIA after purging the old drivers:

sudo apt-get purge nvidia*

wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/NVIDIA-Linux-x86_64-310.19.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/NVIDIA-Linux-x86_64-310.19.run)

sudo ./NVIDIA-Linux-x86_64-310.19.run

sudo shutdown -r now


Now it seems that the resolution is much better (even in text mode) but I still can't seem to see anything past a background and a mouse when I try

sudo startx

And I have the same trouble in the login screen (If I try to log in through the graphical login, I get logged back out immediately). I am starting to think that maybe this problem is not just a driver issue. Any ideas are very welcome.

Thanks all!

---

### Post by ashwinrao on 2012-11-23
Please try  reinstalling lightdm once. I recommend further reading these: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951404](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/951404) and [https://answers.launchpad.net/ubuntu/+source/lightdm/+question/197479](https://answers.launchpad.net/ubuntu/+source/lightdm/+question/197479).

---

### Post by NikTh on 2012-11-23
> **shabti87 said:**
> Just an update.

I gave up on the drivers I get through apt-get, and I got the drivers directly from NVIDIA after purging the old drivers:

sudo apt-get purge nvidia*

wget [http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/NVIDIA-Linux-x86_64-310.19.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/310.19/NVIDIA-Linux-x86_64-310.19.run)

sudo ./NVIDIA-Linux-x86_64-310.19.run

sudo shutdown -r now


Now it seems that the resolution is much better (even in text mode) but I still can't seem to see anything past a background and a mouse when I try

**sudo startx**

And I have the same trouble in the login screen (If I try to log in through the graphical login, I get logged back out immediately). I am starting to think that maybe this problem is not just a driver issue. Any ideas are very welcome.

Thanks all!

No ,no , do not do this please. Is not recommended to start X as root. You can create problems with permissions .. etc. startx only as a normal user. 
Try to remove .Xauthority 
```
rm ~/.Xauthority
``` and try to stop and start the DM (lightdm). 
```
sudo service lightdm stop
sudo service lightdm start
```startx not always initialize the connection correctly , also it take too long sometimes. 
If you want to use startx , then use it as a normal user ```
startx
```and if you get only a background and a mouse cursor , then open a terminal CTRL+ALT+T and try to restart the environment ```
setsid unity
```---------------------------------------------------------------------------------------------------------------------------
What about nouveau ? Have you tried it ? I mean, purge nvidia completely and see if you can use nouveau (the open source pre-installed driver). 

```
sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo rm /etc/X11/xorg.conf 
sudo apt-get install nvidia-common ubuntu-desktop
echo "nouveau" | sudo tee -a /etc/modules
sudo dpkg-reconfigure xserver-xorg
```Reboot your system and see. 

If not working , the only thing you have to do , is to remove "nouveau" from /etc/modules and of course , re-install Nvidia driver.

Thanks

---

### Post by shabti87 on 2012-11-24
> **NikTh said:**
> No ,no , do not do this please. Is not recommended to start X as root. You can create problems with permissions .. etc. startx only as a normal user. 
Try to remove .Xauthority 
```
rm ~/.Xauthority
``` and try to stop and start the DM (lightdm). 
```
sudo service lightdm stop
sudo service lightdm start
```startx not always initialize the connection correctly , also it take too long sometimes. 
If you want to use startx , then use it as a normal user ```
startx
```and if you get only a background and a mouse cursor , then open a terminal CTRL+ALT+T and try to restart the environment ```
setsid unity
```---------------------------------------------------------------------------------------------------------------------------
What about nouveau ? Have you tried it ? I mean, purge nvidia completely and see if you can use nouveau (the open source pre-installed driver). 

```
sudo apt-get purge nvidia-*
sudo apt-get install --reinstall xserver-xorg-video-nouveau
sudo rm /etc/X11/xorg.conf 
sudo apt-get install nvidia-common ubuntu-desktop
echo "nouveau" | sudo tee -a /etc/modules
sudo dpkg-reconfigure xserver-xorg
```Reboot your system and see. 

If not working , the only thing you have to do , is to remove "nouveau" from /etc/modules and of course , re-install Nvidia driver.

Thanks

Haha yea I noticed that .Xauthority thing while looking through some related bugs that were brought to my attention. I fixed that and I can log in now from the login screen, but I still only get  a background and mouse. So I know now that my .Xauthority file is correct, and I'm also fairly certain my drivers are working. To test that I added 
```
 exec twm 
``` to my .xinitrc file to use twm. Once in a simple windows manager, I could open a terminal and run
```
glxgears
```and
```
glxinfo 
``` to check that drivers were functioning properly.
Given that those all came back positive, I tried an alternate windows manager lxde, and so far that has been working just fine. Aside from no knowing how to make it so that desktop icons only appear on one of my two monitors, dual monitors work, I can log in with lxde from the login screen, I am free from the .Xauthority issue and I can run all the programs I need to. 

Logging in with the standard Ubunty desktop manager still gives me the background and mouse, an I can't seem to start a terminal (using CTR-ALT-T). For the time being, lxde is suitable for me, but I am still puzzled with Unity's failure to start. I'm not sure if I would call the problem [solved], but still a bit of a pain.

Thanks all for help!

---

### Post by NikTh on 2012-11-24
Hi , 
glad you fixed (even with another DE, LXDE is a good DE , I use it too)

What drivers you use now ? nvidia's proprietary or nouveau ? 

Ubuntu standard display manager is lightDM. You can examine some logs and see if you can find something interesting there. 
```
sudo cat /var/log/lightdm/lightdm.log
sudo cat /var/log/lightdm/x-0-greeter.log
cat /var/log/Xorg.0.log
```Thanks

---

