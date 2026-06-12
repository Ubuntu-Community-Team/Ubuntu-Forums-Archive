---
title: "Disabled nVidia Drivers in &quot;Additional Drivers&quot; now X doesn't start"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by gwohl on 2011-05-15
Hi guys!

I recently updated to 11.04, and in order to get Unity to work, I tried disabling my nVidia drivers in the "Additional Drivers" to see what results that would bring. Now X won't start, because it can't find the nvidia module. I'm new to Ubuntu and to GNOME/KDE environments, so I'm confused by what this function actually did. It didn't change my xorg.conf at all, it just seemed to delete it from my system!

Since I can't start X, I can't reopen that menu and re-enable the driver. I used apt-get to download the nvidia drivers again but no setup menu ever came up as I am used to when installing nvidia's drivers, so I'm not sure exactly what that particular apt-get package did. I'm afraid to stray out of the apt-get system out of fears related to past experiences with dependency issues and a broken system. But I'll do whatever I have to do to get X back up and running with the nvidia drivers!

Any suggestions would be much appreciated!


(Ubuntu Studio 11.04, X86-64, GeForce GTX 260)

---

### Post by MAFoElffen on 2011-05-15
> **gwohl said:**
> Hi guys!

I recently updated to 11.04, and in order to get Unity to work, I tried disabling my nVidia drivers in the "Additional Drivers" to see what results that would bring. Now X won't start, because it can't find the nvidia module. I'm new to Ubuntu and to GNOME/KDE environments, so I'm confused by what this function actually did. It didn't change my xorg.conf at all, it just seemed to delete it from my system!

Since I can't start X, I can't reopen that menu and re-enable the driver. I used apt-get to download the nvidia drivers again but no setup menu ever came up as I am used to when installing nvidia's drivers, so I'm not sure exactly what that particular apt-get package did. I'm afraid to stray out of the apt-get system out of fears related to past experiences with dependency issues and a broken system. But I'll do whatever I have to do to get X back up and running with the nvidia drivers!

Any suggestions would be much appreciated!


(Ubuntu Studio 11.04, X86-64, GeForce GTX 260)
Refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Shortcut to get you back:
Reboot
Press shift key and get to boot menu
Press "e"
Will bring you into edit mode of the linux boot item...
Move to the line starting with
```

linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro   quiet splash vt.handoff=7

```[COLOR=Red][COLOR=Black]
Edit it to read (look at end)
[/COLOR][/COLOR]```
inux    /boot/vmlinuz-2.6.38-8-generic root=UUID=32939def-1f4a-4134-9b56-bed2319a9216 ro [COLOR=Red]nosplash nomodeset text[/COLOR]

```[COLOR=Red][COLOR=Black]
Press <cntrl><x>
Will bring you to a text console login.  Enter userid and password.
```

cd /etc/default/
sudo vi grub

```Add this line
[/COLOR][/COLOR]```
GRUB_GFXPAYLOAD=text

```Save and exit, then...
[COLOR=Red][COLOR=Black]```

sudo update-grub
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot

```That should reboot you into a mode that is going to tell the kernel to ignore graphics calls (mode sets) from grub and let Xorg use the nvidia drivers without interference from external calls...
[/COLOR][/COLOR]

---

### Post by gwohl on 2011-05-22
Thank you for your response. Unfortunately, while following your directions, I get stuck at "sudo nvidia-xconfig" because it returns "command not found" when I try to run it. Any suggestions?

Thanks again!

---

### Post by robbiemacg on 2011-05-22
This maybe a silly question, but did you receive any warnings or unusual dialogues following the **sudo apt-get install nvidia-current **command? Have you installed applications or drivers via CLI in the past?

---

### Post by MAFoElffen on 2011-05-22
> **gwohl said:**
> Thank you for your response. Unfortunately, while following your directions, I get stuck at "sudo nvidia-xconfig" because it returns "command not found" when I try to run it. Any suggestions?

Thanks again!
If you got "command not found" on "sudo nvidia-xconfig"... then the previous "sudo apt-get install nvidia-current" failed or the installed package that is already there has problems, because "that is" a part of that package.

In that case, try this and see how it works: (paying attention to the messages)
```

sudo apt-get remove --purge nvidia*
sudo apt-get install nvidia-current
sudo nvidia-settings
sudo nvidia-xconfig

```

---

