---
title: "grub entry gone after upgrading ubuntu 9.10"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by opensas on 2010-01-06
a strange thing happened...

I have installed ubuntu 9.10 and everything was working fine

just a minutes ago a window popped up telling me that a complete update couldn't be completed, and asked me to go on with a partial update.

I did it and then a window popped up (I think it was debconf running) asking me if I wanted to delete phpmyadmin database configuration or if I wanted to keep it... seemed like the updater was removing quite a bunch of packages!

after that I was presented with a looong list of packages to be removed (among them apache2, php5, linux headers, etc.)

I thought it was going to remove them in order to reinstall them latter, so I let it go)

but now there's no ubuntu entry in the grub menu, so I had to boot with windows! :(

I need some help to fix this mess... right now I'm downloading ubuntu 9.10 livecd to give it a try...

thanks a lot


ps: quite often I issue a aptitude update followed by an aptitude safe-upgrade, so I think my system should have been pretty much upto date

ps2: is it a bug in the updater? has anybody else experienced such a thing?

---

### Post by kansasnoob on 2010-01-06
I know this is in a development thread but it still pretty much applies:

[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

Anyway I've quite often been able to recover from these problems using a mount & chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

**[COLOR="Red"]Note: You must know what partition to mount![/COLOR]**

If you'd like to try it I'll certainly try to help, but I first need to see the output from terminal (using your Live CD) of:

```
sudo fdisk -l
```

You should also know that this could well take an hour or considerably longer, quite a bit of back and forth between us, and there is no guarantee we'll be able to save it!

I generally begin by running "lsb_release -a" just to be sure I'm in the right place then "apt-get update" and "apt-get upgrade" just to see what the output tells me.

Quite often I'll end up having to "apt-get install --reinstall" some base packages like "ubuntu-minimal", "ubuntu-standard", and "ubuntu-desktop".

Thought to add this one: "update-grub" will be needed to try and add the kernel back to grub.cfg if we'd get that far!

A lot of times certain errors tell me what do do next, it can be time consuming but I actually enjoy playing with things :P

In all honesty a fresh install is usually less time consuming but less fun for idiots like me.

---

### Post by opensas on 2010-01-06
hey, thanks a lot!

let's go for it... it reminds me my all gentoo days... I no longer remember the last time I chrooted...

well, i'm about to boot my usb drive... I'll tell ya how it goes

---

### Post by opensas on 2010-01-06
I've finally chrooted, aptitude update && aptitude safe-upgrade and look what I've found

The following NEW packages will be installed:
  linux-headers-2.6.31-17{a} linux-headers-2.6.31-17-generic{a} 
The following packages will be upgraded:
  chromium-browser chromium-browser-inspector linux-headers-generic linux-libc...

so, the kernel headers are back... it seems...

---

### Post by kansasnoob on 2010-01-06
That looks promising!

Remember to run "update-grub" while you're still in the chroot. If this is a dual or multi-boot os-prober will only find the mounted Ubuntu's kernel so you'll have to run "sudo update-grub" after you boot into Ubuntu the first time, and always wait until it says "done". Mine thrashes around for as long as 2 minutes sometimes but I'm running a ridiculous multi-boot.

---

### Post by opensas on 2010-01-06
mmm

grub cannot find any kernel, I guess

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

so I

aptitude install linux-image-2.6.31-17-generic

and then

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!
done

well it seems like it found something...

---

