---
title: "Laptop CPU not scaling down when idle"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by evolutionx on 2009-03-17
Hi,

I'm currently running Jaunty 9.04 on a older Compaq nc6000 laptop and I am noticing that the CPU is stuck on it's max scaling of 1.6Ghz all the time.

It normally has three levels, 800Mhz, 1.2Ghz and 1.6Ghz which it scales to depending on system load.

Has anyone else encountered this on other Compaq/HP Laptops?

I'm not sure how to check why its stuck on 1.6Ghz but have included some information below, which may be useful.

cat /proc/cpuinfo
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Pentium(R) M processor 1.60GHz
stepping	: 6
cpu MHz		: 1600.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips	: 3189.97
clflush size	: 64
power management:
```

acpi -V
```
 Battery 0: Full, 100%
     Battery 0: design capacity 1486 mAh, last full capacity 1486 mAh = 100%
  AC Adapter 0: on-line
     Thermal 0: ok, 33.1 degrees C
     Thermal 1: ok, 56.0 degrees C
     Thermal 2: ok, 65.0 degrees C
     Cooling 0: Processor 0 of 10
     Cooling 1: Fan 1 of 1
     Cooling 2: Fan 1 of 1
     Cooling 3: Fan 1 of 1
     Cooling 4: Fan 0 of 1

```

lm-sensors
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +65.0°C  (crit = +103.0°C)                  
temp2:       +56.0°C  (crit = +115.0°C)                  
temp3:       +33.1°C  (crit = +103.0°C) 
```

---

### Post by nyarnon on 2009-03-17
Use top or systemmonitor to see what is using your CPU

---

### Post by evolutionx on 2009-03-17
Hi,

It doesn't appear to be under heavy load.  I've included the top header and a system monitor screen shot.

I have the system monitor and CPU frequency applets on my panel at the moment and I keep watching them closely. 

```
top - 20:09:21 up  3:22,  2 users,  load average: 0.25, 0.23, 0.19
Tasks: 126 total,   2 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  0.8%sy,  0.0%ni, 98.2%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:    509380k total,   484900k used,    24480k free,     9472k buffers
Swap:  1494004k total,   261848k used,  1232156k free,   114044k cached
```

```
cat /proc/acpi/processor/CPU0/throttling 
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

---

### Post by nyarnon on 2009-03-17
Ok, now let's try the following, do you have the scaling applet installed, if not install it now, then go to the properties of the applet and see what it current setting is.

---

### Post by RAOF on 2009-03-17
The most interesting thing is likely to be the contents of
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
I'd guess yours will say "performance", whereas what you want is "ondemand".  I'd guess that this is likely due to the changes in the powernowd init script that recently occurred; please file a bug!

While you're waiting for the bug to be fixed
```

echo "ondemand" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
will set CPU0's governor to ondemand, which is what you want.

---

### Post by nyarnon on 2009-03-17
@RAOF

That was what I was pointing to but considering the users knowledge I didn't want to hit him with low level gibberish.

---

### Post by evolutionx on 2009-03-17
Hi nyarnon,

Thanks for your help.  

I have cpufreq-applet installed and on the main panel.  The preferences only show appearance settings for the output on the panel. There is a screenshot below.  

Is this the same applet you are referring to?

When you mouse over it, it reads Performance 1.6Ghz (100%) but the processor use is < 10%.

---

### Post by nyarnon on 2009-03-17
Yes now try leftbutton click. :-)

---

### Post by RAOF on 2009-03-17
> **nyarnon said:**
> @RAOF

That was what I was pointing to but considering the users knowledge I didn't want to hit him with low level gibberish.

Fair enough, but we're in the Jaunty development forum before beta release.  I assume everyone here is not afraid of a little bit of copy-and-paste commandline fun!

---

### Post by nyarnon on 2009-03-17
> **RAOF said:**
> Fair enough, but we're in the Jaunty development forum before beta release.  I assume everyone here is not afraid of a little bit of copy-and-paste commandline fun!

Thats my point, you should have used 

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

then. Don't be surprised if a lot of users here wouldn't think of that. In fact I'm stuned how low the level of knowledge sometimes is here. But then again every tester helps and it's a great place to educate.

---

### Post by scaine on 2009-03-17
As of about 2 days ago, the default for scaling appeared to switch from "OnDemand" to "Performance".

Annoyingly, although it's easy to change with the CPU frequency scaler applet, and *despite* the fact that it asks for permission before doing so, the changes you make there are per-session only and on reboot, you'll be back to Performance.

