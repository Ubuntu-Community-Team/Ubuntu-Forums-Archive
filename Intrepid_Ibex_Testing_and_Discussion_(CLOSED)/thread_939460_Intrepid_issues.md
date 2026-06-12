---
title: "Intrepid issues"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by smmalis on 2008-10-05
I've been trying out the Intrepid beta and love it so far, but I have two (minor) issues:
1. I can't figure out how to change the default governor for cpu frequency scaling
2. Occasionally it boots into 640x480 resolution, instead of the 1280x1024 I set in xorg.conf.
I realize that this is a beta, but help would be appreciated.

---

### Post by Yellow Pasque on 2008-10-06
```
sudo apt-get install cpufrequtils
sudo cpufreq-set -g <governor>

cpufrequtils 002: cpufreq-set (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
Usage: cpufreq-set [options]
Options:
  -c CPU, --cpu CPU        number of CPU where cpufreq settings shall be modified
  -d FREQ, --min FREQ      new minimum CPU frequency the governor may select
  -u FREQ, --max FREQ      new maximum CPU frequency the governor may select
  -g GOV, --governor GOV   new cpufreq governor
  -f FREQ, --freq FREQ     specific frequency to be set. Requires userspace
                           governor to be available and loaded
  -h, --help           Prints out this screen

Notes:
1. Omitting the -c or --cpu argument is equivalent to setting it to zero
2. The -f FREQ, --freq FREQ parameter cannot be combined with any other parameter
   except the -c CPU, --cpu CPU parameter
3. FREQuencies can be passed in Hz, kHz (default), MHz, GHz, or THz
   by postfixing the value with the wanted unit name, without any space
   (FREQuency in kHz =^ Hz * 0.001 =^ MHz * 1000 =^ GHz * 1000000).
```

---

### Post by Sef on 2008-10-06
moved to ibex forum.

---

### Post by smmalis on 2008-10-06
I'm aware of cpufreq utils, but how can I run the command on startup?  Also, thanks for moving to the Intrepid forum, I didn't see it earlier.

---

### Post by Yellow Pasque on 2008-10-06
Put the command in your ~/.profile file ( gedit ~/.profile )

---

### Post by smmalis on 2008-10-06
Will that run with root privileges?  I believe cpufreq needs to be run as root.  Also, does anyone have an idea on #2?  I'm using the nvidia driver.

---

