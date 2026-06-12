---
title: "Boot not working after grub reinstall cleared by windows instal"
date: 2010-03-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alex88 on 2010-03-07
Hi, i was using ubuntu 10.04 x64, it was working fine, then i've installed windows 7 on the other partition, then i've booted with livecd, done
```
sudo grub-install --root-directory=/media/mounted /dev/sda
```
it says no errors, so i've rebooted, now for the first time it said "mount time in the future, fixed" or something like that. But after /dev/sda1 clean the boot wont continue. It just stay there, ctrl-alt-canc make it restart but it still hang there on the next reboot. Any clue? i've tried also to do a fsck -f /dev/sda1 from live cd, but no luck..

---

### Post by KrazyPenguin on 2010-03-07
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by alex88 on 2010-03-07
> **KrazyPenguin said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

so? i've reinstalled grub in that way... but the problem is now after the grub.. in linux boot..

---

### Post by philinux on 2010-03-07
> **alex88 said:**
> so? i've reinstalled grub in that way... but the problem is now after the grub.. in linux boot..

You might find this works

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

---

### Post by VMC on 2010-03-07
> **alex88 said:**
> so? i've reinstalled grub in that way... but the problem is now after the grub.. in linux boot..

@alex, Run *boot_info_script*, then output the *RESULTS.txt* file back here so we can get a clearer picture of what's going on. 

You can get it using my "blue" link below.

---

### Post by alex88 on 2010-03-07
> **VMC said:**
> @alex, Run *boot_info_script*, then output the *RESULTS.txt* file back here so we can get a clearer picture of what's going on. 

You can get it using my "blue" link below.

here is the file..

PS: dunno if it's useful, these are last lines of /var/log/dmesg

```
root@ubuntu:/mnt/var/log# tail dmesg
[   23.465030] type=1505 audit(1267517520.492:6):  operation="profile_replace" pid=963 name="/sbin/dhclient3"
[   23.465667] type=1505 audit(1267517520.492:7):  operation="profile_replace" pid=963 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   23.466010] type=1505 audit(1267517520.492:8):  operation="profile_replace" pid=963 name="/usr/lib/connman/scripts/dhclient-script"
[   23.467715] type=1505 audit(1267517520.492:9):  operation="profile_load" pid=964 name="/usr/bin/evince"
[   23.468654] type=1505 audit(1267517520.492:10):  operation="profile_load" pid=966 name="/usr/lib/cups/backend/cups-pdf"
[   23.469413] type=1505 audit(1267517520.492:11):  operation="profile_load" pid=966 name="/usr/sbin/cupsd"
[   23.770135] RPC: Registered udp transport module.
[   23.770137] RPC: Registered tcp transport module.
[   23.770138] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   23.793507] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
```

---

### Post by alex88 on 2010-03-07
> **philinux said:**
> You might find this works

[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)


tried that way, no luck, btw the problem is after grub! It start loading os, but after fsck it remain idle.

---

### Post by ranch hand on 2010-03-07
> **vmc said:**
> @alex, run *boot_info_script*, then output the *results.txt* file back here so we can get a clearer picture of what's going on. 

You can get it using my "blue" link below.
+485

---

### Post by VMC on 2010-03-07
@alex, It appears your missing a swap file. Do you know if you had one before? 'free' will tell you how much free ram you have. You will notice no swap space.

```
/dev/sda1                  63    78,124,094    78,124,032  83 Linux
/dev/sda2    *     78,125,056    78,329,855       204,800   7 HPFS/NTFS
/dev/sda3          78,329,856   390,716,864   312,387,009   7 HPFS/NTFS

```
Also, can you boot Windows?

---

### Post by alex88 on 2010-03-08
I never had a swap space, i've 2gb of ram and it was always enough, btw, yes i can boot windows and i think i'll reinstall ubuntu, i need it working.. :S

---

### Post by mdurham on 2010-03-08
> **ranch hand said:**
> +485

Hey ranch hand, what does that mean?

---

### Post by VMC on 2010-03-08
> **mdurham said:**
> Hey ranch hand, what does that mean?

Usually if someone says "+1" , they tend to agree with previous post. I'm guessing RH enthusiastically agrees - 484 times more :)

---

### Post by ranch hand on 2010-03-08
YUP the boot info script is a must on every computer.  Use it, if only for your own entertainment.

---

### Post by mdurham on 2010-03-08
> **VMC said:**
> Usually if someone says "+1" , they tend to agree with previous post. I'm guessing RH enthusiastically agrees - 484 times more :)

That's certainly enthusiastic then!
Cheers, Mike

---

### Post by alex88 on 2010-03-15
ok same problem again...reformatting again..damn..](*,)

---

