---
title: "upgraded from 12.04 to 13.04, display imaged distorted/not-readable"
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by coralreefer on 2013-08-26
I upgraded from 12.04 to 13.04 on a Dell Inspiron 8100 notebook with nvidia N17 graphics and it boots to a screen washed out with colors (nothing readable).  I am able to blindly type my password and then the screen colors change so I assume the GUI loads and I can get to terminal.  I believe that 13.04 is setting the screen resolution too high by default and the N17 can't handle it?  I can boot to low graphics mode and the screen is clear but the image only uses the center 2/3 of my display.  I do not see any 3rd party drivers loaded and have used terminal to force nvidia updates with no success.  I see many discussion about 13.04 booting to a black screen with nvidia but that is not my problem and none of those fixes work.  Any help?

---

### Post by Frogs Hair on 2013-08-26
Hello and Welcome

> have used terminal to force nvidia updates with no success. I don.t know what is meant by forced updates . If you were using a proprietary Nvidia driver prior to the upgrade it was removed as a result of the upgrade. One reason for this is the new kernel . You can install a driver via the terminal and I have a number of different options available . One thing you might try is installing the tested Nvidia driver from the terminal . 

```
sudo apt-get install nvidia-current
```

---

### Post by coralreefer on 2013-08-26
that is exactly what I tried already.  I am new to ubundu but from what I can tell when I boot in the low graphics mode and look at the "additional drivers" tab in the "software & updates" tool, there are no drives listed at all.

---

### Post by Frogs Hair on 2013-08-26
Perhaps you graphics chip/card  isn't supported on 13.04 . If you haven't already install updates. ```
sudo apt-get update && sudo apt-get upgrade 
```
Video Card/Chip Info : ```
lspci -v
``` Did you upgrade via 12.10 or simply add the 13.04 sources and upgrade directly ? Direct upgrades via the source list are not recommended  and basically a crap shoot.

---

### Post by coralreefer on 2013-08-26
I re-installed 12.04 to get back up and running.  I will use the above code in 12.04 to determine to get chip info but then where do I check to see if 13.04 supports my chip?  I upgraded to 12.10 first.

---

### Post by Frogs Hair on 2013-08-26
You can copy and paste the output of the command here . Use # symbol in the reply box tools to add code tags or submit at the link and past the url to the thread.   h[ttp://paste.ubuntu.com/]("http://paste.ubuntu.com/")

---

### Post by coralreefer on 2013-08-26
here is the video card ouput:

```
01:00.0 VGA compatible controller: NVIDIA Corporation NV17 [GeForce4 440 Go] (rev a3) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 00d4
    Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 11
    Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Memory at dff80000 (32-bit, prefetchable) [size=512K]
    Expansion ROM at d8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nouveau, nvidiafb, rivafb
```

---

### Post by coralreefer on 2013-08-26
Also I see no additional drivers availble when I search for driver and see the note that "no proprietary drivers are in use on this system".  How do I get the nvidia drivers?

---

### Post by Frogs Hair on 2013-08-27
I see you chip/card listed here. [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

The nvidia-173, is the only driver that supports older hardware and if it is not displayed in additional drivers you may be out of luck for running newer versions of Ubuntu. If 12.04 worked  you may want to stick with it until you can upgrade you graphics. Lubuntu is great on system resources , but I don't think it has any other Nvidia driver options than Ubuntu.

---

### Post by coralreefer on 2013-08-27
so after going back to 12.04 i decided to try installing updated nvidia via the below code and it again crashed my display
sudo apt-get install nvidia-current

i was able to get my display back by purging the nvidia and going back to nouveau

so now my question is can i dump the 13.04 video drivers and use the same nouveau default drivers that 12.04 uses to allow me to run 13.04 on my system???

---

### Post by Frogs Hair on 2013-08-28
I was running the 13.04 + compiz cube with nouveau, but with a newer Nvidia  graphics card that has dedicated graphics memory . I had problem waking from sleep(Unity only) so I went back to proprietary drivers. I would have been perfectly happy with  nouveau otherwise as it worked in the Gnome Shell and XFCE. Nouveau is the default driver and was installed during your first upgrade. If you choose try again use the following command for Unity support. 13.04 has a different version of Unity.

```
/usr/lib/nux/unity_support_test -p
```

---

