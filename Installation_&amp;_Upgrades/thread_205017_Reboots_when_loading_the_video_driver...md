---
title: "Reboots when loading the video driver.."
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by shockme17 on 2006-06-27
I want to install ubuntu on my 800mhz computer with 384mb ram, and a nvidia geforce4 440, but i can't even get it to load.. every time i put the disk in, it starts to load, but then the last task i can see is trying to load the video driver, and then the machine turns off/reboots.. this also happened with older versions of ubuntu.. 

is there a simple fix to this?

thank you

---

### Post by AllenGG on 2006-06-27
Not nessarily a simple fix, but try a "live CD", either Knoppix or Ubuntu. The Live CD's seem to find the hardware, why ?
This will help you find the problem.

---

### Post by shockme17 on 2006-06-27
thank you, but the versions i've tried were live cds.

---

### Post by tseliot on 2006-06-28
Try the Safe Mode from the LiveCD (as soon as it boots)

---

### Post by shockme17 on 2006-06-28
i've tried safe mode, and i get an error saying that the x server failed to load, and i'm given the option to view the output to view the problem, but then a bunch of text shows up, followed by a series of bash prompts.. 

i know there is nothing wrong with the cd, because i've used it successfully on other computers.. 

are there any other suggesetions?

---

### Post by tseliot on 2006-06-28
Please follow these instructions:

1) you install Ubuntu using the **alternate installation** CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then use Method 1 of this guide and point 7 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by shockme17 on 2006-06-28
i'll try that, thanks for the tips

the thing that is weird though, is that the computer that does work has the pretty much the same video card - nvidia geforce4 440se with 128mb, as opposed to the computer which doesnt work, it has the nvidia geforce4 440 with 64mb.. 

very strange.

---

