---
title: "A few problems after the upgrade to 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by chunchengch on 2008-11-02
I upgraded my Ubuntu 8.04 to 8.10 on last Saturday, and found some problems need help,

1. I have set the CPU frequency policy to be [COLOR="Red"]**performance**[/COLOR] in the gconf-editor [COLOR="Green"](apps > gnome-power-manager > cpufreq > policy_ac)[/COLOR], however, every time I boot the computer, it always adopts the policy [COLOR="Red"]**ondemand**[/COLOR].

I installed the cpufreq-selector and added the module acpi-cpufreq to /etc/modules, but no helps.

2. Like Ubuntu 8.04, Ubuntu 8.10 uses pulseaudio as the sound sever, but I notice that I can activate only one media program at a time, otherwise, the other program has no sound output, of course, the system sound is also disabled. this problem occurred in Ubuntu 8.04, I just wonder why six months later, Ubuntu 8.10 still has the same problem?

I solved this problem by editing /etc/pulse/default.pa to modify the following two lines

[COLOR="Green"]#load-module module-alsa-sink 
load-modul module-suspend-on-idle[/COLOR]
 
to

[COLOR="Green"]load-module module-alsa-sink device=dmix
#load-modul module-suspend-on-idle[/COLOR]

but I got another problem with this modification, I can not adjust the volume with combined keys Fn+F11 and Fn+F12 , this did not happen in Ubuntu 8.04, I tried many times to solve it but still no success.

3. Cheese can be activated normally, but the webcam is still on after the Cheese is closed, the only way to shutdown the webcam is to **[COLOR="Red"]power off[/COLOR]** the computer. (The light of webcam is still on if [COLOR="Red"]reboot[/COLOR], that is weird)


Thanks for any clues and solutions to these problems.

---

### Post by MacheteMurderer on 2008-11-03
I have a similar problem with my CPU frequencies, the governor does revert after restarts but that isn't the main problem - my CPU frequencies are locked to the minimum clockspeed. Even though several speeds are listed in /sys/devices/system/cpu/cp0/cpufreq/scaling_available_frequencies

---

### Post by brujoand on 2008-11-03
I just did a fresh install of 8.10 and The cpu-freq settings are no longer in Gconf-editor. Also when i tried to run "acpi-freq -c 1 -g conservative" It sets the governor to conservastive, but the command never returns.. I think sombody made a pupu in this module...

---

### Post by brujoand on 2008-11-25
bumbp

---

