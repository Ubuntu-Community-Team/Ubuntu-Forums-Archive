---
title: "Desktop takes time to show up after entering password on login screen"
date: 2022-08-20
forum: Installation &amp; Upgrades
---

### Post by anspectrum on 2022-08-20
_**Problem:**_
After entering password at login screen, a blank screen appears with mouse cursor which we can move and after ~ 2 mins desktop shows up. This happens not only after booting but also if I logout and try to log back in. However it does not occur after waking up from suspend state. This started after I upgraded from 20.04 LTS to 22.04.1 LTS couple of days back.

_** System Description:**_
i[nxi output]("https://paste.ubuntu.com/p/mJ5zMtWnKQ/")

Syslog Output covering time (line 274-286)

[syslog]("https://paste.ubuntu.com/p/zcbMxTrvHh/")
[Screenshot]("https://postimg.cc/wtvC1hLz")

JournalCtl output covering time (line 149-160. The output is reversed)
[Journctl output]("https://paste.ubuntu.com/p/xtQp43cp3p/")
[ Screenshot]("https://postimg.cc/Wq6WW3gS")

_**Things I've tried:**_

1. Disabling Networking
2. Using xfce instead of lightdm
3. Reinstall mate DE
4. Creating another user account
5. Disabling VFS daemon
6. Hours and hours of Internet Searching and trying different solutions

Can someone take a look at the logs and point out something that can be the cause of this nuisance.

---

### Post by oldfred on 2022-08-20
My newest system, seems to have longer firmware time. But screen almost appears immediately.
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  systemd-analyze [/COLOR]
Startup finished in 10.932s (firmware) + 3.121s (loader) + 2.754s (kernel) + 1.383s (userspace) = 18.191s  
graphical.target reached after 1.262s in userspace


[/FONT]
```

I use Kubuntu and immediately uninstall all snaps.
I change multiple settings, details in these threads.
I have no bluetooth, nor is firmware in fwupdate, so no need for those.
Many users have mounts that may take longer, like network or NTFS or incorrect mount that has to timeout.

You can narrow down errors, but I still get a couple of pages of warnings & errors. Some are just repeating the mount command that has error in the options.
sudo egrep -i 'warn|error' /var/log/*g
journalctl -b -p 3
journalctl -b -p 4
man journalctl # for explanation of parameters

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by anspectrum on 2022-08-20
Thanks for the reply @oldfred. However, as I mentioned in my problem description that it happens also when I logout and try to log back in. So I suppose we can eliminate boot sequence. I had earlier checked[FONT=monospace][COLOR=#000000] outputs of systemd-analyze but [/COLOR][/FONT]didn't find any out of ordinary times there. Here is the output
```
systemd-analyze 
Startup finished in 5.517s (kernel) + 5.379s (userspace) = 10.897s 
graphical.target reached after 4.727s in userspace
```

More detailed logs outputs are linked under. All these logs are from the time when I logged out and logged back in. So no boot sequence is involved. Time of interest is Aug 20, 19:59:00 till Aug 20, 20:03:00 (~2-3 mins).
[sudo egrep -i 'warn|error' /var/log/*g]("https://paste.ubuntu.com/p/44R3tsb4Gf/")
[journalctl -b -p 3]("https://paste.ubuntu.com/p/zNfrRCZt6H/")
[journalctl -b -p 4]("https://paste.ubuntu.com/p/8jrrCHhpJw/")

In above logs you will see PCIe errors, which I had searched earlier that it was Wireless/Bluetooth device. Bluetooth I don't use so I already had it disabled using
```
sudo systemctl status bluetooth.service 
&#9675; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor pr>
     Active: inactive (dead)
       Docs: man:bluetoothd(8)
```

---

### Post by oldfred on 2022-08-20
See description on aer errors.
[https://gist.github.com/Brainiarc7/3179144393747f35e5155fdbfd675554](https://gist.github.com/Brainiarc7/3179144393747f35e5155fdbfd675554)
To remove all add this boot parameter: pci=noaer
But mentions setpci as better option?

---

### Post by anspectrum on 2022-08-21
AER is advanced reporting and setting that boot parameter is just suppressing error reporting and not fixing the actual cause. The other link from that github to setpci parameter is for suppressing that particular PCI instead of all devices. I had already tried AER boot parameter as well as pcie_aspm=off. They do suppress these log messages but don't fix the delay issue. I had my bluetooth already disabled in BIOS. But to further check it, I disabled WiFi as well in BIOS. After booting Login delay was still there but no AER reporting in syslog. 

I think syslog is unable to provide root cause for this delay. Is there some other logfile / command that can help in figuring out Desktop Session delay ?

---

### Post by oldfred on 2022-08-21
If Ubuntu it is a larger system for desktop.
I now use Kubuntu, and those with old systems use lightweight flavors. Those still work on newer systems, just may not have as many features with default install.
Your boot time is pretty fast.

---

