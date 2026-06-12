---
title: "nvidia nsanity"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by jerryphx on 2011-05-31
Hi, this is my first post, and of course, it is in desperation.

I am installing 11.04 on a Gigabyte E7AUM-DS2H with an onboard GeForce9400. I'm trying to turn this into an XBMC htpc. I'm not using xwindows or anything like that. going straight to console for now.

I'm experiencing the GRUB Black/Blank screen. I've read the sticky, searched for 2 days, now looking for any help from the community. I know this is a COMMON problem, but I just don't know what else to try...

1. I've changed the kernel boot options, i.e. nomodeset
2. I've toggled the GRUB_GFXMODE=640x680 line
3. I've remembered GRUB-UPDATE
4. I can get into GRUB menu using SHIFT at bootup, messing around with settings and CLI there
5. I started with default nvidia drivers (not good), and then installed nvidia-current - that works better.
6. At the blank screen, I can hit ALT-F1 into console/tty fine.
7. If I use nosplash --verbose, I get a long wait with a blank screen, then the last bits of the bootup log and the login prompt.
8. And stuff I've forgotten I've done....

Now what I really can't understand is that I have XBMC installed AND working beautifully. I can set XBMC to autorun with no trouble at all. It's just the period between bios and XBMC that it all goes dark. When I quit XBMC, I get a blinking cursor, which I can F1 to the console. What is it with GRUB??? What am I missing? Why is this so difficult? I COULD live with it, but its just not right, and I want to get it right.

Any ideas???

Thanks,
Jerry

---

### Post by tommcd on 2011-06-01
Have you installed the nvidia driver for your card?
To do this from the terminal or the ALT + F2 tty (since you seem to be comfortable using the terminal from your post, and good for for learning to use the terminal btw!) do this:
```

sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings mesa-utils
sudo reboot

```
Then after Ubuntu reboots, run:
```
sudo nvidia-xconfig
```
to configure the nvidia driver.
Write back if you need more help.
EDIT: I just saw that you have tried nvidia-current. Have you configured nvidia-current as I posted?
Does Ubuntu run ok from the live CD? This may be a problem with XBMC and not Ubuntu.

And welcome to the Ubuntu forums!

---

### Post by jerryphx on 2011-06-01
Thanks for the reply. I just had a chance to go through your suggestions.

> **tommcd said:**
> Have you installed the nvidia driver for your card?
```

sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings mesa-utils
sudo reboot

```
Then after Ubuntu reboots, run:
```
sudo nvidia-xconfig
```
I just looked, and the settings and utils were installed already, event though I didn't explicitly install. They are current.

I had not run nvidia-config. However, I did as you instructed and it has made no difference

> Does Ubuntu run ok from the live CD?
Haven't tried - will attempt.

EDIT: The live CD seems to work fine. I see all the splash screens, everything boots fine, there is never a period with a blank screen. It eventually lands at the menu.

I'm using the instructions [here]("http://ubuntuforums.org/showpost.php?p=10740097&postcount=3"), but I can't get to the GRUB menu by hitting ESC.  ESC has no effect, so I'm stuck there...

> This may be a problem with XBMC and not Ubuntu.

I'm not sure about that. This problem was occurring before I even attempted to install the XBMC packages. The blank screen has been there since the very beginning.


> And welcome to the Ubuntu forums!
Thank you for your reply!

---

### Post by tommcd on 2011-06-02
> **jerryphx said:**
> 
EDIT: The live CD seems to work fine. I see all the splash screens, everything boots fine, there is never a period with a blank screen. It eventually lands at the menu.

If the live CD runs ok then there must be some problem with your installation. If it were me I would try reinstalling Ubuntu. Then verify that you can boot with the default nouveau driver. If not, then boot with nomodeset according to that link you posted. Then install the nvidia driver. then reboot.
Sorry I can't think of anything else to try. Installing the nvidia driver usually fixes this problem.

---

### Post by jerryphx on 2011-06-02
UPDATE:

So the only way I can get the bootup graphics to work even close to right is using the following grub line:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" or "nosplash nomodeset"
```

However, I still get a blank screen up to the moment that the login shows. OTOH, with splash flag set, I will get a blank screen until I F1 into tty. 

Now I can adjust the resolution using 

```
GRUB_GFXMODE=1600x1200 (the native resolution)
```

What I find odd though is that in Xorg.0.log, I can see that the nvidia driver identifies the monitor and determines the screen size to be 1600x1200, BUT unless I manually set it in Grub, I get LOW res.

If this were a stand alone desktop, I might be ok with hard coding. But this will/may be an HTPC, so it should recognize what it is connected to. 

Where is this falling down?

---

### Post by jerryphx on 2011-06-02
Thanks for your help.

> **tommcd said:**
>  If it were me I would try reinstalling Ubuntu. 

This is my second shot. Third seems inevitable. I might try the CD instead of MiniCD.

> 
Then verify that you can boot with the default nouveau driver. If not, then boot with nomodeset according to that link you posted. Then install the nvidia driver. then reboot.

The nouveau driver does not work. I get an ugly mess on the screen.

> 
Sorry I can't think of anything else to try. Installing the nvidia driver usually fixes this problem.

Well thanks for the effort. Very kind of you for trying.

---

### Post by drdos2006 on 2011-06-02
Hee is how I fixed my problem.


Switch off machine, remove nvidia card .....nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
Boot with vga monitor on onboard vga output
Remove : sudo rm /usr/lib/extra-modules/nvidia.so
Shutdown, reinstall video card, re-install nvidia driver

regards

---

