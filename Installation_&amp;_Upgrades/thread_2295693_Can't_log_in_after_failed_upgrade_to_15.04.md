---
title: "Can't log in after failed upgrade to 15.04"
date: 2015-09-20
forum: Installation &amp; Upgrades
---

### Post by timswait on 2015-09-20
I got part way through an upgrade to 15.04 when we had a power cut to our street. The power was only off for a few seconds but it rebooted the computer when it was only partially upgraded. I've managed to use recovery mode to complete the installation (or I think it is). So now when I type ```
dpkg --configure -a
``` nothing happens and when I type apt-get upgrade it says the system is up to date with 0 packages need updating, installing or removing.
However when I try to boot the computer it hangs. Grub comes up and then I get a brief message appear saying "starting version 219" but then I just get a white screen.
I've tried ```
systemctl enable sddm.service -f
``` from recovery mode but I get an error message ```
Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1)
``` repeated three times. I've read that this can be caused by drives referred to in fstab, so I looked in that and commented out the only drive in there which wasn't already commented out. This made no difference to booting up, still just get the white screen and it hanging at that point.
Since editing fstab to comment out that drive it now doesn't seem possible to mount the file system as read/write from recovery mode. Now when I try to edit fstab it says that it's read only and if I run ```
systemctl enable sddm.service -f
``` I get the same error as before and also ones saying that it can't do various things because it's a read-only filesystem. So now I not only have a problem with my display manager not working but I also have a problem with the filesystem being mounted as read only, and since fstab is on that filesystem I can't even edit it to change it back!
What can I try now?

---

### Post by CantankRus on 2015-09-20
Try booting in [**_[COLOR="#B22222"]recovery mode[/COLOR]_**]("https://wiki.ubuntu.com/RecoveryMode").
The enable networking option doesn't work for me.
Follow the steps in the above link to mount "/" as read-write.
Then as a last step enable networking with...
```
dhclient [COLOR="#FF0000"]eth0[/COLOR]
```
where [COLOR="#FF0000"]eth0[/COLOR] is your network interface. 
May be **wlan0** for wireless.

Commands to run in recovery mode:
```
dpkg --configure -a
apt-get install -f
apt-get update && apt-get upgrade
apt-get dist-upgrade
```

If I install sddm in my regular 15.04 Ubuntu install I get a blank white screen.
If you still get this you could try installing another display manager like lightdm or gdm.
```
sudo apt-get install lightdm
```

You may be prompted to choose a new display manager during install, if not...
```
sudo dpkg-reconfigure lightdm 
```
Use the arrow keys to select and tab to move to the "ok" confirmation and press Enter.


Still no luck try purging sddm after installing another display manager...
```
sudo apt-get purge sddm
```

---

### Post by timswait on 2015-09-21
Thanks for that, maybe some improvement. I had already installed all the upgrade packages, so the computer is fully upgraded to 15.04, there are no packages showing as still to install.
I already had lightdm installed, so reconfigured and selected it as my default. That time on booting up I got the Kubuntu logo but then it just dropped into a command line log on, the filesystem was still mounted as ro. So I went back into recovery mode, edited fstab to remove the commenting out I had done.
It now gets further into booting, I get the Kubuntu logo appearing and glowing pulsing, but now I just get as far as a black screen with a white mouse cursor (that moves with the mouse) and no more.
I've tried purging sddm. I've even tried purging lighdm and re-installing sddm, and then removing sddm and re-installing lightdm.
It seems whenever I try to install any display manager I get the same error at the end:
```
Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1)
```

---

### Post by timswait on 2015-09-21
Looks like I've cracked it. It appears that half of kde didn't get installed, so when I did ```
apt-get install plasma-desktop
``` it installed a whole load of packages and now boots up (using sddm, I did eventually get lightdm to get as far as the login screen, but it then tried to load unity, which wasn't there so it gave up there).

---

