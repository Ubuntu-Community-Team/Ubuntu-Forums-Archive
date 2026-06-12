---
title: "Video card drivers?"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by gabe2 on 2013-08-12
OK, I got my Ubuntu 12.04 up and running, updates installed, and made a couple of simple tweaks (mouse speed, etc.). Now my next step is to install drivers for my video cards, and I did as instructed by going to the "Additional Drivers" app, only it comes up blank. Does this mean my video cards aren't supported (yet)? I use 2 EVGA 460 GTX in SLI mode. Actually, does Ubuntu recognize SLI? I went to NVIDIA's page and they do have drivers listed (Linux or FreeBSD? And x64 is for the 64-bit systems, correct? That's what I have). I read in a lot of places, however, that I should very much avoid using NVIDIA's download. What do I do here?

Thanks!

---

### Post by papibe on 2013-08-12
Hi gabe2.

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by gabe2 on 2013-08-12
I feel a little dumb asking this, but where do I input that command?

---

### Post by papibe on 2013-08-12
Open a terminal, and paste the command above, then paste its output on another post :)

Regards.

---

### Post by gabe2 on 2013-08-12
All right, gotta switch over to Ubuntu...back in 10

---

### Post by gabe2 on 2013-08-12
OK, here's what it showed:

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1362]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1362]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF104 [GeForce GTX 460] [10de:0e22] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1362]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1362]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

---

### Post by papibe on 2013-08-12
Thanks.
Somehow your are actually using the Nvidia proprietary driver.

Just make sure to enable sli by running either:
```
sudo nvidia-xconfig --sli=AFR
```
or
```
sudo nvidia-xconfig --sli=SFR
```
depending on the rendering mode you prefer.

Then restart your computer.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by gabe2 on 2013-08-12
What's the difference between the two modes? Also, if I have NVIDIA drivers installed, why can't I select the correct resolution for my monitor? It should be 1920 x 1200 and I only have 1024 x 768 and 800 x 600 to choose from.

---

### Post by papibe on 2013-08-12
Are you using 'Nvidia X Server Settings' to set the resolution?

(that replaces the functionality of 'Displays' when using the Nvidia driver).

Let us know how it goes.
Regards.

---

### Post by gabe2 on 2013-08-12
Didn't know that was there, but while there are additional resolutions available, it still only appears to max out at 1024x768, I do not see 1920x1200 anywhere, unfortunately. I guess I need to go into the X Config file and manually enter it there?

---

### Post by gabe2 on 2013-08-12
I'm still having no luck whatsoever trying to change the resolution. I've been looking at all kinds of different fixes and none of them appear to work (or maybe I'm not doing it right, I don't know). Also, I can't seem to adjust the brightness of the screen because my slider is gone for some reason. Is there a fix for that as well?

Please help, I'm quite eager to learn about this OS and the potential troubleshooting I gotta do. This is sort of research for building my grandmother a simple and user-friendly computer that isn't tempermental. The resolution and slider are really the two big remaining items that I need to fix here, I'm so CLOSE!

For the record, here's what xrandr says:
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected 1024x768+0+0 (normal left inverted right x axis y axis) 520mm x 330mm
   1024x768       75.0*+   70.1     60.0  
   800x600        75.0     72.2     60.3  
   640x480        75.0     72.8     59.9  
   640x350        70.1  
HDMI-0 connected (normal left inverted right x axis y axis)
   1024x768       75.0 +   70.1     60.0  
   800x600        75.0     72.2     60.3  
   720x480        59.9  
   640x480        75.0     72.8     59.9  
DVI-I-3 disconnected (normal left inverted right x axis y axis)

---

### Post by papibe on 2013-08-12
What kind of cable are you using to connect the monitor? Is a VGA, DVI or HDMI?

Also, could you paste the content of this file:
```
/var/log/Xorg.0.log
```
Please paste it here: [paste.ubuntu.com]("http://paste.ubuntu.com/"), and then post back the link to it.

Regards.

---

### Post by gabe2 on 2013-08-12
DVI

I tried entering that line code in the terminal, it told me that permission is denied?

---

### Post by gabe2 on 2013-08-12
Whoa! I just noticed something interesting. On a lark, I switched over to the Guest Session and the resolution there is CORRECT!

***EDIT* I copied & pasted the contents of the xorg.conf file from the Guest Session (after saving using NVIDIA X Server) to my account, that appears to have fixed the problem, now I have the correct resolution.**

---

