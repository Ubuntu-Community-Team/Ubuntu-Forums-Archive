---
title: "[SOLVED] Disable synaptics touchpad scrolling Intrepid"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by derrick81787 on 2008-10-16
Hello everyone,

I just upgraded from Hardy to the Intrepid beta, and I'm having some problems with my touchpad.  In Hardy, I had my touchpad configured to where tapping was disabled and scrolling worked just fine.  When I first upgraded to Intrepid, tapping was still disabled, but my scrolling quit working.  I looked around for a while and found out that Xorg has had a bunch of major changes, and that I probably shouldn't be using my xorg.conf file from Hardy.  I replaced it with the default xorg.conf file from Intrepid, and my scrolling started working, but now tapping isn't disabled.

In Hardy, I had added this to my xorg.conf:
```
MaxTapTime  "0"
```
and that caused tapping to be disabled.  However, I can't do that, now, because I don't even have an entry for my touchpad in my xorg.conf.

I've followed the directions at [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad) for enabling SHMConfig and using gsynaptics in Intrepid, but for some reason gsynaptics says that SHMConfig isn't on, even after restarting X and rebooting.

The only reason I can think of for it not working is because I'm not running default Ubuntu.  In Hardy, I installed the CLI version and built up from that with Openbox, etc.  I figure that maybe I'm missing something that causes this not to work.

Does anyone have any idea what I can do to disable tapping on my touchpad?  With tapping enabled, I screw up my typing and randomly click things all the time, so I'd really appreciate any help you can offer.

Thanks,
Derrick

***** Edit:**
The relevant section on the wiki has changed drastically since I first posted this, so for all I know, the directions might work now.

---

### Post by derrick81787 on 2008-10-17
Bump.

Isn't there anyone who's running Intrepid that has a touchpad with tapping disabled that can also scroll?

---

### Post by Scheater5 on 2008-10-19
I have the same problem with getting SHMC to work.  I have no desire to turn off tapping, but I want to run gsynaptics for circular scrolling.  I followed the instructions in the wiki to enable SHMC, rebooted and there was a noticable change in the sensitivity of my touchpad, and then when I pulled up firefox noticed that scrolling no longer works.  Yet, gsynaptics still won't open.

Edit: Latest round of updates, including updated X, and scrolling automagically worked - gsynaptics still doesn't.

---

### Post by wgrant on 2008-10-19
Make sure you put the SHMConfig option inside the part of the FDI file that corresponds to your touchpad - it's quite possible that you have an ALPS one, so the Synaptics product name will not match.

As for turning off tapping, why not use System->Preferences->Mouse->Touchpad? There's a perfectly good option there.

Also, while there isn't yet a GUI for it, you can [use xinput on the commandline](https://wiki.ubuntu.com/X/Config#Dynamic Input Configuration with xinput) to set up circular scrolling without having SHMConfig on. You'll need to set the two properties relating to circular scrolling. The one to enable it is obvious, but setting the starting region is less so - check the synaptics manpage for values.

You can then run xinput on login to set those, without the horrible security risk of SHMConfig.

I should have a nice GUI built in for Jaunty.

---

### Post by derrick81787 on 2008-10-19
> **wgrant said:**
> Make sure you put the SHMConfig option inside the part of the FDI file that corresponds to your touchpad - it's quite possible that you have an ALPS one, so the Synaptics product name will not match.

As for turning off tapping, why not use System->Preferences->Mouse->Touchpad? There's a perfectly good option there.

Also, while there isn't yet a GUI for it, you can [use xinput on the commandline](https://wiki.ubuntu.com/X/Config#Dynamic Input Configuration with xinput) to set up circular scrolling without having SHMConfig on. You'll need to set the two properties relating to circular scrolling. The one to enable it is obvious, but setting the starting region is less so - check the synaptics manpage for values.

You can then run xinput on login to set those, without the horrible security risk of SHMConfig.

I should have a nice GUI built in for Jaunty.

Are you the one who writes that GUI?  I'm not using it because I'm using OpenBox, and so it's not installed.  What's the package name, and do you know whether or not it has a lot of GNOME dependencies?

After posting this thread, I ended up trying to use xinput, but there was a bug or something that caused it to segfault.  I posted about that in this thread [http://ubuntuforums.org/showthread.php?t=950797](http://ubuntuforums.org/showthread.php?t=950797) but after the update today, everything works.  I just now got xinput to work, and so my tapping successfully is disabled.

I do like the mouse GUI.  When I used GNOME, that was how I did it, but after moving  to OpenBox, I found it easier to just set MaxTapTime equal to 0 in my xorg.conf.  I'm a senior in CS right now, and if your GUI does have a bunch of GNOME dependencies, I wouldn't mind looking at it and writing a stripped down GTK-only version, assuming I can figure out how it works, haha.

Anyway, thanks for the help.

- Derrick

---

### Post by derrick81787 on 2008-10-19
By the way, if anyone is having a similar problem, I solved it by having this command run at startup:

```
xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Synaptics Tap Time" 32 0

```

---

### Post by wgrant on 2008-10-19
The GUI existed beforehand using some nasty hacks in the synaptics driver, but I rewrote it during Intrepid to eliminate the dependency on those hacks. It is gnome-mouse-properties from gnome-control-center, but that just sets gconf keys that gnome-settings-daemon looks and and configures the devices with.

It basically just automates the somewhat painful manual use of xinput (which I finally got to work on amd64. That took a while).

Since you seem to have an ALPS touchpad, you should be able to set things in the ALPS section of the FDI file, if you need to.

---

### Post by jbg7474 on 2008-10-23
William:
2 questions:
1. When do changes in the fdi file take effect, on starting of X like xorg.conf?

2. Is there documentation anywhere for these files?  Since this is such a big change from the way settings were done before, there doesn't seem to be a lot of community support like there was for xorg.conf.

---

### Post by wgrant on 2008-10-24
> **jbg7474 said:**
> William:
2 questions:
1. When do changes in the fdi file take effect, on starting of X like xorg.conf?

2. Is there documentation anywhere for these files?  Since this is such a big change from the way settings were done before, there doesn't seem to be a lot of community support like there was for xorg.conf.

See [the X configuration documentation](https://wiki.ubuntu.com/X/Config#hal) for details. The fdi file's settings will be applied when the device is redetected - for a touchpad this can currently be easily achieved by restarting X or running 'sudo rmmod psmouse && sudo modprobe psmouse'.

---

### Post by jbg7474 on 2008-10-24
Thanks!  That's useful information.  This seems like the best way to get the same kind of configuration ability we had previously in xorg.conf.

---

