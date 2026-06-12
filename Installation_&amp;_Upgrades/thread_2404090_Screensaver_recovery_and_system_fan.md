---
title: "Screensaver recovery and system fan"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by raccoonstrait on 2018-10-19
Good day all,

Additional problems with upgrade to 18.10. When screensaver, or more accurately screen blanking happens, nothing will restore the screen, except a power off reboot. The second issue is the fan is running constantly, and the keyboard is warm when there is nothing actually requested from the CPU and the monitor shows no CPU activity.

I have tried reinstalling (using Synaptic) all installed python, xfce, power, and gdkpixbuf (due to errors seen in the original dist-upgrade terminal output). No luck so far.

This is a System 76 Bonobo laptop running Xubuntu. The issues found prior to upgrade were all resolved, and the system was running very well prior to upgrade.

Please let me know if additional information is needed to find a resolution.

Raccoon Strait

---

### Post by adelpozoman-f on 2018-10-20
Can you use other options of ubuntu when booting, and test the old kernel wich should still be there?

---

### Post by raccoonstrait on 2018-10-20
Interesting. I rebooted and was presented with two options under Ubuntu Advanced. 4.18.0.10 and 4.15.0.36. I chose the older one and when the boot completed let the screen go blank. Using the mouse the screen recovered. Also, the issue with the fan running constantly went away. 

I then rebooted into the normal Ubuntu and the screen blanking issue returned, but the fan running has stopped. I suppose I will need to wait for a new kernel for the fix now. Is there some place I should report this, or do the kernel folks read this?

Raccoon Strait

Well, the fan running constantly is back. Nothing taxing to the CPU is happening.

---

### Post by dino99 on 2018-10-20
Think to always clean the system after a dist-upgrade, to purge orphans and old settings left behind, and often disturbing the system.
Use 'autoremove' 'gtkorphan' and/or 'bleachbit'

---

### Post by raccoonstrait on 2018-10-20
The system has been cleaned with apt-get autoremove, apt-get autoclean, and bleachbit. No help.

Raccoon Strait

---

### Post by raccoonstrait on 2018-10-20
Reading in a different thread I tried running 

```

journalctl -b

```

Here is the output

```

https://paste.ubuntu.com/p/ymzPwQqBT5/

```

There were several red highlighted lines, unfortunately they did not remain red when copy and pasted into pastebin.

I have no idea what to do with this information.

Raccoon Strait

---

### Post by raccoonstrait on 2018-10-22
OK,

My query to System76 got a response. They recomended:

```

[COLOR=#574F4A][FONT=&quot]sudo apt purge nvidia* && sudo apt autoremove[/FONT][/COLOR]
[COLOR=#574F4A][FONT=&quot]sudo apt install system76-driver-nvidia[/FONT][/COLOR]
[COLOR=#574F4A][FONT=&quot]reboot

```

And that has worked.

Thank you everybody.

Raccoon Strait[/FONT][/COLOR]

---

