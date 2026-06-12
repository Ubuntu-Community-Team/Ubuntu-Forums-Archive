---
title: "Lenovo s10e install and fixes."
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by nytek on 2010-02-01
For the record, I'm an avid Ubuntu user that loves to support open source. 

I wouldn't consider myself an expert on Linux but, I have a good amount of knowledge due to the fact of these lovely forums that the open source community provide. 

This is me trying to show my appreciation by posting my install instructions and fixes for my Lenovo s10e netbook running Ubuntu Karmic 9.10.

First of all, installed a fresh copy of Ubuntu 9.10.

Ethernet, bluetooth, webcam, and laptop function keys worked out of the box.

Microphone, SD slot and headphone jack didn't work correctly. 

Wireless worked, installed the restricted Broadcom STA wireless drivers. 

Instructions:

1. Install a fresh copy and do a full update when you get your system up and running. 

2. Install wireless driver from System ---> Restricted Drivers. (Broadcom STA)

3. Microphone was a little buggy at first, but I realized that I just needed to change the default in sound preferences to "Microphone 2". Skype works great with microphone and webcam. :D

4. SD card, I haven't found a fix for. But, if anybody has an ideas I'm more than happy to hear them. 

5. Headphone jack was a little tricky, but a simple fix; indeed. All you need to do is edit your "/etc/modprobe.d/alsa-base.conf" file and add the following line with your corresponding Audio card ID. 

a) Press alt-f2 and type: 

```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

b) Add the following line:  

```
options snd-hda-intel model=ID
```

Add your corresponding ID in the "ID" part of the code. 

c) If you don't know what yours is, Open up a terminal and type: 
```

aplay -l
```

You'll then get an output something like this:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #

```
Continue c) Where ALC883 or whatever your Device ID is the ID. Copy that into the code and you're good to go. Your speakers will silence when you plug in your headphones and vice versa. 

Mine looks like this:

```
options snd-hda-intel model=ALC269
```

d) I, Also, haven't messed with the multi-touch support with the touchpad. But, I don't doubt there is something floating out there about it. Again, if anybody has any expertise with this issue, please pass along the information.

I guess, that's pretty much it. If anybody has an question feel free to respond to this thread and I'll do my best to help you out. Happy netbooking!

---

### Post by Funzo22 on 2010-02-16
Thanks!!! I had to give up on moblin because there were no forum posts like this to make everything just work so easily!! Saved hours and hours of time spent on google.

---

### Post by nytek on 2010-02-17
You are very welcome!

---

### Post by alcide on 2010-03-05
thanks, ubuntu is a whole lot faster on this tiny machine, compared to upgrade thickened Windows xp

---

