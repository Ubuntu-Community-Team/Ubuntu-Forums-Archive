---
title: "[SOLVED] Ubuntu 20.04 Slow boot"
date: 2020-09-20
forum: Installation &amp; Upgrades
---

### Post by tuxxtuta on 2020-09-20
Hey there,

I had upgraded (clean install ) from 19.04 to 20.04 the last week and i have since then very slow times at boot (almost 2 minutes)

I was seeing the check disks at the loading screen first and i disabled it like this 
```
fsck.mode=skip grub.cfg just before quiet splash
```


I don't know if you need something from my hardware specs, the pc is 1 years old , Ryzen 5 3400G , no problems at all with the 19.04 distro 

So here is the output of systemd-analyze

```

systemd-analyze
Startup finished in 15.415s (firmware) + 4.265s (loader) + 3.541s (kernel) + 1min 39.750s (userspace) = 2min 2.973s 
graphical.target reached after 1min 39.734s in userspace

```

and here the critical-chain
```

graphical.target @1min 39.734s
&#9492;&#9472;multi-user.target @1min 39.734s
  &#9492;&#9472;kerneloops.service @1min 36.919s +21ms
    &#9492;&#9472;network-online.target @1min 36.899s
      &#9492;&#9472;NetworkManager-wait-online.service @1min 30.601s +6.296s
        &#9492;&#9472;NetworkManager.service @1min 30.367s +233ms
          &#9492;&#9472;dbus.service @1min 30.364s
            &#9492;&#9472;basic.target @1min 30.357s
              &#9492;&#9472;sockets.target @1min 30.357s
                &#9492;&#9472;snapd.socket @1min 30.355s +697us
                  &#9492;&#9472;sysinit.target @1min 30.349s
                    &#9492;&#9472;systemd-timesyncd.service @1min 30.280s +69ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @1min 30.241s +37ms
                        &#9492;&#9472;systemd-journal-flush.service @301ms +320ms
                          &#9492;&#9472;systemd-journald.service @220ms +79ms
                            &#9492;&#9472;systemd-journald.socket @217ms
                              &#9492;&#9472;system.slice @214ms
                                &#9492;&#9472;-.slice @214ms

```

Any thoughts where to search next ?

Many thanks in advance

---

### Post by oldfred on 2020-09-20
Wide variety of issues.

HDD or SSD?
Is UEFI firmware & if SSD, the SSD firmware up to date?

Do all UUIDs in fstab match actuall partitions you have, often a reformatted swap changes and causes issues. Compare UUIDs, may sure all are valid.
cat /etc/fstab
lsblk -o NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE,MODEL, uuid | egrep -v "^loop"

Are you using snaps. Many are now installed by default, instead of .deb. But snaps are slower. 
Since these posts they have improved snaps, but still not as fast. I uninstall all snaps and install only .deb versions using snaptic or command line.

Other issues:
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

Changes I make:
turned off NetworkManager-wait with systemctl
changed from quiet splash to noplymouth, will see boot process rather than Ubuntu logo
sudo apt install libblockdev-crypto2 libblockdev-mdraid2
turned off printer when rebooting
removed snaps

Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
If UEFI firmware update not supported (yet):
sudo apt-get purge fwupd

---

### Post by tuxxtuta on 2020-10-11
Sorry for the late response

Thank you for your reply,
YES! It was a wrong entry in my fstab , i thought that it was my HDD and i had comment the entry but the problem was not fixed , i found that there was an entry from the installation , i removed it and everything works perfect

thx again for your time :)

---

