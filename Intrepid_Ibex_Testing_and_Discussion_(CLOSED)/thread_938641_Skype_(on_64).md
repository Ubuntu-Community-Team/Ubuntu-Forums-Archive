---
title: "Skype (on 64)"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Odisej on 2008-10-05
Is there a new problem with using skype on Intrepid 64 on the horizon?

After following instructions from this thread 

[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

I get an error if trying to run skype from terminal

> Fatal: Cannot mix incompatible Qt libraries
Aborted (core dumped)


It may just be that the instructions are incorrect or incompatible with latest intrepid beta but it seemed wise to report this problem here as well. 

Odisej

---

### Post by lucanuscervus on 2008-10-05
I'm running Ubuntu 8.10 beta and I'm having some problems as well. Skype, either the standard or the static version from the Medibuntu repos, was complaining about some missing libraries although they were installed. That was easy to fix using "ldd skype" and afterward creating symbolic links.
The problem now is the following:

> ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library /usr/lib/alsa-lib/libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

---

### Post by grumpymole on 2008-10-05
Search for the ALSA crash in google.  I found a launchpad bug that advises which asla file to edit.  This fixes the core dump.  Sorry, can't remember the details, but it is fixable.

I have skype working on my amd64 intrepid now.  After the QT lib fixes and fixing the core dump above.

Cheers

---

### Post by lucanuscervus on 2008-10-05
Thanks for this information. I'll check on Google. The most annoy thing is that skype works perfectly on my laptop which is using 8.10 alpha 3.

---

### Post by bpl07 on 2008-10-05
Skype is 32-bit, but as you can see from your error, it's trying to use 64-bit alsa libs.  There's a temporary fix for this, but hopefully we'll get an official one soon.  Check the end of the Pulseaudio thread for the temporary fix.

---

### Post by ktp on 2008-10-05
check following bug:
[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/273693](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/273693)

---

