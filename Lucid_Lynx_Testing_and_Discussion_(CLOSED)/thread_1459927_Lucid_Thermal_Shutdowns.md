---
title: "Lucid Thermal Shutdowns"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dhlii on 2010-04-22
I have an HP DV8333 that I upgraded from a core duo to a core 2 duo some time ago. 

Works fine in Karmic. But I am getting frequent thermal shutdowns in Lucid.
I can delay the inevitable by forcing the system to powersave using the cpu freq/power management applet..
But eventually something changes the setting back to ondemand and if I do not catch it quick enough the system shutsdown. 

Ultimately I would like to get the thermal management working correctly so that ondemand actually works and the system scales itself back. 

Where do I find whatever is periodically changing the power management ? 
How do I force it to something that will not kill the system ?
And what do I need to do to fix the thermal throttling so that the system goes to a lower power state before it hits the critical shutdown trigger ?

---

### Post by x-shaney-x on 2010-04-22
Not much help to you but my missus is suffering from the same problem on her laptop.
Please post back if you find a solution?

---

### Post by BrokeMahPC on 2010-04-22
Interesting problem!
Does this laptop have the Geforce Go 7600 graphics?
Are you sure it's heat from the processor and not from the adjacent graphics chip?
There have been some video driver issues but can't help further as all my experience is with ATI cards.

---

### Post by dhlii on 2010-04-22
Yes it has then nVidia Corporation G73 [GeForce Go 7600] (rev a1) adapter.

from syslog
kernel: [17008.844268] Critical temperature reached (99 C), shutting down.

99C is the CPU0/1 threshold. 

IT is possible that the GeForce could be cooking the CPU but it is the CPU temp that is causing the shutdown. 

I have a CPU freq scaling applet and a temp applet installed so I can watch this.

Leaving the CPU's set to powersave radically decreases (but does not eliminate) thermally triggered reboots. 
Leaving it set to ondemand pretty much guarantees that the system will reboot constantly.

I can force reboots by increasing the load - particulary with mathematically intense tasks like video encoding. 

What I want is to be able to tweak the CPU parameters so that I do nto have to worry about what I am running, so that I get the most performance possible, and so that whateer is managing this will choke the crap out of the CPU if necescary before allowing it to cook or reboot.

slow        bad
rebooting   worse
cooking CPU worst. 

I can tweak the kernel ACPI parameters, but there appears to be some task already doing that. 
I would like to know what that is and how I can configure it.

---

### Post by dhlii on 2010-04-22
More,
  I did not/do not get thermal shutdowns in Karmic.
  nor in windows. 

  At the same time atleast these shutdown are almost graceful. 

  I once had a Toshiba P25 with a P4 that would periodically overheat. Rather than letting the OS bring things down gracefully the CPU would shutdown.
   
   I can probably reduce the shutdowns by tearing the laptop apart cleaning out the fan and heatsink and putting new thermal grease on the CPU.

    But I am pretending I do not need bifocals, and tearing apart a laptop occasionally results in a dead laptop.

---

### Post by moviemaniac on 2010-04-22
> **x-shaney-x said:**
> Not much help to you but my missus is suffering from the same problem on her laptop.
Please post back if you find a solution?
If you're using ATI on the notebook you should read this thread/posts:

[http://ubuntuforums.org/showpost.php?p=9136784&postcount=3](http://ubuntuforums.org/showpost.php?p=9136784&postcount=3)
[http://ubuntuforums.org/showpost.php?p=9143602&postcount=17](http://ubuntuforums.org/showpost.php?p=9143602&postcount=17)

---

### Post by BrokeMahPC on 2010-04-22
Something is producing heat in lucid and not in windows or karmic. I have not heard of a CPU bug? (anyone?). I would suspect the GPU.

Some people with ATI laptops have had this problem - is it affecting Nvidia as well? Tweaking the CPU to deal with an overheating GPU probably isn't the best course of action. 

The only time I have had similar problems was not replacing the heatsink correctly after upgrading a CPU. If this was the problem in your case you would get shutdowns in Karmic and Windows - you don't?

---

### Post by x-shaney-x on 2010-04-22
> **moviemaniac said:**
> If you're using ATI on the notebook you should read this thread/posts:

[http://ubuntuforums.org/showpost.php?p=9136784&postcount=3](http://ubuntuforums.org/showpost.php?p=9136784&postcount=3)
[http://ubuntuforums.org/showpost.php?p=9143602&postcount=17](http://ubuntuforums.org/showpost.php?p=9143602&postcount=17)

It is integrated Intel in my case.  Inspiron 1525/X3100 graphics

---

### Post by moviemaniac on 2010-04-22
Sorry, I don't know whether the lack of power management in the ATI KMS driver applies to Intel/NVidia too - I only have ATI cards in my household.

You could try to disable KMS and revert to UMS by adding "nomodeset" to the grub options. This reverts graphics support back to what it was in Karmic.

---

### Post by dino99 on 2010-04-22
check packages installed into synaptic:
-lm-sensors
-libsensors-applet-plugin0
-fancontrol
-sensors-applet
-xsensors


thats sound your sensors are not detected: run sensors-detect and add them to your settings

old thread: [http://ubuntuforums.org/showthread.php?t=1009540](http://ubuntuforums.org/showthread.php?t=1009540)

[http://www.robotsystematic.com/2009/ubuntu/howto-fan-control-in-ubuntu/](http://www.robotsystematic.com/2009/ubuntu/howto-fan-control-in-ubuntu/)

---

### Post by clhsharky on 2010-04-22
HI moviemaniac

If you would like to test ATI Power Management heres instructions

> 3 R600/R700 laptops that need Power Management that fglrx has but is not a delight on linux can now be tested in OSS drivers.

You need KMS its default in Lucid and the 2.6.34 kernel-ppa/mainline/drm-next
[http://kernel.ubuntu.com/~kernel-ppa...-next/current/](http://kernel.ubuntu.com/~kernel-ppa...-next/current/) 
and you may need radeon.dynpm=1 in the boot string

I also recommend xorg-edgers PPA
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)


[http://ubuntuforums.org/showthread.php?t=1458089&page=3](http://ubuntuforums.org/showthread.php?t=1458089&page=3)

Sharky

---

### Post by dhlii on 2010-04-22
So far I think I have fixed this. 

I tried a number of things.

fancontrol is does not work with the fans in  my laptop.

I tried cpufreqd and so far that looks promising.

The laptop is running both faster and on average hotter, but so far it has not shutdown. 
Even though it is running hotter the temperature is not spiking so much and the fans are running alot more.

---

