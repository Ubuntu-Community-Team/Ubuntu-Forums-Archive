---
title: "Stuck at 1400x1050 after 12.04 -&gt; 14.04 upgrade"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by duffymcdrew on 2016-02-16
I finally decided to upgrade an old desktop from 12.04 to 14.04. Its an AMD system with onboard radeon graphics...

```
$ lspci |grep VGA
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4250]
```

According to [this]("https://help.ubuntu.com/community/RadeonDriver#Fully_supported") it should be supported by 14.04, but prior to the upgrade I got the [Unity3D]("https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D") warning. I had no graphics issues at 12.04 and was running 1920x1080 (or 1680x1050). So despite the warning, I upgraded anyways, and of course, the graphics are now messed up. It doesn't seem to be recognizing the monitor (an Acer H233H connected via VGA). The Display settings labels it as a 'Built-in Display' and only gives me a resolution option of 1400x1050.  The upgrade was done while connected via a KVM switch, which perhaps had something to do with it?  I did try connecting the display directly and reboot, but still only gave 1400x1050.  I tried [this]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx") as well, but no luck (however this was also done over the KVM)

Any thoughts?

---

### Post by QIII on 2016-02-16
Hello!

Which point release of 12.04 were you running?  Did you have the proprietary driver installed?  Did you upgrade or do a fresh installation?

---

### Post by duffymcdrew on 2016-02-17
It was an upgrade. By "point release" do you mean 12.04.x? If so, I'm not sure, though I know I kept the packages up to date. I don't believe I had the fglrx drivers installed, though looking at my bash history, looks like I did a 'sudo apt-get purge fglrx*' after the upgrade, though I think thats when I first started troubleshooting this.  So I'm really not sure about the proprietary driver. Is there a upgrade log somewhere?

---

### Post by mörgæs on 2016-02-17
> **duffymcdrew said:**
> 
According to [this]("https://help.ubuntu.com/community/RadeonDriver#Fully_supported") it should be supported by 14.04

The link shows that your graphics processor is fully supported by the open source Radeon driver, which is installed by default. The drivers have improved a lot lately, among other things with less overheating (see further down on the page), and I suggest a fresh install of 15.10 in stead.

---

### Post by grahammechanical on 2016-02-17
A couple of things that I have noticed.

The screen displays utility does sometimes get the monitor label wrong. I am using a Sharp 24 inch digital TV as a monitor. And screen displays calls it a Sharp 7 inch. It does not seem to have a detrimental effect on the use of the monitor. And it is most like caused by inaccurate information in the digital display's EDID.

A VGA connection does limit the maximum screen resolution. I noticed this when I first purchased this digital TV and had to use a VGA connection because the TV did not have a DVI connector. But it did have HDMI connections and with that I am able to get the manufacturer's optimum resolution.

When using a proprietary video driver it is better to use the proprietary settings utility that comes with the driver then to use screen displays.

Some commands that give useful information about screen resolutions.

```
xrandr
```

these will need to be installed

```
lxrandr
arandr
```

Regards.

---

### Post by duffymcdrew on 2016-02-17
Yea I played with xrandr a bit to try and force 1680x1050, which took, but then I was unable to switch to it, I forget the specific error.  I also did try HDMI (when I was bypassing the KVM) and that didn't yield anything different either. In fact, it was worse over HDMI as it was still 1440x1050 but both letter and pillar boxed.

I installed those 2 packages, but the xrandr output is the same:

```
$ sudo xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1400 x 1050, current 1400 x 1050, maximum 1400 x 1050
default connected primary 1400x1050+0+0 0mm x 0mm
   1400x1050      77.0* 

```

Also, I just realized a typo in the title... as you can see I'm stuck at 1400x1050.

---

