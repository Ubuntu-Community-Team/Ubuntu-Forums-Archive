---
title: "kdm doesn't load after upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Tiny Grasshopper on 2008-11-01
I believe that my hardy install had the kubuntu-kde4 packages installed as well, but I wasn't using them and switched back to the kdm login screen.

I upgrade, it apparently goes smoothly up until i reboot then I get this error message:

grep: /usr/lib/kde4/etc/kde4/kdm/kdmrc: No such file or directory
Not starting K display manager (kdm-kde4); it is not the default display manager

which is obvious since there's just kde 4 now and it's just called kdm not kdm-kde4

I was about to start poking about at the init script but found [this thread]("http://ubuntuforums.org/showthread.php?p=5987579") which is pretty much the same problem and the described fix makes perfect sense, uninstall kdm-kde4 and reinstall kdm with these commands.

sudo aptitude purge kdm-kde4
sudo aptitude reinstall install kdm
sudo depmod -a
dpkg-reconfigure kdm

and then I reboot and I don't get the error message anymore but kdm still hasn't come up

---

### Post by Tiny Grasshopper on 2008-11-07
I've also retested this with clean installs of Kubuntu 8.10 32-bit and 64-bit and Ubuntu 64-bit and 32-bit. In all four occasions, kdm and gdm did not appear.

I've observed the following bugs [275379]("https://bugs.launchpad.net/bugs/275379"), [294405]("https://bugs.launchpad.net/bugs/294405"), [282328]("https://bugs.launchpad.net/bugs/282328"), that seem related to what I'm going through but there are some differences and I've filed a separate bug [295160]("https://bugs.launchpad.net/bugs/295160").

Can anyone please assist me in any way with this?

---

### Post by aseemrane on 2008-12-08
I upgraded my Kubuntu 8.04 and faced the same issue. I have not upgraded it to 8.10 yet. When I selected the kernel version 2.6.24-21 from the Grub menu everything was fine again. 
Now I have changed the default selection in the Grub menu to select 2.6.24-21 instead of 2.6.24-22. But I am looking for a permanent solution.

It doesn't seem like a KDM problem but a driver issue as you might have already noticed

---

