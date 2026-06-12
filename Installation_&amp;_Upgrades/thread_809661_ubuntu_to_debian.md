---
title: "ubuntu to debian"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by KazukiFlame on 2008-05-27
i'm kinda new to this linux, n i'm loving linux. i've installed ubuntu 8.04 lt less than a month. this morning i got a update from update manager that required me to restart after the the update. weird part is that after restarting the machine, in grub instead of booting to ubuntu, it says booting to debian. is that normal???

---

### Post by bwhite82 on 2008-05-27
The grub screen says Debian? Or on the splash screen? At any rate, Ubuntu is based off of Debian unstable so there's no cause for concern. You don't have any Debian repos enabled do you?

---

### Post by Rallg on 2008-05-27
Ubuntu is based on Debian. Although I haven't specifically seen any message saying that my system boots to Debian, there are a number of packages that carry the "debian" label.

If your systems boots and functions, let it slide. If it doesn't, then I would guess that somehow, you got a non-standard or corrupted file mixed in.

If your system does boot, do you see a large "Ubuntu" label in orange, with a moving slider underneath? It's the first thing you should see other than text.

---

### Post by KazukiFlame on 2008-05-27
its the grub menu listing i can choose bootups.
what i used to have ubuntu is now debian instead...
for example b4 i had ubuntu, 2.xxxxxx (recovery)
now it is debian, 2.xxxxx (recovery)

i don't remember the the digits after the ubuntu/debian after that exactly. but i think u get my idea. the orange screen with ubuntu and a sliding bar until the login, aren't those supposed to be splash screens? like i can replace those splash screens into any crap i like although i haven't bothered to.

well it does boot up, n i haven't seen anything exactly out of the ordinary other than that, but i'd only had 10 minutes to find out whats going on b4 i had to jet off for work.

---

### Post by bwhite82 on 2008-05-27
Hmm..very odd indeed. Please post the result of the terminal command:

> cat /boot/grub/menu.lst | grep kernel

---

### Post by KazukiFlame on 2008-05-27
it says:

```
# kernel	/vmlinuz root=/dev/hda2 ro
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
title		Debian GNU/Linux, kernel 2.6.24-17-generic
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=79faeb0f-2159-49de-b112-401dc8a66112 ro quiet splash
title		Debian GNU/Linux, kernel 2.6.24-17-generic (recovery mode)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=79faeb0f-2159-49de-b112-401dc8a66112 ro single

```

---

