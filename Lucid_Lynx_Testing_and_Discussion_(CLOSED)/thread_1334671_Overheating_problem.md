---
title: "Overheating problem"
date: 2009-11-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2009-11-22
Ever since upgrading to Lucid my laptop has randomly shut itself down and been running very hot. Today I took the bottom panel off to check for dirt in the fan but all was well. The fan works until just before the login screen appears and then stops but acpi reports a steady 40c and never changes.

The laptop is an acer Aspire 5315.
Any ideas?

---

### Post by ronacc on 2009-11-22
check top to see if something is running the cpu at full throttle also check your power management settings .

---

### Post by macroshaft on 2009-11-22
> **ronacc said:**
> check top to see if something is running the cpu at full throttle also check your power management settings .

There are no settings for the fan in power management settings and none of that explains why acpi appears feel the cpu is at 40c all the time. My laptop has heat blindness!

---

### Post by qwerty2009 on 2009-11-22
hi i have the same laptop (come installed with vista) ive had the same problem since about a year after buying it

for me the middle part and the back part (back foot) of the base get extremely hot and it just turns itself off and when restarted it sometimes freezes on the bios screen ive read other places that people with the same laptop have the same problems i think its just a fault with the laptop as it happens on xp,vista and ubuntu (ive tried all)

i just keep mine off any soft furnishings and when i have it on a desk i tend to keep some over lapping the edge to keep the air circulating, theres not much more you can do to stop it

---

### Post by macroshaft on 2009-11-22
> **qwerty2009 said:**
> hi i have the same laptop (come installed with vista) ive had the same problem since about a year after buying it

for me the middle part and the back part (back foot) of the base get extremely hot and it just turns itself off and when restarted it sometimes freezes on the bios screen ive read other places that people with the same laptop have the same problems i think its just a fault with the laptop as it happens on xp,vista and ubuntu (ive tried all)

i just keep mine off any soft furnishings and when i have it on a desk i tend to keep some over lapping the edge to keep the air circulating, theres not much more you can do to stop it

Until this month mine has been happy in windows, ubuntu, whatever to stay turned on 24/7 on my bed. This is new for me.

---

### Post by faeirywoman on 2009-11-22
yeah mine had the same problem actually - just one day it decided it was gonna get lazy..... as querty said keep it cool - another trick i used was takin out the battery and pluggin it into the mains instead - alright if youre at home - if youre out - stick to the shade ;)

---

### Post by qwerty2009 on 2009-11-22
> **macroshaft said:**
> Until this month mine has been happy in windows, ubuntu, whatever to stay turned on 24/7 on my bed. This is new for me.

if you have the exact same problem as me (sounds like you do) you will soon notice a decrease in battery life and then in about 6 or 7 months ur battery will only last about 20 mins

---

### Post by ronacc on 2009-11-22
is your fan not running in lucid ? as to the temp , I think lucid has a problem reading the sensors , NM shows my wireless at 0% strength although it works just fine and another box 75 feet further away running karmic shows it at 57% ? powermanagement should show several settings fo a laptop IIRC something like power save , normal and maximum performance .

---

### Post by qwerty2009 on 2009-11-22
> **faeirywoman said:**
> yeah mine had the same problem actually - just one day it decided it was gonna get lazy..... as querty said keep it cool - another trick i used was takin out the battery and pluggin it into the mains instead - alright if youre at home - if youre out - stick to the shade ;)
+1 have you also had the battery issues i described ?

---

### Post by macroshaft on 2009-11-22
It looks like this is a problem karmic has brought to our doorstep. There is a patch for it but the kernel versions don't match mine and I'm not too keen on installing randomly in the hope I don't make things worse.

[http://ubuntuforums.org/showthread.php?t=1304612&highlight=acer+aspire](http://ubuntuforums.org/showthread.php?t=1304612&highlight=acer+aspire)

---

### Post by faeirywoman on 2009-11-22
as for battery problems - yes! but not as severe... 20 minutes is pushin it!!!

---

### Post by qwerty2009 on 2009-11-22
> **faeirywoman said:**
> as for battery problems - yes! but not as severe... 20 minutes is pushin it!!!
lmfao :P i have had my laptop nearly 2 years nw so that could add to it lol as for the over heating mine started whilst i was still using vista so its not karmics fault fr me

---

### Post by ronacc on 2009-11-22
if you think it is mabye due to the OS get a livecd of jaunty or hardy and try that , just run the livecd no need to install , but the suggestion from the others about mabye a battery getting old sounds like it could be it , an old tired battery will have a high internal leakage rate .

---

### Post by Gina on 2009-11-23
I get an unexplained increase in CPU activity with Karmic and Lucid too.  Including running off a Live CD.  Just the operating system and default start-up apps, no other app set to run.  System Monitor doesn't show any individual app using more than a few % yet the CPU History shows 50-80% and the CPU switches to a higher speed.

---

### Post by pulpo69 on 2009-11-23
i would generally like to see a good tool or applet for temperatur and fan in ubuntu. But there isn't or not for all boards and cpu's.
For boards with AMD Phenom cpu i don't no a working tool for reading the temperature. (lm-sensors don't work).

