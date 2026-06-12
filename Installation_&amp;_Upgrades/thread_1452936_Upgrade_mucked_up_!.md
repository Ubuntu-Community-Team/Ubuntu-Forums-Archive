---
title: "Upgrade mucked up !"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by dancq on 2010-04-12
Hi there, today i decided to take upgrade to 10.04 lucid lynx ( for i wanted to sync my iPod touch). I left it to do its thing, an when it had done upgrading it was just sitting there, switched off! When I turned it on, and loaded the GRUB, it still came up with ubuntu 9.10. I just booted up as normal, but it got nowhere past the black screen before the usplash. I turned my laptop off, and entered into the recovery mode. It loaded all the files, and then eventually got to a dead end; the code read

```
/usr/bin/timidy: error while loading shared libraries: usr/lib/libX11.so.6: invalid ELF header [fail]
```I have no clue what do do and have some very important stuff on this laptop. In the ideal world i would like to do a fresh install, but keep all my applications and files. 

My specs: Compaq Presario, V6500, AMD turion 64 X2 (1.9 ghz), 2g ram, 120g hard drive, no cd drive (broke).

Thanks for any help Dan,

---

### Post by khelben1979 on 2010-04-12
Maybe this can help you: [Extracting data from a dead laptop with a laptop hard drive adapter]("http://articles.techrepublic.com.com/5100-10878_11-5160538.html").

So maybe you have a friend or that you yourself have an desktop PC where you can connect it to and access the data from another Linux system on a different harddrive.

Next time I would recommend doing backups before trying out a beta version of Ubuntu.

---

### Post by dancq on 2010-04-12
Thanks alot, will look into it and yeah was a bit stupid of me it was a spur of the moment thing as i was leaving.

Dan

---

### Post by bcbc on 2010-04-12
This may be a long shot, but after you are done backing up your data, try chroot'ing into your 'lucid' and running updates. I had a working beta1 with upgrades, but for some reason a fresh beta2 install just kept crashing. I did the chroot thing, then ran
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
and it's booted fine since. (Having said that - I don't know what state your system is in with a failed upgrade from karmic - but it's worth a shot if you can recover your system).

---

