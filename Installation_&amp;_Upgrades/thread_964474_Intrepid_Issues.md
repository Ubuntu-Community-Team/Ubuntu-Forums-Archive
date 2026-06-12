---
title: "Intrepid Issues"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by belfasttim on 2008-10-30
Hi all--

I installed Intrepid, after playing with the beta for a week or so--

A couple issues:

1) I can't seem to get my nvidia settings to "stick" even after starting the nvidia manager (using sudo) from command line, configuring display settings and clicking "save x config file"-- each time I reboot the 2nd monitor is inactive. Pretty annoying.

2) similar problem with network manager and a static IP configuration. I want to run as a static IP machine with a custom DNS server on the local network-- even after getting it all working properly via the NM applet, nothing is saved and after reboot I'm back to DHCP.

Other than that, liking 8.1 very much.

Any help much appreciated.

---

### Post by Laibcoms on 2008-10-31
What I did was:
```

gksudo nvidia-settings

```

Setup, save config, and restarted.  Worked fine after that.

With the network settings, I'm not sure, I was able to setup my Static IP fine and it saved.

---

### Post by belfasttim on 2008-10-31
Thanks Laibcoms -- I tried that, just in case the gksudo was doing something different, but no luck. /etc/X11/xorg.conf was still plain vanilla.

Thanks

---

### Post by belfasttim on 2008-10-31
A little more info on the nvidia issue-- 

I tried running nvidia-settings from both the Alt-F2 window and a basic command line, using both sudo and gksudo, and I checked the file permissions on the xorg.conf file to make sure it was writeable.

Odd thing is that the nvidia settings manager closes immediately after you click save x settings-- syslog has this entry--

Oct 31 10:12:24 ub-desktop kernel: [49194.114821] nvidia-settings[22385]: segfault at 10 ip 0000000000463b1c sp 00007fff9a0c0950 error 4 in nvidia-settings[400000+9e000]

Any thoughts on this?

Thanks

---

### Post by belfasttim on 2008-10-31
Ok looks like it may have been a known bug -- this thread ([http://ubuntuforums.org/showthread.php?p=6072222](http://ubuntuforums.org/showthread.php?p=6072222)) helped me out. 

What I ended up doing was sudo nvidia-xconfig (which gave some warnings and ended up just rewriting the same old xorg.conf) then sudo nvidia-settings.

This last time the save x config button worked as intended and I can verify that the settings are saved to the xorg.conf file.

Now I just need to figure out how to get a static IP to stay!

---

### Post by potatoehead64 on 2008-10-31
I've got the same network problems. I'm not sure how to set up the network settings to connect to my BT Home hub. It all seemed to work automatically on the last 2 distributions. How do you do that?

Cheers

Marty

---

### Post by taekr on 2008-10-31
> **belfasttim said:**
> Hi all--

I installed Intrepid, after playing with the beta for a week or so--

A couple issues:

1) I can't seem to get my nvidia settings to "stick" even after starting the nvidia manager (using sudo) from command line, configuring display settings and clicking "save x config file"-- each time I reboot the 2nd monitor is inactive. Pretty annoying.

2) similar problem with network manager and a static IP configuration. I want to run as a static IP machine with a custom DNS server on the local network-- even after getting it all working properly via the NM applet, nothing is saved and after reboot I'm back to DHCP.

Other than that, liking 8.1 very much.

Any help much appreciated.

I have the same problem. Can't save Nvidia setting.

---

