---
title: "CPU Frequency Scaling changed under Ibex??"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jboehm on 2008-10-23
Hi,

I running a desktop machine with a Core 2 Duo.  There does not appear to be any frequency scaling by default.  It also appears that the standard HOWTO for this topic no longer applies:

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

Most of the packages that it mentions no longer exist.

How do I turn on the correct scaler for a C2D under Ibex??

Thanks,
Jon

---

### Post by waspbr on 2008-10-23
the frequency scaling packages are already there, I reckon it used powernowd, anyway all you have to do it to right click in one of your panels, select the "add to panel option", the chose the CPU frequency scaling monitor applet, you should be sorted then.

---

### Post by jboehm on 2008-10-23
The HOWTO I mentioned says to uninstall powernowd and install speedstep-centrino for a core duo.  speedstep-centrino does not exist.  powernowd does not scale voltages only frequencies.  I'm wondering if cpufreqd is now the package to use.

Thanks,
Jon

---

### Post by myddewji13 on 2008-10-23
im using the cpu scaling applet...although this has nothing to do with your question is there a way to get it running on 'ondemand' when my laptops on battery and 'performance' when its on ac power. I know that in hardy one could do this with gconf-editor but the entries no longer exist...

---

### Post by PatrickVogeli on 2008-10-23
powernow is just fine. speedstep-centrino is deprecated in favour of acpi-cpufreq, and that's the module you should be using. It's not powernowd that controls the voltages, but the acpi-cpufreq  module. If you install phctool (search on the web how to install it) and modprobe msr before using it, you'll see how the voltages scale up/down with the frequency

That howto is deprecated, forget about it. 2 years in Linux means a lot.

---

### Post by PatrickVogeli on 2008-10-23
> **myddewji13 said:**
> im using the cpu scaling applet...although this has nothing to do with your question is there a way to get it running on 'ondemand' when my laptops on battery and 'performance' when its on ac power. I know that in hardy one could do this with gconf-editor but the entries no longer exist...
I have them under Apps -> gnome-power-manager -> cpufreq

---

### Post by mdurham on 2008-10-23
> **PatrickVogeli said:**
> I have them under Apps -> gnome-power-manager -> cpufreq
Where is 'Apps" ?

---

### Post by mc4100 on 2008-10-23
> **mdurham said:**
> Where is 'Apps" ?

Well, the folder is in:
```
~/.gconf
```
... but the keys should be changed in the **configuration editor**:
```
gconf-editor
```

---

### Post by mdurham on 2008-10-23
> **mc4100 said:**
> Well, the folder is in:
```
~/.gconf
```
... but the keys should be changed in the **configuration editor**:
```
gconf-editor
```

Thanks

---

