---
title: "nVidia still broken here"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by joepotter on 2008-10-12
I have used Ubuntu since the first release, and have run the development branch on and off ever since. I realize that the development branch is subject to various problems.

I also am beginning to suspect that Intrepid will be released and I will not be able to use it. I require nVidia for my on-board GeForce 6100 (rev A) and it has never worked under Intrepid.

I have a fresh install of the just released Beta all updated to October 11, and I see three choices. All three drivers fail. I have tried 64 bit as well as 32 bit just to make sure. 

Can anyone shed any light on this at all? Good news, or bad news, I just want to know the status and what the future might bring since I just can not afford to change out the hardware to something that works at this time.

---

### Post by int on 2008-10-12
the driver works well for my nvidia 7700.

32bits and 64bits.

---

### Post by The Cokeaholics on 2008-10-12
Have you tried Envy to set up the NVIDIA-driver?
```

ubuntu:sudo apt-get install envyng-gtk
kubuntu: sudo apt-get install envyng-qt
sudo envyng -t
```

See details on [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by joepotter on 2008-10-12
> **The Cokeaholics said:**
> Have you tried Envy to set up the NVIDIA-driver?
```

ubuntu:sudo apt-get install envyng-gtk
kubuntu: sudo apt-get install envyng-qt
sudo envyng -t
```

See details on [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

I tried this to no avail. 

The 177.80 and 173.14.12 drivers load but give the "black screen of death" while the 96.42.05 driver will fail to load period.

This was all in 64 bit but looks just like months of testing went in 32 bit. I guess I'll put 32 back on one more time and then just give up on Intrepid.

I can run nvidia in any other distro; just not Ubuntu Intrepid. Well, I do not know about Sid as I have not tried that lately.

---

### Post by wgrant on 2008-10-12
> **joepotter said:**
> I tried this to no avail. 

The 177.80 and 173.14.12 drivers load but give the "black screen of death" while the 96.42.05 driver will fail to load period.

This was all in 64 bit but looks just like months of testing went in 32 bit. I guess I'll put 32 back on one more time and then just give up on Intrepid.

I can run nvidia in any other distro; just not Ubuntu Intrepid. Well, I do not know about Sid as I have not tried that lately.

Which version of the driver do you normally use? 96 needs to be updated by nvidia before it can be used on Intrepid.

---

### Post by joepotter on 2008-10-12
> **int said:**
> the driver works well for my nvidia 7700.

32bits and 64bits.

What part of broken here with the Geforce 6100 on-board chip was I not clear about?

Or, are you offering to give me that board?

---

### Post by klamari on 2008-10-12
Hi there

some bad news from my side, trying to get a Nvidia Geforce 6100/7600GS working under Intrepid since two days, 32Bit, 64Bit, various drivers, manual driver install, Jockey... all not working,
Nothing found with Google, only people having similar problems with Nvidia...
I started using Kubuntu after the problems with binary issues with Opensuse became more and more but now it looks I will stay with 8.04 for a while...

Greetings

martin

---

### Post by joepotter on 2008-10-12
> **klamari said:**
> Hi there

some bad news from my side, trying to get a Nvidia Geforce 6100/7600GS working under Intrepid since two days, 32Bit, 64Bit, various drivers, manual driver install, Jockey... all not working,
Nothing found with Google, only people having similar problems with Nvidia...
I started using Kubuntu after the problems with binary issues with Opensuse became more and more but now it looks I will stay with 8.04 for a while...

Greetings

martin

Please add to the bug;
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/282214)

so that we might get some developer to notice it.

Thanks in advance.

---

### Post by joepotter on 2008-10-12
> **wgrant said:**
> Which version of the driver do you normally use? 96 needs to be updated by nvidia before it can be used on Intrepid.

I have used 173 in other distros mostly; but 177 has my card on the list of cards supported. Both drivers yield only a black screen when they load in Intrepid.

I have used 96 in the past, but it is for cards older than mine if I understand the situation correctly. However, any driver that would work would be good news to my ears.

That said, I still do not see why I can not use 177 in Intrepid since the GeForce 6xxx series is listed as working with it.

---

### Post by nanog on 2008-10-12
Joepotter, Does the nv driver not work? You are limited to gnome-based compositing -- but better than nothing.

---

### Post by joepotter on 2008-10-12
> **nanog said:**
> Joepotter, Does the nv driver not work? You are limited to gnome-based compositing -- but better than nothing.

The nv driver works here but only gives 800x600 resolution and that is not workable. The vesa driver works just fine and that is what I use when I test Intrepid since no nVidia driver has ever worked. 

I suppose that I could get used to the idea that I must use "vesa" if it were not for the fact that I can get nVidia with the latest kernels in Arch, Zenwalk, Debian Lenny, and with Ubuntu Hardy. (well, I use Mint most of the time, but that is mostly just Hardy)

---

