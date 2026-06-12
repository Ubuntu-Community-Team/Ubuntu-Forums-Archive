---
title: "Beagleboard with ARM processor: How to change the kernel boot order in Ubuntu 14.04"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by xxlray on 2014-05-28
I use Ubuntu 14.04 and need a custom kernel as I am running it on a beagleboard. The standard kernel in this board is (currently) vmlinuz-3.8.13-bone54 but I need a modified one that loads the virtual ethernet module to be able to run linux containers.
I compiled a new kernel and tried  to install it by```
dpkg -i ~ubuntu/stable-kernel/deploy/linux-image-3.9.11-x5_1.0cross_armhf.deb
dpkg -i ~ubuntu/stable-kernel/deploy/linux-headers-3.9.11-x5_1.0cross_armhf.deb
```
Now /boot/ contains vmlinuz-3.9.11-x5 and vmlinuz-3.8.13-bone54 (amongst other stuff). Unfortunately the system still boots vmlinuz-3.8.13-bone54 by default.```
$ uname -r
3.8.13-bone54
```
 How do I change the default kernel in Ubuntu 14.04 as there seems to be no update-grub and no /etc/default/grub any more?

---

### Post by Bucky Ball on 2014-05-28
Well,

```
sudo update-grub
```

... is still alive and well (unless you're using Lilo or something else rather than grub of course). Try running that in a terminal. Post any error message back here.

---

### Post by sudodus on 2014-05-28
You can

1. copy and paste (with superuser privileges) the relevant

```
menuentry {
...
...
...
}

```
section in **/boot/grub/grub.cfg**

into (the end of)** /etc/grub.d/40_custom**

2. rename /etc/grub.d/40_custom to a name that will be found before 10_linux, for example

```
sudo mv /etc/grub.d/40_custom /etc/grub.d/07_custom
```

3. Make it active (copied into a new version of /boot/grub/grub.cfg) with the command

```
sudo update-grub
```

---

### Post by xxlray on 2014-05-28
```
$ sudo update-grub
sudo: update-grub: command not found

$ sudo ls /boot/grub
ls: cannot access /boot/grub: No such file or directory
```
So maybe the standard image for this board uses a different boot manager. Is there a way to find out?

---

### Post by sudodus on 2014-05-28
Are you running the system you are asking about, or are you running from a live system?

What output do you get from the following commands?

```
sudo find / -name grub
```
```
sudo find / -name grub.cfg
```

---

### Post by sudodus on 2014-05-28
Maybe you are booting with lilo? How did you install Ubuntu? What image did you use? Is there some information about it, where you found it? Or is it a dual boot or wubi system with Windows and booting somehow via Windows?

---

### Post by xxlray on 2014-05-28
The beagleboard is somehoe similar to a Rasberry Pie (if that information helps) and has an ARM processor. I installed the pre-compiled OS image from [http://elinux.org/BeagleBoardUbuntu#Trusty_14.04](http://elinux.org/BeagleBoardUbuntu#Trusty_14.04)
Afterwards I log in via SSH, download kernel sources, modify the .config, compile the kernel and install the resulting .deb packages like described above.

The find commands don't bring up any result.

---

### Post by sudodus on 2014-05-28
I think you have another boot loader. I have no own experience of lilo, but you can search for it in a similar way as you were searching for grub

```
sudo find / -name "lilo*"
```

---

### Post by xxlray on 2014-05-28
Nope - lilo content seems to only be in some linux containers. I will try to reach out to the developers.```
$ sudo find / -name "lilo*"
/var/cache/lxc/trusty/rootfs-armhf/usr/share/vim/vim74/syntax/lilo.vim
/var/lib/lxc/testcontainer1/rootfs/usr/share/vim/vim74/syntax/lilo.vim
```
Could there be another boot loader? The OS is on a micro SD card if that helps.

---

### Post by sudodus on 2014-05-28
Yes, probably there is another boot loader. I must admit that I don't know. Let us hope that someone who knows can chip in and help you. Maybe it helps to attract people who know, if I edit the title of your thread to mention beagleboard and ARM.

---

### Post by xxlray on 2014-06-02
It seems to use a bootloader called u-boot but I couldn't find out how to define the proper kernel for boot yet.

---

