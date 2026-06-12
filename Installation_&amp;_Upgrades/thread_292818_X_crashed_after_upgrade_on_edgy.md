---
title: "X crashed after upgrade on edgy"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by oskar-swe on 2006-11-04
Hi, people.

I have an nvidia 6800 pcie.

I just upgraded my edgy install and I think the nvidia-drivers was part of the update, so i restarted X with ctrl-alt-bs and it crashed.

My X is now fubar. I tried to sudo apt-get remove nvida-glx and nvidia-kernel-common and then reinstalling them. But when I run sudo nvidia-glx-configure enable I get weird error messages about md5sums and what not. Anyway, i followed the instructions about the md5sums. Now i get weird error messages like:

First the install seems to be going well, then I get this message:

"dexconf:error:this program does not know how to configure the "10 shared/default-x-server doesn't exist" X server.


now all i get is:
"/etc/X11/XF86Config-4 or /var/lib/X11/XF86Config-4.md5sum are missing from your system. Please be sure that your xserver package is installed correctly"

Please help me. It feels hopeless, and I think I'm about to cry :(

---

### Post by oskar-swe on 2006-11-04
Someone, please?

---

### Post by pdub on 2006-11-04
Try switching to the nv driver just to see if X is OK.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

**sudo vi /etc/X11/xorg.conf**

find the line that says:

```
Driver		"nvidia"
```

and change it to 

```
Driver		"nv"
```

in vi, use the **i** key to move to insert mode, then **backspace** out the idia, then hit **esc**, then **:wq** to quit and save.

Then startx

If this fails, please post the last few pages of /var/log/Xorg.0.log

---

### Post by oskar-swe on 2006-11-04
Thank you for trying! I solved it myself, however. Somehow I'd f:ed my entire xserver up, so I did $ sudo synaptic remove xserver-xorg then $ sudo synaptic install xserver-xorg. Then $ sudo dpkg-reconfigure xserver-xorg.

This worked wonders. I guess i could have just used a backup version of xorg.conf, instead of the reconfigure.

It still sucks that an automatic glx update broke my X. Very little has changed with open gl and X since my last GNU/Linux adventure with red hat back in 2000. It's too bad.

---

