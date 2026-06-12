---
title: "Failed to load the NVIDIA kernel module"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by john@ukgillies.com on 2010-05-04
Can anyone please help.

I have just upgraded from Karmic kubuntu to Lucid. A full distribution update.

This appeared to go well - lots and lots of files were downloaded. When I tried to restart I discovered that I could not start kubuntu. I could get a tty2 login, but any attempt to load the graphical desktop fails.

I discovered that the upgrade did not load the latest kernel so I did this from the command line and now have the 2.6.31-22 kernel loaded. I also got the headers etc....

But I still cannot get past the tty login! I get the message - failed to load the NVIDIA kernel module. 

How do I get past this. Tearing my hair out!!

PS I know that Lucid will run on the machine as I have this running on a different partition for testing purposes.

Thanks,

John

---

### Post by willko6 on 2010-05-05
I had this same problem, except it only happened after I upgraded the kernel, i.e. the upgrade to Lucid went fine, but when I accepted the kernel upgrade and rebooted I got the "failed to load the NVIDIA kernel module" error.  For me, installing the headers fixed the problem. Sorry I can't help.

---

### Post by Jose Catre-Vandis on 2010-05-05
Which headers?

I tried linux-headers-2.26.32.22

but that didn't make any difference?

---

### Post by D-KICK on 2010-05-06
the initial installation went fine and nvidia was running ok with the 2.6.31-21 kernel.
today the kernel was updated to 2.6.31-22 and the XServer no longer starts. the same message in Xorg.0.log as described above.

(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/extra-modules/nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

how can I fix this?

---

### Post by dabl on 2010-05-06
You probably need to reinstall the driver.  This may help:

[http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

Don't worry about the "Kubuntu" aspect of it -- use gedit instead of kate, and "gdm" instead of "kdm", and everything else is the same.

---

### Post by Jose Catre-Vandis on 2010-05-06
Yep

See [here]("http://ubuntuforums.org/showpost.php?p=9249626&postcount=16") for fix

---

