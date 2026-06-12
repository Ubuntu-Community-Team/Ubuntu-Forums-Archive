---
title: "CPU throttling and fan noise on Lenovo x200 laptop"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shuttleworthwannabe on 2010-04-04
Hi there--I have just installed 10.04 beta on my X200 Thinkpad. All seems to be working just fine, but the problem is the CPU--it is constantly at 2.53GHz (max) and fan speed is always blowing. I can adjust the CPU to "on demand" using the panel applet, but now the fan still continues to blow (in windows it is silent).

Any suggestions?

---

### Post by songochain on 2010-04-04
Same here, cpu is at 40% but fan is running all time.
BR.

---

### Post by songochain on 2010-04-04
I think I've found the problem:

> 
link@link-laptop:/proc/acpi/thermal_zone/THRM$ cat trip_points 
critical (S5):           92 C
passive:                 90 C: tc1=2 tc2=3 tsp=20 devices=CPU0 


It should be:

> 
link@link-laptop:/proc/acpi/thermal_zone/THRM$ cat trip_points 
critical (S5):           92 C
passive:                 90 C: tc1=2 tc2=3 tsp=20 devices=CPU0 **CPU1**


---

### Post by shuttleworthwannabe on 2010-04-05
Thanks for the pointers. But, do you notice that the fan speed _also _comes down with this new setting? CPU is P8700 C2D Centrino 2 @2.53GHz. 

I tried this work around, and CPU now automatically throttles down--but noticed that fan still blazing.

BTW don't you think those critical and passive tempts are very high?? (I am not technically gifted, so I may be wrong)

---

### Post by songochain on 2010-04-05
I don't know what value I have to set on trip_points file so i can't probe the settings.
My cpu temp is always 40ºC because cpu fan is always running.
Also I've seen fancontrol file under /etc/fancontrol is missing. Something it's wrong with acpi.
BR.
Edit: Try this [http://goo.gl/AXfb](http://goo.gl/AXfb) I can't now because I'm at work.

---

### Post by flomar on 2010-04-15
I have a X200 myself and just installed 10.04 Beta 2 on it via Wubi. The problem you describe unfortunately is a very old one and could not be fixed. See this [bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380303?comments=all") and the [X200 owners]("http://ubuntuforums.org/showthread.php?t=907936") thread.
You might find some interesting reading on [thinkwiki]("http://www.thinkwiki.org/wiki/ACPI_fan_control_script").

---

### Post by Sylslay on 2010-04-15
92C is very high for any silicon chip , even with active cooling.
Working temp are 40-70C (depend if chip was made of Cu, AL and Si):confused:

---

