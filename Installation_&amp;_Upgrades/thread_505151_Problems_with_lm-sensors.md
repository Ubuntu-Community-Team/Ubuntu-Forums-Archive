---
title: "Problems with lm-sensors"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Rich1386 on 2007-07-19
I followed a how-to post for installing and configuring lm-sensors, and everythign seemed to go ok, but when i tried to run "sudo sensors" it said that no sensors were detected.  I rebooted as the how-to said, but my screen wouldnt come up.  I had to boot in recovery mode and try again, but same thing happened.  Now I can't boot into regular ubuntu.   Also, sometimes when booting into recovery mode, "Setting sensor limits", something worded like that, will fail.  Others it wont be seen.

All help is appreciated

---

### Post by bren on 2007-07-20
z

---

### Post by confused57 on 2007-07-20
> **Rich1386 said:**
> I followed a how-to post for installing and configuring lm-sensors, and everythign seemed to go ok, but when i tried to run "sudo sensors" it said that no sensors were detected.  I rebooted as the how-to said, but my screen wouldnt come up.  I had to boot in recovery mode and try again, but same thing happened.  Now I can't boot into regular ubuntu.   Also, sometimes when booting into recovery mode, "Setting sensor limits", something worded like that, will fail.  Others it wont be seen.

All help is appreciated
You might want to check out this lm_sensors howto:
[http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors](http://ubuntuforums.org/showthread.php?t=2780&highlight=lm-sensors)

To get back into Ubuntu, boot into the recovery mode, then enter:
```
nano /etc/modules
```

delete the section pertaining to sensors(or place a # in front of)...might be best to place a #(comment out), instead of deleting...ctrl+x, y, enter...this will save the changes.  Then I think you just need to press "Esc" to continue into a GUI, or possibly enter reboot.

---

### Post by Rich1386 on 2007-07-20
Unfortunately no change.  It still leaves me with the monitor not getting any signal.  Any other suggestions?

Thanks

---

### Post by confused57 on 2007-07-20
> **Rich1386 said:**
> Unfortunately no change.  It still leaves me with the monitor not getting any signal.  Any other suggestions?

Thanks

Which howto did you follow?

I don't know  if it would make a difference if you tried uninstalling lm-sensors:
```
sudo apt-get remove --purge lm-sensors
```

---

### Post by Rich1386 on 2007-07-20
I used the how to that you linked to.

Removing it didn't help.

---

### Post by Rich1386 on 2007-07-22
can anyone help?

Much appreciated

---

### Post by Pumalite on 2007-07-22
I installed GKrellM through Synaptic. I consider it better than l-sensors.

---

### Post by Rich1386 on 2007-07-22
I'll certainly consider it after this mishap, but any insights on how to get my GUI/login screen back?

---

