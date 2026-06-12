---
title: "Live CD boot fail &quot;Cannot Display this Mode&quot;"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by neotint on 2010-08-28
Trying to boot Ubuntu 10.04.1 live CD and I get nowhere because the screen just stays black, with a monitor OSD alert saying "Cannot display this mode."

Is there a consumer version of Ubuntu available for regular people to use? I searched on the fourms and any post about "cannot display this mode" advises users to edit configuration files, or go into command line mode... what is this, 1991? Seriously?

What is the real solution to this? Or is Ubuntu not made for consumer users? What other options do I have besides Mandrake?

The Ubuntu screenshots looks swell, nice graphic design of the user interface, pretty, but they should make the installer/live CD actually work like any other OS in 2010 first tho'.

Any help is appreciated. Thank you.

---

### Post by mörgæs on 2010-08-29
> **neotint said:**
> Trying to boot Ubuntu 10.04.1 live CD and I get nowhere because the screen just stays black, with a monitor OSD alert saying "Cannot display this mode."

Is there a consumer version of Ubuntu available for regular people to use? I searched on the fourms and any post about "cannot display this mode" advises users to edit configuration files, or go into command line mode... what is this, 1991? Seriously?

What is the real solution to this? Or is Ubuntu not made for consumer users? What other options do I have besides Mandrake?

The Ubuntu screenshots looks swell, nice graphic design of the user interface, pretty, but they should make the installer/live CD actually work like any other OS in 2010 first tho'.

Any help is appreciated. Thank you.



First: Another attitude might help. Are you American?

Then: A thorough description of your hardware would make it easier to provide an answer. 

And then: Which kind of experimenting have you done? Booting with older releases of Ubuntu, for example? 

And then: Did you try any of the recommendations found in the forum, or did you decide a priori that they were no good? If you for principal reasons don't want to type a command, you might give yourself a hard time.

---

### Post by oldfred on 2010-08-29
mörgæs, I laughed ( on first) but I know it it altogether too true in many cases.

To the OP:

Have you tried f4 or f4 on the initial boot of the CD? These give options for less standard hardware. I have install Ubuntu on my two PCs with out any issue with 9.10, but 10.04 has a regression with a new design video system that require me to add nomodeset (with f6) on both liveCD and initial boot (e - edit grub menu). Some other video driver settings are required for other hardware.

---

