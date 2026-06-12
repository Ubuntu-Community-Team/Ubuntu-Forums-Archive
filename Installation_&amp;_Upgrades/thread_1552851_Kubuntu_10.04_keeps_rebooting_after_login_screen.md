---
title: "Kubuntu 10.04 keeps rebooting after login screen"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by bhram on 2010-08-14
Hi,

I earlier faced a [problem]("http://ubuntuforums.org/showthread.php?t=1548319"). However, I anyways went for reinstalling kubuntu 10.04. The installation went fine. It asked to reboot at the end, which I did. After the reboot, it gives me the login screen. After filling up the details there it again shows me the same login screen. This goes on forever. Please let me know, how can I solve this issue.

---

### Post by Fxy on 2010-08-14
Once you arrive at the logon screen press 

```
ctrl+alt+f2
```

That should boot you into a terminal session...

...Once the session has loaded, you can log yourself in & then type

```
startx
```

Upon typing that code your desktop should hopefully load...

...If that fails to load your desktop, then you can come back here & post any errors you receive or anything strange that happens;)

---

### Post by bhram on 2010-08-14
Hi Fxy, 

Thanks. I already tried this. First, the ctrl+alt+f1/f2/f3... doesn't work for me. Instead what I did is that I booted in recovery mode. I chose to drop into root shell and tried startx command. It again gives me the same login screen and same behavior (some times it even gets stuck at the screen where it shows loading various things viz. hard disk, tools etc.). 

What I now think is that it could be related to the less amount of swap available to kde. I am now trying to find out that how can I increase the size of swap. Currently it is 978MB. I would try to increase it to atleast 2GB. My RAM's size is 1GB. Do you have any idea how can I increase the size of the swap partition (may be by using installation cd again).

Thanks in advance...!

---

### Post by bhram on 2010-08-15
I increased the swap space to 2GB by reinstalling Kubuntu 10.04. The problem still persists. However, somehow (explained below) I could login and started working in Kubuntu now. The process is little painful though. 
    By trying out various trial and error, I could boot Kubuntu properly. As I explained earlier the boot sequence was never completing and keeps retrying endlessly. While it is doing that I could put the live CD in and arbitrarily did two things. One, pressed Ctrl-Alt-Del many times and secondly, sometimes got the CD out and in again few times. This is strange but somehow works :confused:.
    It would be great if someone could relate the strange solution to the actual problem and guess what could be done to correct things here.

---

### Post by bhram on 2010-08-18
During the arbitrary boot that happened with the mechanism that I described earlier, I did an upgrade also over internet. 
```
sudo apt-get upgrade
```
It did upgrade few things, however, the problem still remains. I still see the boot screen of Kubuntu coming up partially (in all cases before it never shows actual kubuntu icon) and restarting again and again. For time being, the live CD works as boot CD.. :mad:
   Looks like nobody encountered the same problem ever before.

---

### Post by brownslink on 2010-09-06
I have the same problem.  I tried a bunch of video cards that I had laying around and found one that let's me startx once I am logged-in.

---

