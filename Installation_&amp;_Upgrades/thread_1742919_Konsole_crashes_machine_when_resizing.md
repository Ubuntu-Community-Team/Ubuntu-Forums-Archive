---
title: "Konsole crashes machine when resizing"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by carlbeech on 2011-04-29
Hi,

I've just finished installing ubuntu, with kubuntu desktop - 11.04, on an ASUS X59GL with Nvidia chipset, and used the NVIDIA 3d drivers.

All has gone fine, video, sound and wifi working (ok after a bit of tweaking as normal), however, I've found that if I resize the Konsole application, I get lots of flickering and garbage on screen - like the GPU can't keep up with the screen refreshes. After a couple of seconds the entire machine locks up...

I'd say I've got a video problem, however, it seems that Konsole is the only app that does this - the normal GUI apps appear to work fine...? I've turned off desktop effects under KDE (e.g. translucency), but it doesn't seem to make much difference...

The terminal emulator app under gnome works fine.

Anyone else seen this?

Thanks

Carl

---

### Post by schnelle on 2011-04-29
It is nvidia driver bug. Everything works fine here on ati with catalyst. 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632)

---

### Post by User55 on 2011-04-29
> **carlbeech said:**
> Hi,

I've just finished installing ubuntu, with kubuntu desktop - 11.04, on an ASUS X59GL with Nvidia chipset, and used the NVIDIA 3d drivers.

All has gone fine, video, sound and wifi working (ok after a bit of tweaking as normal), however, I've found that if I resize the Konsole application, I get lots of flickering and garbage on screen - like the GPU can't keep up with the screen refreshes. After a couple of seconds the entire machine locks up...

I'd say I've got a video problem, however, it seems that Konsole is the only app that does this - the normal GUI apps appear to work fine...? I've turned off desktop effects under KDE (e.g. translucency), but it doesn't seem to make much difference...

The terminal emulator app under gnome works fine.

Anyone else seen this?

Thanks

Carl


Yes, same on my computer using proprietary NVIDIA driver. :-(

I will replace Kubuntu with Ubuntu/Unity now...

---

### Post by User55 on 2011-04-29
You can use Version 173 of NVIDIA drivers. This version is stable but resizing is very slow.

---

### Post by ep_ on 2011-05-03
Kubuntu 11.04 on AMD 64 here.  I experience the crash as well.  Ironically, when it occurs, it's often set off by resizing the konsole application.  It's not consistent but when it happens it's a hard crash.  Everything freezes, leaving a frozen 'resize' mouse cursor.  Have to reboot via the reset button. It seems pretty severe.

As far as I can tell there's nothing amiss in any of the system kernel logs.  Hence, I've reverted to version 173 of the Nvidia drivers using the System | Additional Drivers applet, simply selecting the 173 choice, clicking OKAY and rebooting.

Not sure if this is a good way to change drivers.  The system appears clunky now, even typing this message on Kate.  I'd like to help trace/debug this but I'm rather a noob. Anything I can do?

How do I know when I should try "reinstalling" or revert back to the latest driver? Man, I was really digging the new release till this started happening.

---

### Post by ep_ on 2011-05-04
Another possible fix: Turn off desktop effects?   Seems to solve the problem but I've only tested for a day or so.  Can't force the crash.

---

### Post by Mr.Goose on 2011-05-05
It's a bug with the NVIDIA driver. Folks having problems with this might wish to click the "This bug affects me" link at the top of the bug report page:-
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632)

FWIW, this bug was first reported on the NVIDIA forums over a month ago. In fact the NVIDIA forums are littered with threads detailing issues with the latest NVIDIA driver and Ubuntu 11.04.

[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

However, both  the NVIDIA and the Ubuntu development teams seem astonishingly quiet regarding these issues. Sadly, I suspect the only way we'll get this fixed is if enough people moan about it. :(

Best wishes, G

---

### Post by Little Jawa on 2011-06-15
Seems we're getting out of it : 
 [http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html)

> Fixed a bug that caused freezes and crashes when resizing windows in KDE 4 with desktop effects enabled using X.Org X server version 1.10 or later.

 Now we "just" need to wait for it to come to the repositories.
 Unless you can't wait anymore and want to grab it there ? :-)

---

### Post by lemon_pulp on 2011-08-03
The 09.07 driver didn't work for me.  I folloed directions for the 09.04 driver here ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632/comments/107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632/comments/107)) and that seemed to fix things.

---

### Post by ankspo71 on 2011-08-04
It was doing it to me too. Konsole is my most frequently used app so it drove me nuts. Clicking on the maximize button was giving me mega screen distortion too. I'm testing Kubuntu 11.10 since a few days ago though, so I won't be able to follow the progress.

---

### Post by ankspo71 on 2011-08-17
After using more terminals it seems that the only two that I have found that are uneffected by the resizing bug is "Yakuake", and the terminal that is built inside Dolphin; Dolphin Menu -> View -> Panels -> Terminal. If you right click on the toolbar in Dolphin and choose "configure toolbars", you can add a shortcut to "Terminal" to make it easier to toggle on and off. This is what I am using now.

---

### Post by z_mikowski on 2011-09-12
Per [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632/comments/117](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/760632/comments/117) (and 118), this worked for me:

I have confirmed that downloading the 275.09.07 driver from NVIDIA fixes the freeze, which only recently became problematic for me.

1. Download 275.09.07 driver (64 bit) from [http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html)
2. Switch to a virtual terminal
<Ctrl-Alt-F1> and login
3. Shutdown X:
sudo stop kdm

4. Install new driver
cd ~/Downloads
chmod +x NVIDIA-Linux-x86_64-275.09.07.run
./NVIDIA-Linux-x86_64-275.09.07.run
# When notified that preinstall script failed, agree to proceed anyway

5. Reboot

This is the most trusted near-term solution, and /should/ be fairly clean. When the repo gets 275.xx.xx, it should overwrite this installation.

---

