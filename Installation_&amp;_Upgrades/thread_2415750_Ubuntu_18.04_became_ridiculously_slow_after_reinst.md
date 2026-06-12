---
title: "Ubuntu 18.04 became ridiculously slow after reinstall"
date: 2019-03-30
forum: Installation &amp; Upgrades
---

### Post by khalifa97 on 2019-03-30
My PC got super slow about I had reinstalled it.
Here is how my PC specs are like:
```
8GB RAM
128SSD(Windows), 60GB (Linux) and 940 GB HDD
Nvidia GTX MX150
Intel(R) Core(TM) i7-8550U CPU @ 1.80G
```

and that's the output of the following commands:
```
$ systemd-analyze blame
```

```
  29.827s dev-sda6.device
         23.895s systemd-journal-flush.service
         22.245s dev-loop6.device
         21.042s dev-loop4.device
         20.921s dev-loop5.device
         20.537s systemd-udevd.service
         20.219s dev-loop0.device
         19.514s dev-loop1.device
         19.294s dev-loop3.device
         19.224s dev-loop2.device
         17.709s plymouth-quit-wait.service
          7.634s NetworkManager-wait-online.service
          6.896s ModemManager.service
          6.858s plymouth-start.service
          6.125s snapd.service
          5.874s gpu-manager.service
          5.868s udisks2.service
          5.316s bolt.service
          4.976s accounts-daemon.service
          3.837s NetworkManager.service
          3.600s polkit.service
          3.181s networking.service
          2.838s networkd-dispatcher.service
```

```
$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @58.601s
&#9492;&#9472;multi-user.target @58.601s
  &#9492;&#9472;kerneloops.service @48.472s +124ms
    &#9492;&#9472;network-online.target @48.449s
      &#9492;&#9472;NetworkManager-wait-online.service @40.814s +7.634s
        &#9492;&#9472;NetworkManager.service @36.975s +3.837s
          &#9492;&#9472;dbus.service @35.828s
            &#9492;&#9472;basic.target @35.585s
              &#9492;&#9472;sockets.target @35.585s
                &#9492;&#9472;snapd.socket @35.533s +52ms
                  &#9492;&#9472;sysinit.target @35.532s
                    &#9492;&#9472;apparmor.service @33.370s +2.161s
                      &#9492;&#9472;local-fs.target @33.272s
                        &#9492;&#9472;run-user-121.mount @44.434s
                          &#9492;&#9472;local-fs-pre.target @6.133s
                            &#9492;&#9472;keyboard-setup.service @3.976s +2.156s
                              &#9492;&#9472;systemd-journald.socket @3.940s
                                &#9492;&#9472;system.slice @3.940s
                                  &#9492;&#9472;-.slice @3.927s
```


```
$ systemd-analyze
Startup finished in 6.573s (firmware) + 3.282s (loader) + 8.883s (kernel) + 1min 1.758s (userspace) = 1min 20.497s
graphical.target reached after 58.601s in userspace
```

sometimes It takes much much longer than this the time it took a whole 3.5mins to boot.
P.S: When I reinstalled I used the option "Erase Ubuntu 18.04 and Install a new one" not the something else option

Anyways, thank you for your time and I would be quite grateful if anyone could help

---

### Post by TheFu on 2019-04-01
It is just slow to boot or slow all the time?

There have been multiple fixes for snaps being terribly slow. [https://www.omgubuntu.co.uk/2019/03/the-cause-of-slow-snap-app-startup-times-has-been-identified](https://www.omgubuntu.co.uk/2019/03/the-cause-of-slow-snap-app-startup-times-has-been-identified) Don't know when those will be available in 18.04.  I've removed all support for snaps in my 16.04 setups for a few reasons, performance is just 1, but RAM utilization was a key consideration and broken functionality were also important.  I'm hopeful that snaps will be useful for many aspects, but using snaps for everything is like saying that chocolate ice cream should be placed on top of everything you eat too.  IMHO.

Whenever a system is slow, check the system log files for any issues. A failing SSD or HDD or cable or PSU can slow a system down too.

Is is always faster to have fewer USB devices connected too.  I had a 35-in-7 USB reader and my boots were taking over 3 minutes.  Just by unplugging the USB2 device, boots dropped to under 30 seconds.  The issue was that systemd wanted to check each device slot for media to boot.  I removed it from the boot order and it still wanted to check them all. Never figured out why.  This was a front-panel device with USB2, USB3, USB3.1 and support for basically every sort of memory card slot.  The USB3 ports didn't have any impact on boot times. They are still connected and working great. The problematic 16.04 server today:
```
$ systemd-analyze 
Startup finished in 6.353s (kernel) + 22.403s (userspace) = 28.757s
```
Since I don't reboot it all that often, a 30 sec boot time doesn't matter to me. I did go through a remove all the services from the critical-chain that weren't being used. It has been a few months, so I don't remember them all. It is basically down to networking, LVM, and cg groups at this point. I use LVM, if you don't, then it is safe to remove that from the startup dependencies.  Also, I don't allow normal users to mount things, so udisks/gdisks isn't allowed and I don't use network manager ... ever.

We all have different needs from our systems, so take careful notes about everything you disable and how it impacts startup.  You can always delay the startup for some things, if you need it, just not at boot, but then you'll have to decide which dependencies make sense and alter those in the systemd init files.

---

