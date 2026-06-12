---
title: "Edgy usplash gone on boot"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by UltraMathMan on 2006-10-29
Did some searching and tried adding vga=791 to /boot/grub/menu.lst but that just gave me some weird test looking things in the upper left of my screen. I noticed however that when I did sudo update-grub I got the following ```
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
***Searching for splash image ... none found, skipping ...***
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/vmlinuz-2.6.15-27-686
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-686
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.15-23-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```
so I did sudo aptitude reinstall usplash and tried again, but sudo update-grub keeps listing the splash image as missing. Any suggestions?

---

### Post by UltraMathMan on 2006-10-30
Ok, I think I got it back, I did ```
sudo aptitude reinstall usplash-theme-ubuntu
``` and then ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` I noticed this was editing the generic kernel so I rebooted and used that one (need it to support dual-core apparently too) and presto! Usplash is back :)

---

### Post by Sentinel83 on 2006-10-30
It's awesome to see something that worked for you and that I will be able to try tonight.  I have been searching for quite a while for a fix to the blank boot screen and adding the vga=xxx to the menu.lst didn't work for me either.

I finally have some hope that maybe I can try those commands tonight and get my usplash back.  

Thanks for posting that information UltraMathMan

---

### Post by frankelr on 2006-10-30
You need to update-grub after editing menu.lst!

Try out the vga=791 idea by editing the grup boot line (esc at grup boot)  Also vga=791 doesn't work with all monitors or video cards..
I needed to use vga=788 for sis 630/730 video

Bob

---

### Post by UltraMathMan on 2006-10-30
> **frankelr said:**
> You need to update-grub after editing menu.lst!

Try out the vga=791 idea by editing the grup boot line (esc at grup boot)  Also vga=791 doesn't work with all monitors or video cards..
I needed to use vga=788 for sis 630/730 video

Bob

I did try both vga=791 and vga=788 and did update-grub after each, when I would update-grub it kept telling me no splash was found, which is why I tried what turned out to work (see my second post).

Sentinel, hope this works for you too!

---

### Post by Sentinel83 on 2006-11-02
Hey guys no such luck.  ](*,) 

I tried to do the two commands in MathMan's second post, didn't work and I tried to add the vga=791 into my menu.lst and that also didn't work.  

I am thinking about opening up a new thread to see if I can get some more help.

Thanks!

---

### Post by seatea on 2006-11-02
Try to use Synaptic to re-install everything usplash. There are three programs in Synaptic, usplash, usplash-dev, and usplash-theme-ubuntu. Apply the reinstall option to all of  them.

---

### Post by Sentinel83 on 2006-11-03
Nope, the reinstall through synaptic still didn't work.

---

### Post by UltraMathMan on 2006-11-03
After I did the steps listed in my post I booted with the generic kernel, are you booting with that or the i386 one?

---

### Post by johnny9794 on 2006-11-06
> **UltraMathMan said:**
> Ok, I think I got it back, I did ```
sudo aptitude reinstall usplash-theme-ubuntu
``` and then ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` I noticed this was editing the generic kernel so I rebooted and used that one (need it to support dual-core apparently too) and presto! Usplash is back :)


Thanx man that worked for me :).

---

### Post by alephnull on 2006-11-06
Something that helped me fix this as well as reinstalling the usplash artwork was to change the resolution settings in /etc/usplash.conf. By default it seems to be 640x480, and there is no associated artwork at that resolution.
I changed mine to
```

# Usplash configuration file
xres=1024
yres=768

```
and this, done between the 2 steps mentioned by UltraMathMan (so this would be step 1.5) in the post above, fixed the problem for me.

---

