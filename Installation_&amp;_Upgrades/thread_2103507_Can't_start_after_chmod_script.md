---
title: "Can't start after chmod script"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by Prostakov on 2013-01-10
I have Ubuntu 12.04.1 LTS with last update (3 day ago). It is desktop PC, but I have dokuwiki site on it. 2 days ago I load 20-30 dokuwiki arcticles on my HDD and run script for it with chmod. Unfortunes in this time electric power was off, and my PC was reboot. Now Ubuntu can not start. I see screen with Ubuntu logo and only it :(
I used USB HDD and boot this PC. I can copy / and /home dir by tar, and check by fsck and gparted but no find errors. I see syslog and have:
```
Jan 10 15:28:46 alex kernel: [    9.977958] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
Jan 10 15:28:46 alex kernel: [   11.857413] init: mounted-proc main process (349) terminated with status 126
Jan 10 15:28:46 alex kernel: [   11.857668] init: mounted-run main process (353) terminated with status 126
Jan 10 15:28:46 alex kernel: [   11.981918] Adding 8196092k swap on /dev/sdb7.  Priority:-1 extents:1 across:8196092k 
Jan 10 15:28:46 alex kernel: [   12.013691] init: container-detect pre-start process (354) terminated with status 126
Jan 10 15:28:46 alex kernel: [   12.339478] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 10 15:28:46 alex kernel: [   16.120680] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro
Jan 10 15:28:46 alex kernel: [   16.535937] EXT4-fs (sdb6): mounted filesystem with ordered data mode. Opts: (null)
Jan 10 15:28:46 alex kernel: [   16.547306] init: mounted-tmp main process (417) terminated with status 126
Jan 10 15:28:46 alex kernel: [   16.563257] init: Failed to spawn passwd main process: unable to execute: Permission denied
Jan 10 15:28:46 alex kernel: [   16.615242] init: dbus pre-start process (427) terminated with status 126
Jan 10 15:28:46 alex kernel: [   16.617896] init: Failed to spawn dbus post-stop process: unable to execute: Permission denied
Jan 10 15:29:32 alex kernel: [   63.138310] usb 7-4: USB disconnect, device number 2
Jan 10 15:29:34 alex kernel: [   64.696113] usb 7-4: new low-speed USB device number 3 using ohci_hcd
Jan 10 15:29:34 alex mtp-probe: checking bus 7, device 3: "/sys/devices/pci0000:00/0000:00:16.0/usb7/7-4"
Jan 10 15:29:34 alex mtp-probe: bus: 7, device: 3 was not an MTP device                                                                                                                                         
                                                              
```
I am sure problem with "Permission denied". Please, help me! What must I  make for repair my Ubuntu?

---

### Post by dino99 on 2013-01-10
booting in recovery mode then selecting "repair" should clean that issue (hit "shift" key at bios end process to get the grub menu on a single OS system)

---

### Post by Prostakov on 2013-01-10
Of course, I was try do it first time, system don't want start in safemode. Don't know why, but I saw only Ubuntu logo in safemode too. I understand, must show special menu with disk check, normal load and etc., but for my PC it is no true. After last grub update (about 1 month ago) my GRUB is no normal, russian font is broke, resolution too. But I don't make restarting system every day, because it is small problem for me. Please speak about repaire my system. Perhaps i can boot in safemode, what i must do for repair? File sytem fsck? I made, have not errors (see first post)

---

### Post by Prostakov on 2013-01-11
Repaired use it:
load by live-cd/usb:
```

cd $DIR_SRC
getfacl --recursive . >/tmp/acl
getfattr --recursive --dump . >/tmp/attr
cd $DIR_DST
setfacl --restore=/tmp/acl
setfattr --restore=/tmp/attr

```After restart and load in safe mode. Early I can not load in safemode, after it can.
Made .deb repair and FS check and resume load in normal
How is mark this thread like "DECIDED"?

---