Seems a strange decision to move to performance and possibly it's a simple bug/regression.  I'll have a hunt later on.

**Powertop** advises to move back to OnDemand, funnily enough...

---

### Post by evolutionx on 2009-03-17
Hi nyarnon and RAOF,

Bingo! You guys were right.

The scaling_govenor was set to performance. I've set it to ondemand and all is well again.

Thanks for bearing with me ;) Left clicking the applet was quite an oversight I must admit.

I actually came across a similar bug here [https://bugs.launchpad.net/debian/+bug/163398]("https://bugs.launchpad.net/debian/+bug/163398")
where ```
cpufreq-selector -g ondemand
``` was used to set it manually, which worked a treat too.

Thx again!

---

### Post by nyarnon on 2009-03-17
@Scaine

Did you file a bugreport?

---

### Post by scaine on 2009-03-17
Bug report here :
[https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252)

And a possibly related report here, but it's closed for a previous distribution :
[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/262567](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/262567)

I'm not on my laptop, so I can't confirm whether it's relevant.  If someone with this problem can run the code below to see if this correctly sets the scaling to "OnDemand", that would be very helpful :

```
sudo /etc/init.d/powernowd start
```

---

### Post by pferraro on 2009-03-17
> **RAOF said:**
> The most interesting thing is likely to be the contents of
```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
I'd guess yours will say "performance", whereas what you want is "ondemand".  I'd guess that this is likely due to the changes in the powernowd init script that recently occurred; please file a bug!

While you're waiting for the bug to be fixed
```

echo "ondemand" | sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

```
will set CPU0's governor to ondemand, which is what you want.

And if you're on a dual/quad core/processor machine, don't forget about your other cpus.  e.g.
```

cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```

---

### Post by scaine on 2009-03-17
> **scaine said:**
> And a possibly related report here, but it's closed for a previous distribution :
[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/262567](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/262567)

I'm not on my laptop, so I can't confirm whether it's relevant.  If someone with this problem can run the code below to see if this correctly sets the scaling to "OnDemand", that would be very helpful :

```
sudo /etc/init.d/powernowd start
```

I can answer my own question now that I'm back on my lappie - powernowd isn't installed on Jaunty, at least not by default since Alpha5 which my laptop is running, fully up to date.

So, it looks like we're stuck on the bug report I just filed and hope for a response.  At least there's a workaround.

[EDIT : Whoops - spoke too soon... just restarted my laptop and I'm back on performance.  I'll update my ticket on launchpad...]

---

### Post by taavikko on 2009-03-18
What, and now one has confirmed that bug?
Nevermind, did that myself ;)

---

### Post by nanomad on 2009-03-18
nanomad ~ $  grep -i default_gov /boot/config-2.6.28-10-generic  
# CONFIG_CPU_FREQ_DEFAULT_GOV_CONSERVATIVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_ONDEMAND is not set
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_POWERSAVE is not set
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set

Maybe the kernel is compiled the wrong way? (should be CONFIG_CPUFREQ_DEFAULT_GOV_ONDEMAND=y)

---

### Post by Nullack on 2009-03-18
A change just hit the build farm to make the default on demand

---

### Post by yanns on 2009-03-18
Installing the package cpufrequtils resolve the problem

---

### Post by PatrickVogeli on 2009-03-18
putting cpufreq-selector -g ondemand & into /etc/rc.local before exit 0 takes care of the problem. It's not nice, but it's a good fix until it's definitely fixed.

---

### Post by scaine on 2009-03-18
Yeah, like I say, I'll just keep the defaults so that I can test any changes pushed as a result of the bug I raised.  I've nominated it for Jaunty by the way.  Thanks to everyone who helped confirm it.  It's a bit of a hassle having to change this every time.

Ironically, when I used an EEE701, the processor on that thing was so poor that the first thing I did whenever I switched it on was put it into the "performance" setting!

As someone on the bug noted, an option for this should be placed into the gnome-power-settings dialog...

---

### Post by saracen on 2009-03-24
This has been fixed now.  See [https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/344252)

---

### Post by Andreas1 on 2009-04-09
> **scaine said:**
> As someone on the bug noted, an option for this should be placed into the gnome-power-settings dialog...

I agree.
This feature kind of existed once (not in the gnome-power-settings though) and then was removed. Look [here]("http://ubuntuforums.org/showthread.php?t=971578"). (while i basically understand the reasoning brought forward, i don't fully agree with/believe it. Experience taught me otherwise.)

---

