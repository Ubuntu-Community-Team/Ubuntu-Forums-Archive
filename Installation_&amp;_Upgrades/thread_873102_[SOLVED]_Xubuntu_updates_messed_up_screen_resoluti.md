---
title: "[SOLVED] Xubuntu updates messed up screen resolution"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by Valve on 2008-07-28
Hi,
I've had Xubuntu (Hardy Heron) running alongside Vista (wubi installation) for a few months. Today I ran the update package as normal, which required a reboot. When Xubuntu restarted the screen resolution was wrong with no option to change it. The resolution is painful on the eyes.

I have tried everything I can think of: I looked for packages to run my graphics card (ATI Radeon Xpress 200) and installed, but nothing happened. I opened the hardware driver window and checked the box to enable the ATI driver, but now everything won't run. I have had options for changing the screen in low graphics mode, but it's hopeless.

What has gone wrong? Any help appreciated.

---

### Post by Partyboi2 on 2008-07-28
Have you tried booting into recovery mode and using xfix?

---

### Post by Valve on 2008-07-28
> **Partyboi2 said:**
> Have you tried booting into recovery mode and using xfix?
I admit I don't fully know my way around the system yet. Could you explain how to get into recovery mode and get onto xfix?
Thanks

---

### Post by Valve on 2008-07-29
I got into xfix and system now boots again. But the resolution is still vertically stretched and very blurred. It used to work fine. Now the ATI card just won't work properly uder Linux.

---

### Post by Partyboi2 on 2008-07-29
Give [[COLOR=Blue]envy [/COLOR]]("http://albertomilone.com/nvidia_scripts1.html")ago, has worked for me when I have had problems.

---

### Post by Valve on 2008-08-05
Envy hasn't worked for some reason. I installed the driver through envy and rebooted, but nothing has changed. I then opened the jockey interface and enabled the driver (which requires restart). On restart it simply has no video support or offers a configuration option which won't configure.

Are there really no solutions? I'm getting depressed having to use Vista.

---

### Post by Valve on 2008-08-06
Well, after a lot of mucking about and changing from Xubuntu to Ubuntu (though I suspect this has no influence) I have the card working. Who knows for how long.

After editing the xorg.config and adding the driver name I rebooted and got the 'input not supported' nonsense. I booted into recovery and did xfix and to my astonishment it was ok on the login screen.

This was the guide I followed:
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Looks like it's solved for now.

---

