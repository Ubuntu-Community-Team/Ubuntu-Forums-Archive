---
title: "Install 32 bit simcity in 64 bit Ubuntu"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by jobje on 2011-05-18
Hello,

I'm new to linux and recently installed Ubuntu 11.04 64bit. Now I have the game "Simcity 3000 unlimited" which is supposed to be linux compatible. Now I have come to the point where I should install the game with the following command "sudo sh /media/cdrom/setup.sh" but when I try this it gives me the following error "This installation doesn't support unknown on Linux / x86_64"

Now I figured this old game doesn't support 64bit. My question is, is there any way to install it? Like you can install 32bit windows software on 64bit windows machine.

Thanks

---

### Post by dino99 on 2011-05-18
32 bits apps on 64 bits system need "ia32libs" installed first

sudo apt-get install ia32libs

---

### Post by Sal Z on 2011-05-18
If I remember well, the game itself it actually is a static linked executable, it should require some reaaaaally old version of libc, tough.

alternatives:

1) If you have it, install 32bit wine and run the windows version of the game. it should run quite well on it.

2) try chrooting an old 6.06 32bit ubuntu installation, but I have no idea if it's feasible while running a 64 bit kernel...

3)if chrooting is not possible, you could try running some old linux version on virtualbox/vmware, the overhead shouldn't be too much taxing on a modern cpu, especially if you streamline the distro just to the bare needs to run the game.

---

### Post by jobje on 2011-05-18
Thanks for the replies.

@dino99:
I installed it but it still didn't work. It was "ia32-libs" by the way ;)

@Sal Z
From what I understand from you it isn't possible to run it directly on my version of Ubuntu. Unfortunatly I don't have the Windows version. I might try the VMware solution someday. But for now thats to much hassle. I was hoping it would run on my installation ;)
Thanks anyway :)

---

### Post by Sal Z on 2011-05-18
Well, it's not technically impossible, but it would require a lot of old packages, most of which have been superseded and would break your configuration if they were directly installed.

---

### Post by jobje on 2011-05-18
> **Sal Z said:**
> Well, it's not technically impossible, but it would require a lot of old packages, most of which have been superseded and would break your configuration if they were directly installed.

Oke, well I don't want to risk breaking my install ;)

---

### Post by MBybee on 2011-05-18
This is true of a lot of the old Loki Games stuff - I own almost everything they put out for Linux, and hardly any of it will run on a modern system without hacking around.

My solution was to do a chroot jail with all that old stuff they wanted.

---

