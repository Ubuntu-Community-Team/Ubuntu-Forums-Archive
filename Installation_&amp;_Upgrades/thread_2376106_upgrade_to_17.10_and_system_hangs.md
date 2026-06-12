---
title: "upgrade to 17.10 and system hangs"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by grandesso-giovanni on 2017-10-30
Hi,
after the update to Ubuntu 17.10, the system stops unexpectedly and does not respond. I have to press the shutdown button for a while to restart.
During hangs, the system-monitor program and the CPU History graph seems frozen.
With GNOME, the problem is most commonly encountered. With LXDE a little less but locks the same after 30/40 minutes.
Wayland disabled. Nvidia  nouveau driver installed (nvidia drivers purged from the system) ...  all previous tests did not improve the situation, even using the least  up-to-date kernel.
Configuration
Dell Precision M4500
NVIDIA Corporation GT215GLM [Quadro FX 1800M] (rev a2)
Kernel 4.13.0-16-generic

can I kindly ask some tips on how to solve it?
Thanks

---

### Post by perro.insano on 2017-10-30
Hi There! 

I have the same issue, I tried checking " journalctl " command getting the following errors a few moments before the freeze happened:
[B]
[I]oct 30 22:35:27 host gnome-session-binary[1801]: CRITICAL: Unable to create a DBus proxy for GnomeScreensaver: Error calling StartServiceByName for org.gnome.ScreenSaver: GDBus.Error:org.freedesktop.DBus.Err
oct 30 22:35:46 host kernel: nouveau 0000:01:00.0: msvld: unable to load firmware data
oct 30 22:35:46 host kernel: nouveau 0000:01:00.0: msvld: init failed, -19
oct 30 22:35:57 host pulseaudio[1892]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out[/I]

[/B]I will appreciate any help, I'll keep troubleshooting.!

Regards!

---

### Post by monkeybrain20122 on 2017-10-30
> **grandesso-giovanni said:**
> Hi,
after the update to Ubuntu 17.10, the system stops unexpectedly and does not respond. I have to press the shutdown button for a while to restart.
During hangs, the system-monitor program and the CPU History graph seems frozen.
With GNOME, the problem is most commonly encountered. With LXDE a little less but locks the same after 30/40 minutes.
Wayland disabled. Nvidia  nouveau driver installed (nvidia drivers purged from the system) ...  all previous tests did not improve the situation, even using the least  up-to-date kernel.
Configuration
Dell Precision M4500
NVIDIA Corporation GT215GLM [Quadro FX 1800M] (rev a2)
Kernel 4.13.0-16-generic

can I kindly ask some tips on how to solve it?
Thanks

Do a clean install, it is  much easier than trying to trouble shoot a bad upgrade where many things could have gone wrong. "upgrade" is always kind of fishy and even more so this time with the big changes from 17.04 to 17.10

---

### Post by grandesso-giovanni on 2017-10-31
Thank you for the reply. A clean installation is perhaps the best solution but reveals a less technical approach. The system lock prevents me from checking out what the killer program is or what the conflicting feature is.
I can understand a program that does not go but the total freezing of the computer makes the system unusable
I  simply asked for a set of checks to be carried out and then removed or  replaced the defective program (at least until correction).
at  the moment it seems that the Xorg server with the LXDE graphic  environment has no problems (it seems ... I'm still invesigating) and I  guess the cause is Gnome + Nvidia + Wayland (but I could get it wrong).
Thanks again.

---

### Post by mörgæs on 2017-10-31
> **grandesso-giovanni said:**
> I  guess the cause is Gnome + Nvidia + Wayland (but I could get it wrong).

No, I think you got it right. There are some posts in this thread indicating the same:
[https://ubuntuforums.org/showthread.php?t=2375077](https://ubuntuforums.org/showthread.php?t=2375077)

---

### Post by gauss4563 on 2017-11-03
Any idea why it happened and how to solve it?
I have the exact same problem with a bit different configuration, but still GNOME + nVidia + Wayland

Did using [COLOR=#000000]Xorg server with the LXDE graphic environment solve the problem?
By Xorg server - do you mean the Nouveau drivers for the nvidia GPU?[/COLOR]

---

### Post by monkeybrain20122 on 2017-11-03
> **gauss4563 said:**
> Any idea why it happened and how to solve it?
I have the exact same problem with a bit different configuration, but still GNOME + nVidia + Wayland

Did using [COLOR=#000000]Xorg server with the LXDE graphic environment solve the problem?
By Xorg server - do you mean the Nouveau drivers for the nvidia GPU?[/COLOR]

Option1: use Ubuntu 16.04 LTS. The interim releases have short support and often are buggy as they are basically tests gearing to the next LTS (there are some very good interim releases, but I would rate 17.10 on the buggy side though nothing show stopping)

Option2: don't use Wayland. There is a Ubuntu-xorg option in the login screen. Use that then you can use your driver and forget about Wayland (I am really not keen on the idea of making a beta software with limited features default, but then 17.10 is a beta ..)

Edited: in any case with so many changes in 17.10 "upgrade" is a bad idea, do a clean install if you must use 17.10

---

### Post by mörgæs on 2017-11-04
> **monkeybrain20122 said:**
> The interim releases have short support and often are buggy as they are basically tests gearing to the next LTS (there are some very good interim releases, but I would rate 17.10 on the buggy side though nothing show stopping)

Yes, Ubuntu 17.10 is buggy and should be considered a testing version but Xubuntu and Lubuntu 17.10 are highly stable. I haven't found any serious bugs in either of them.

---

### Post by gauss4563 on 2017-11-06
> **monkeybrain20122 said:**
> Option1: use Ubuntu 16.04 LTS. The interim releases have short support and often are buggy as they are basically tests gearing to the next LTS (there are some very good interim releases, but I would rate 17.10 on the buggy side though nothing show stopping)

Option2: don't use Wayland. There is a Ubuntu-xorg option in the login screen. Use that then you can use your driver and forget about Wayland (I am really not keen on the idea of making a beta software with limited features default, but then 17.10 is a beta ..)

Edited: in any case with so many changes in 17.10 "upgrade" is a bad idea, do a clean install if you must use 17.10

1. Had many problems with 16.04 and nvidia's GPU. The two just won't play together. 
2. Changing to Xorg indeed fixed the problem. 

It is a clean install.

---

