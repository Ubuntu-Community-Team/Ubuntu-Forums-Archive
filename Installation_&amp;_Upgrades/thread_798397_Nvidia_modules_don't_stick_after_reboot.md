---
title: "Nvidia modules don't stick after reboot"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Everheart on 2008-05-18
Hi,

Since I upgraded to hardy heron, I've been having this problem that each time I boot, I get this low-resolution prompt whining about my gfx card not being detected etc, no matter what I did (envy, nvidia binaries, restricted manager,...)

Luckily, I managed to find a solution: I put the following lines into the /etc/init.d/gdm file so the drivers work every time the system boots:

```
apt-get -y install linux-restricted-modules linux-restricted-modules-2.6.24-16-generic linux-restricted-modules-common linux-restricted-modules-generic --reinstall
insmod /lib/modules/2.6.24-16-generic/volatile/nvidia_new.ko
```

With those lines in the gdm file, my drivers work perfectly (compiz, games,...), but the problem is that this is ofcourse just a triage, and that it has to reinstall those modules each time it starts up, which takes time.

What I would like to find out is, why do I have to reinstall all of these packages in order to my driver to work? Why are they being reset after a reboot? And why do I need to reinsert the module thing each time?

Thanks in advance if you are able to help me,
Everheart.

---

### Post by jsegars on 2008-05-18
I had the same issues, the new drivers would appear to work correctly but after a reboot I would get a low res message saying it couldn't detect my display driver. Looking through the xorg log file it would error out on loading the glx module saying it didn't exist or it wasn't compatible (not sure which). Either way it looked like the nvidia installer wasn't removing all the old module information. I believe there were some residual things hanging around. To fix the issue I used envyng to uninstall any current packages and let it find/install what I needed. Everything works fine now. Hope this helps.

---

### Post by Everheart on 2008-05-18
Thanks for the advice jsegars, it really did help.

Although I also noticed that I had modules nv and nvidia blacklisted, hence why they got blocked upon reboot...

So what solved it for me was uninstall drivers, reinstall linux-restricted-modules (although I'm not sure if that did anything), unblacklist drivers, reboot, install drivers.

When you find a solution it all seems so obvious...

---

