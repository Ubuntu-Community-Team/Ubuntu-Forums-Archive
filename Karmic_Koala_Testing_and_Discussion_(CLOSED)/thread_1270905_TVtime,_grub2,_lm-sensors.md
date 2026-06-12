---
title: "TVtime, grub2, lm-sensors"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ppjose on 2009-09-20
hi (sorry for my english)

 I have karmic updated daily 

1) and use tvtime but I have no sound, in other applications I have sound

2) at system startup grub2 says error file not found

3) I followed this tutorial ( [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) ) at 9.04 and all ok but now lm-sensors not detect the same sensors (no voltage, not rpm, not mb temp ...), the chipset on my motherboard is an nForce4 (AMD Athlon 3500 +) 

 
> 

Driver `w83627hf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627THF/THG Super IO Sensors' (confidence: 9)

Driver `k8temp' (should be inserted):
  Detects correctly:
  * Chip `AMD K8 thermal sensors' (confidence: 9)



any help?  thanks

---

### Post by forumache on 2009-09-21
> **ppjose said:**
> 
3) I followed this tutorial ( [http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780) ) at 9.04 and all ok but now lm-sensors not detect the same sensors (no voltage, not rpm, not mb temp ...), the chipset on my motherboard is an nForce4 (AMD Athlon 3500 +) 


There is a problem with some sensor modules which don't load as there is a conflict. Add to your kernel line in grub (for testing purposes)

acpi_enforce_resources=lax

Then Google about it to see what it does. If it works for it, add it to the grub configuration file. This way, whenever you update kernel, the "acpi..." thing will be added automatically to kernel line in grub.

---

### Post by Gourgi on 2009-09-21
> **ppjose said:**
> 
1) i use tvtime but I have no sound, in other applications I have sound

if you connect the *audio out* from your tv-tuner to *line-in* of your audio card (or similar setup) try ```
alsamixer
``` and enable _everything_ including capture connectors (line-in,mic...) and see if that works. After that disable what you don't need from ```
alsamixer
``` and (optionally) set ```
gstreamer-properties
``` at the audio tab *default input* to _alsa_ (or _pulseaudio_ and choose the apropriate **input** for your audio card from ```
gnome-volume-control
```)
this is my current setup with my tuner and tvtime. i hope it helps
> **ppjose said:**
> hi (sorry for my english)
2) at system startup grub2 says error file not found

same here :)

---

### Post by ppjose on 2009-09-21
hi, 

 thank you very much for responding. 

@**forumache** & @**Gourgi**  I will test it tonight ;)

the grub2 error I hope to fix it with an update....

greetings

---

### Post by ppjose on 2009-09-21
hi  

 I bring news  :)

**Gourgi** --  I have reviewed the options you told me, but I only have sound in tvtime if I throw the test in gstreamer-propierties :confused:

**forumache** -- lm-sensors working fine now!

I read a little google but not clear to me ... 

 is safe to change the value of acpi_enforce_resources? There are other solutions?

---

### Post by forumache on 2009-09-21
> **ppjose said:**
> 

**forumache** -- lm-sensors working fine now!

I read a little google but not clear to me ... 

 is safe to change the value of acpi_enforce_resources? There are other solutions?

Seems like previously the acpi stuff didn't check for something and now (by a change in kernel) it is not so forgiving anymore...

But, because it was "lax" before and my motherboard did not burn (in more than 4 year of using lm-sensors on it), I guess it is safe *for me* to force acpi to continue to be "lax".

See here: [http://patchwork.kernel.org/patch/44754/](http://patchwork.kernel.org/patch/44754/)

So, it it used to work on your motherboard, you can put the "lax" line, if it is a non-tested computer, WARNING, do it at your own risk.

---

### Post by ppjose on 2009-09-22
> **ppjose said:**
> 

**Gourgi** --  I have reviewed the options you told me, but I only have sound in tvtime if I throw the test in gstreamer-propierties :confused:



up!

---

