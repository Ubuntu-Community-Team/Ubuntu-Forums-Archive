---
title: "i8kmon won't work"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bobterri on 2009-10-09
I have used i8kutils to control fanspeeds for my Dell Inspiron 6000 laptop since 7.10.  I've always been able to get it to work.  

It's not working in Karmic.  Has anyone had any luck with i8kutils with their Dell laptop using Karmic.

I know Karmic's just in beta, so I'm not expecting everything to work, but I was just wondering?  All in all, except for i8kutils, I'm very impressed with Karmic.

A couple of things:

I had to enable the [http://archive.canonical.com/ubuntu/Karmic](http://archive.canonical.com/ubuntu/Karmic) repository to install i8kutils.  

Also, I noticed that installing i8kutils automatically created /etc/init.d/i8kmon.  Before I had to create this myself.  

It seems that there is a new file named "/etc/defalut/i8kmon."  "Man i8kmon" isn't clear weather "/etc/default/i8kmon" is the same as the old "/etc/i8kmon" or a separate, new file.  

Anyone had any success yet with this in Karmic?

---

### Post by bobterri on 2009-10-09
Is there anyone using i8kutils on any variant?  Or is there a better way on Dell laptops to manage fanspeeds in Karmic?

---

### Post by bobterri on 2009-10-10
I'm wondering if this thread could be moved to another category?  Maybe Hardware and Laptops?  I don't want to double post.

Perhaps in another category I might get someone to look at this who can help.

---

### Post by wilee-nilee on 2009-10-10
I am using i8k via gkrellm; it works fine, and you don't have to set up a fan control folder gedit setup. If you remove all the setups you have used and install i8k gkrellm then follow 2 through 4 instructions in this link everything should work. Then just add gkrellm to the startup applications using gkrellm as the command it will be running on startup.  [http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

---

### Post by bobterri on 2009-10-11
OK.  I am using Gkrellm too, now.  Thanks, Wilee-Nilee.

I would rather use i8kmon but at least the fan cycles on and off now.  I've always been able to get i8kmon to work, but not this time around.  Maybe I'll try when Karmic is released.

In the mean-time, if anyone gets it working with i8kmon please drop me a line.

---

### Post by bobterri on 2009-10-13
One of the reasons I like i8kmon better is because you can set it up to work in the background.  No icon...no graph, etc.  Is there anyway to set up gkrellm to work this way?  I really don't want the interface on my desktop...just takes up too much real estate and I don't want it in the lower panel.  

And, of course, if anyone has gotten i8kmon to work in Karmic I would love to hear from you.

---

### Post by wilee-nilee on 2009-10-13
> **bobterri said:**
> One of the reasons I like i8kmon better is because you can set it up to work in the background.  No icon...no graph, etc.  Is there anyway to set up gkrellm to work this way?  I really don't want the interface on my desktop...just takes up too much real estate and I don't want it in the lower panel.  

And, of course, if anyone has gotten i8kmon to work in Karmic I would love to hear from you.

 You are using i8kmon look in synaptic and you have it installed inside of gkrellm. You can take it off the desk top or put the gui on another desktop, I also remove all the extra stuff like email, uptime, HD, network, Internet. Just open up the edit gui and mess around, it takes a bit of working with to realize that you have what your looking for and that it is highly customizable.

---

### Post by bobterri on 2009-10-13
Thanks wilee-nilee, but I don't quite understand what you mean.

Gkrellm is controlling my fans now and doing a good job of it.  I just want to run it invisibly, in the background like i8kmon if possible.

Did you mean to say I have i8kmon installed "instead of gkrellm?"  You said "inside of gkrellm."

Also, I believe i8kmon is part of the i8kutils installation.  

So, are you suggesting that I uninstall i8kutils?  

Also, it sounds like from what you say there is no real way to run gkrellm in the background, hidden like i8kmon.

Finding clear documentation for Gkrellm is a bit challenging.

---

### Post by wilee-nilee on 2009-10-13
> **bobterri said:**
> Thanks wilee-nilee, but I don't quite understand what you mean.

Gkrellm is controlling my fans now and doing a good job of it.  I just want to run it invisibly, in the background like i8kmon if possible.

Did you mean to say I have i8kmon installed &quot;instead of gkrellm?&quot;  You said &quot;inside of gkrellm.&quot;

Also, I believe i8kmon is part of the i8kutils installation.  

So, are you suggesting that I uninstall i8kutils?  

Also, it sounds like from what you say there is no real way to run gkrellm in the background, hidden like i8kmon.

Finding clear documentation for Gkrellm is a bit challenging.

  I am not sure of your install but there is a gkrellm-i8k they work together on a dell computer beautifully. If you look in synaptic search with gkrellm and I bet you have gkrellm-i8k installed that is what you want. You can customize that gui so just check out those options, you can change the listed readings, height, width, senors c/f, not in tray----etc. I think you have just gotten used to the way of doing it before which is fine but I think you will find that the gkrellm set up gives you much more options, it works as well as conky, and doesn't messs with the desktop icons like conky does. I don't know the answer to getting it to be invisble, but if that was what I was looking for I would just have it open on another desktop, and know I wasn't suggesting you remove i8k I was under the impression that you thought it wasn't using that in conjunction with gkrellm, which as I said I don't know how you have set it up.

---

### Post by bobterri on 2009-10-15
You're right!  Gkrellm-i8k is installed.  You're also right that I have gotten use to i8kmon.  Gkrellm works just fine, I just hate it when I can't get something to work right and the documentation is so foggy.  The man for i8kmon is really murky.  It's unclear now how to configure i8kmon to work.

It is my personal preference to have i8kmon controlling fanspeeds because it doesn't add something to the desktop or the panel on the bottom.  Yes, I know i can move to another desktop but I shouldn't have to do that, right?

---

### Post by psyke83 on 2009-10-15
You need to load the i8k kernel module. You can manually modprobe or add to /etc/modules.

---

### Post by wilee-nilee on 2009-10-15
> **bobterri said:**
> You're right!  Gkrellm-i8k is installed.  You're also right that I have gotten use to i8kmon.  Gkrellm works just fine, I just hate it when I can't get something to work right and the documentation is so foggy.  The man for i8kmon is really murky.  It's unclear now how to configure i8kmon to work.

It is my personal preference to have i8kmon controlling fanspeeds because it doesn't add something to the desktop or the panel on the bottom.  Yes, I know i can move to another desktop but I shouldn't have to do that, right?

 Hey glad you have it worked out except for the gui I personally like the gui; I run the fans, temp readout and cpu only so it is good for me. It looks like another post might have an answer that can help. I am a pseudo geek and will find the path of least resistance in general, for me the computer is a tool, I am an artist if I want subtle expression I will create it in my own realm.

---

### Post by bobterri on 2009-10-15
The joy of linux--you have it your way, I'll have it mine (that is if I could get it to work!!!)

psyke83 - I did this, just as I did on the previous installations...9.04...8.10....etc.

It just isn't working and as I said, the man for i8kmon is very unclear.

---

### Post by psyke83 on 2009-10-15
> **bobterri said:**
> The joy of linux--you have it your way, I'll have it mine (that is if I could get it to work!!!)

psyke83 - I did this, just as I did on the previous installations...9.04...8.10....etc.

It just isn't working and as I said, the man for i8kmon is very unclear.

Well, it works fine here.

Check:
```
$ modinfo i8k
```

Do you need to force the module?

After inserting the module, check your dmesg log. For example:
```
$ sudo rmmod i8k; sleep 3; sudo modprobe i8k; dmesg | tail
```

---

### Post by bobterri on 2009-10-16
Here you are:

$ modinfo i8k
filename:       /lib/modules/2.6.31-14-generic/kernel/drivers/char/i8k.ko
license:        GPL
description:    Driver for accessing SMM BIOS on Dell laptops
author:         Massimo Dal Zotto (dz@debian.org)
srcversion:     8E0EE56ED0D31F123D03354
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
parm:           force:Force loading without checking for supported models (bool)
parm:           ignore_dmi:Continue probing hardware even if DMI data does not match (bool)
parm:           restricted:Allow fan control if SYS_ADMIN capability set (bool)
parm:           power_status:Report power status in /proc/i8k (bool)
parm:           fan_mult:Factor to multiply fan speed with (int)

$ sudo rmmod i8k; sleep 3; sudo modprobe i8k; dmesg | tail
[sudo] password for bob: 
[   53.838594] [drm] TV-14: set mode NTSC 480i 0
[   56.997616] [drm] DAC-6: set mode 640x480 0
[   57.103251] [drm] DAC-6: set mode 640x480 0
[   57.308887] [drm] TV-14: set mode NTSC 480i 0
[   57.451992] [drm] TV-14: set mode NTSC 480i 0
[   67.219911] lib80211_crypt: registered algorithm 'CCMP'
[   67.385793] padlock: VIA PadLock not detected.
[   67.541727] lib80211_crypt: registered algorithm 'TKIP'
[ 1976.387255] i8k: unable to get SMM BIOS version
[ 1976.387271] Dell laptop SMM driver v1.14 21/02/2005 Massimo Dal Zotto (dz@debian.org)

---