---

### Post by Rusna on 2010-03-24
Any progress on this? 
I have Lucid and Amilo L1310G and my CPU fan stops after a while. It is really annoying, the only solution I've found is a reboot and that fixes it for another 20mins or so...?

---

### Post by Rusna on 2010-03-24
Is there something I can do to help to debug the problem? Some logs etc? 
Would be awesome to get rid of this problem.

---

### Post by psusi on 2010-03-24
It sounds like the bios is retarded and shuts down the fan before booting the OS, and leaves it to the OS to manage the fan, and it sounds like yours isn't.  The sad thing is that ACPI is supposed to handle this automatically in such a way that the fan gets turned on when the machine gets hot enough, not matter what the OS is doing, even if it is totally hung up.  Unfortunately it seems that no vendors implement ACPI properly.

lm-sensors and the fancontrol script should allow you to monitor temperature and control the fan once set up correctly.  Again, because of broken ACPI bios, it stopped working for many people in Karmic because the bios claims the resources needed even though it does not use them, and the newer kernels respect that and won't let the modules that lm-sensors uses have those resources, even though the ACPI bios doesn't actually use them properly.  You can fix this by adding acpi_enforce_resources=lax to your kernel command line.

---

### Post by Rusna on 2010-03-24
> **psusi said:**
> 
lm-sensors and the fancontrol script should allow you to monitor temperature and control the fan once set up correctly. 

You can fix this by adding acpi_enforce_resources=lax to your kernel command line.

Yes, I'm monitoring CPU temperatures by using lm-sensors and sensors-applet. sensors-detect does not find any compatible sensors, so sensors-applet is grabbing the temperatures from acpi.

When I try to configure fancontrol by pwmconfig, it's complaining that there're no pwm-compatible sensors loaded.

I tried adding ```
acpi_enforce_resources=lax
``` to kernel loading via grub command line editing, but it did not have any effect? Is there a way I can confirm that the acpi setting has been succesfully loaded, and functioning? CPU fan still turning off...

---

### Post by psusi on 2010-03-24
Huh?  The purpose of the switch is to allow the modules that sensors-detect and pwmconfig use to continue to work under the new kernel.  If sensors-detect still does not find anything then you're out of luck.  The only other thing I would suggest is look for a bios update or a setting in the bios you can switch so it just leaves the fan on all the time.

---

### Post by Rusna on 2010-03-24
Yep, pwmconfig doesn't find anything and neither does sensors-detect.

Sadly this Amilo has that much of age for a laptop that there's no chance in hoping for a new bios update.

So this is it? No ubuntu for this machine then? This sucks.

---

### Post by rixtr66 on 2010-03-24
Dont worry!I have an acer aspire 5315,and i am running karmic
with no overheating issues!i had the same problem a while back,
and it is in fact the bios.but there is a solution.
[http://ubuntuforums.org/showthread.php?t=1043129&highlight=laptop+overheating&page=2](http://ubuntuforums.org/showthread.php?t=1043129&highlight=laptop+overheating&page=2) post#13
be very careful!!!there are two choices,i downloaded and burned the
bios flash and it worked.BUT after flashing the bios i got the blue screen of death on win 7 so i had to reinstall windows.so back up your files if your running windows.and be prepared to reinstall.
its alot to do but it was worth it.i can now run the new kernels.
and im happily running 9.10 and testing 10.04!
Good luck!
Rick

---

### Post by Rusna on 2010-03-25
Thanks but I have Fujitsu-Siemens Amilo L1310G, not Acer Aspire 5313. So I'm still stuck...

---

### Post by rixtr66 on 2010-03-25
oops! sorry misread.my bad.
Rick

---

### Post by Rusna on 2010-03-25
Case solved on Fujitsu-Siemens Amilo L1310G!

All I had to do is to edit /etc/default/grub file and edit this:
```
GRUB_CMDLINE_LINUX=“acpi.power_nocheck=1” 
``` and do ```
sudo update-grub
```

Now fan is starting and stopping nicely and my Amilo will not overheat anymore!

---

