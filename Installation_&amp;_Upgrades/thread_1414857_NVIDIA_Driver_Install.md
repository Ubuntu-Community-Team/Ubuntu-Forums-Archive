---
title: "NVIDIA Driver Install"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by shnurui on 2010-02-24
After installing the Nvidia Newest possible driver from tty1, I am unable to reboot into gnome and the screen flashes ignoring the input from the keyboard.

If I hit esc after the flashscreen, it just goes to tty1.

---

### Post by RRF2525 on 2010-02-24
Does your screen go black then loss of signal?  More detail please...

---

### Post by nerdy_kid on 2010-02-24
does this help?
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
sudo nvidia-xconfig

```

then reboot (sudo reboot)


if not, then
```

sudo rm /etc/X11/xorg.conf

```
reboot,
and then at least you should get a display to try to find the issue.
good luck

---

### Post by tommcd on 2010-02-24
> **shnurui said:**
> After installing the Nvidia Newest possible driver from tty1, I am unable to reboot into gnome and the screen flashes ignoring the input from the keyboard.
So you installed the driver from nvidia.com? Is that correct?
The nvidia driver from the Ubuntu repositories should always be your first choice. This is always easy to install; and it is well integrated into the Ubuntu OS. You should only install the driver from nvidia.com if the driver in the Ubuntu repos will not work for you for some reason. For example, if you have a bleeding edge nvidia card that is not supported with the driver in the Ubuntu repos.
What nvidia card are you using?

---

### Post by RRF2525 on 2010-02-24
While we're on the topic...I started w/the resident NV drivers in 9.10  On doing a clean install of 9.10 from Live CD I got 1280x960 but not the native resolution for my cards/monitor (1680x1050).  Both my Sceptre X20G Naga III and XFX 6800 GS SLI cards support this resolution but 9.10 will not render it.  

On this I thought...okay...we'll just enable the recommended restricted driver for NV (185) included w/9.10.  What happens on reboot?  Ubuntu starts to fire-up, the monitor looses signal and video dies before the desktop happens.  All I get is a glance at the Ubuntu logo at boot and that's all she wrote!

At that point I have to do what you've outlined above...login as root to the console and rm xorg.conf.  I've renamed it along the way many, many times and played with the options and even forced Display Properties to show 1680x1050 but even if I do select it 9.10 will not produce it.  Only an error message claiming that this is not a valid configuration.  

nvidia-settings is not running properly and nvidia-xconfig want to run one of the installed NV drivers.  I have d/l'd the latest from NV but that seems to have corrupted my machine along the way.  After that I reinstalled and started over again.

Getting tired of the wrong aspect ratio as I have graphics to do and cannot do them as it is right now.  I'm sick to DEATH of windows and want to ditch it in the worst way ever! 

Any thoughts?

---

### Post by tommcd on 2010-02-25
> **RRF2525 said:**
> 
nvidia-settings is not running properly and nvidia-xconfig want to run one of the installed NV drivers.  I have d/l'd the latest from NV but that seems to have corrupted my machine along the way.  After that I reinstalled and started over again.

You should remove the driver from the Ubuntu repos before you install the driver from nvidia.com.

You should be able to get 1680x1050 resolution with the nvidia 185 driver in the Ubuntu repos.
Here is the most fail safe way to install the nvidia driver from the repos in Ubutnu. I am assuming that you are starting from a clean install, without having installed any nvidia drivers yet:
First, hit ctrl + alt + F2 to get to a virtual terminal and login there. Then run:
```
sudo service gdm stop
```
This will stop the X server. Then run:
```
sudo apt-get update
sudo apt-get install nvidia-glx-185 nvidia-settings

```
After the driver is installed run:
```
sudo nvidia-xconfig
```
Then restart X:
```
sudo service gdm start
```
Or just reboot with "sudo reboot".
Then to see if 3D is enabled:
```
glxinfo | grep -i direct
```
It should report "direct rendering: Yes". Then run nvidia-settings with sudo:
```
sudo nvidia-settings
```
and you should be able to set your proper resolution. Hope this helps.

---

### Post by dabl on 2010-02-25
Maybe something in this will help:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

allowing for the differences in Gnome:

gdm instead of kdm
gedit instead of kate
gksu instead of kdesudo

---

### Post by darkod on 2010-02-25
@tommcd

Sorry to jump in on this thread. It seems you are experienced with graphics and nvidia. Would you mind taking a look here please:
[http://ubuntuforums.org/showthread.php?t=1411973](http://ubuntuforums.org/showthread.php?t=1411973)

I was trying to help two separate people with nvidia issues (it seems) but I don't know too much about it. We tried bunch of things and nothing seems to help. :(

---

### Post by tommcd on 2010-02-25
> **darkod said:**
> @tommcd

Sorry to jump in on this thread. It seems you are experienced with graphics and nvidia. Would you mind taking a look here please:
[http://ubuntuforums.org/showthread.php?t=1411973](http://ubuntuforums.org/showthread.php?t=1411973)

I was trying to help two separate people with nvidia issues (it seems) but I don't know too much about it. We tried bunch of things and nothing seems to help. :(
I will take a look and see if I may be of help.

---

### Post by RRF2525 on 2010-02-26
Thanks for the input all...I've been busy with development work on other projects so no time to work on my desktop.  Thankfully my laptop works out-of-the-box with 9.10 (w/16:10 ratio aka 1680x1050) so I've been using that.  

Will be at a Linux forum all day tomorrow so give me a few days to get back to this!  Sorry I can't give you input immediately but THANK YOU FOR YOUR IDEAS AND INPUT!!!

More soon...

---

