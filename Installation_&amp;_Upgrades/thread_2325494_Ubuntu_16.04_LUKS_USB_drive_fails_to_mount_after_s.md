---
title: "Ubuntu 16.04 LUKS USB drive fails to mount after suspend"
date: 2016-05-23
forum: Installation &amp; Upgrades
---

### Post by bfeltman on 2016-05-23
Hi,

I have ThinkCentre-M73 and recently updated to 16.04 from 14.04 (which wasn't painless of course...) but have problem with encrypted USB drive 750 GB with LUKS. 
After resuming PC from suspend I can't unlock the drive because I kept asking me for password and shows error message that other device already exists.

Disks shows double drives. 1 mounted on /dev/sdc and second... on /dev/mapper/....
[IMG]http://i.imgur.com/nN57ISR.png[/IMG]

```
Error unlocking /dev/sdc1: Command-line `cryptsetup luksOpen "/dev/sdc1" "luks-8aa314a8-8f01-4f27-bfdf-4eaa142e0585" ' exited with non-zero exit status 5: Device luks-8aa314a8-8f01-4f27-bfdf-4eaa142e0585 already exists.
```

After reboot USB drive mounts properly after entering password.

```
4.5.2-040502-generic
```

---

### Post by Suor on 2016-10-21
Have the same issue. Used dmsetup to manually remove device earlier, but it doesn't work in latest Ubuntu.

---

### Post by oliverlorenz on 2016-11-17
I have the same problem. Anyone an idea?

---

### Post by kevin.s2 on 2017-01-05
Same issue here, running 16.10. Would love to hear if anyone has figured this out. I'm actually booting from the usb that won't unlock, so am forced to reboot if my computer suspends.

---

