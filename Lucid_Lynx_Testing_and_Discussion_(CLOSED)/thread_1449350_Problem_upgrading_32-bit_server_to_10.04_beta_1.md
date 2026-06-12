---
title: "Problem upgrading 32-bit server to 10.04 beta 1"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rickwookie on 2010-04-07
I thought I'd give 10.04 a try since it's an LTS release and I was still using Jaunty.
I did the upgrade over SSH using sudo*do-release-upgrade*-d and at first it just upgraded me to Karmic. After the reboot I ran the same command again and it looked like it was upgrading this time to Lucid.
Now however after the reboot I no longer could log in (no SSH) and after inspecting the system locally by digging out and old monitor and keyboard, it seams the system hangs during boot.

I went into the Grub menu and found that there is no server kernel listed (apart from the old Jaunty one), only generic-pae and generic. None of these will boot, and if I try the recovery modes the keyboard doesn't function when I get to the recovery menu. Also if I boot the old 2.6.28-17-server, it does boot, but the keyboard also won't function once it boots. I can SSH in once the old kernel has booted, but when I tried to install linux-image-2.6.32-19-server via apt, it can't be found. Furher investigation online sems to indicate that there's only a 64-bit server package and no 32-bit package.

What's that all about, is 32-bit no longer supported on the server platfom, and if so is my install now screwed?

---

### Post by whoop on 2010-04-07
If you boot a working kernel, and connect via ssh what does:
```

cat /etc/issue

```
return?

32 bit server should be supported for lucid :)

---

### Post by rickwookie on 2010-04-11
> **whoop said:**
> If you boot a working kernel, and connect via ssh what does:
```

cat /etc/issue

```
return?

32 bit server should be supported for lucid :)

```
Ubuntu lucid (development branch) \n \l
```
I notice tonight though that doing an 'apt-get update' and 'apt-get upgrade' produces a 'linux-image-server (2.6.32.20.21)' and a 'linux-server (2.6.32.20.21)'.

I'll try booting into that new kernel and see what happens. I wonder why there was no 32-bit server kernel previously?

---

### Post by nanog on 2010-04-11
the kernel was probably building and held back until dependencies are resolved. you can always install the kernel manually via the command line (if its archived locally) or by downloading from here:

[https://launchpad.net/ubuntu/lucid/+package/linux-image-server](https://launchpad.net/ubuntu/lucid/+package/linux-image-server)


or if you are feeling frisky you can install the mainline kernel as a temporary fix:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by rickwookie on 2010-04-19
It seems that linux-server depends on linux-generic-pae which in turn depends on linux-image-generic-pae which currently depends on linux-image-2.6.32-21-generic-pae.
linux-image-server depends on linux-image-generic-pae directly.

So there is no linux-image-2.6.32-21-server, but [http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-server]("http://packages.ubuntu.com/lucid/linux-image-2.6.32-21-server") shows that it exists for the amd64 platform.

So I'm still confused!

---

### Post by rickwookie on 2010-04-22
Ok, so thankfully I can now boot using linux-image-2.6.32-21-generic-pae, which is good because certain things that just wouldn't work anymore using the old kernel (like my M-Audio 24/96 sound card - mismatch between the kernel and the ALSA driver?) now work again. :)

Does this mean however that there is not going to be a server specific kernel for the 32-bit platform?

One last thing that is still not quite right (though only bothers me when logging-in locally): The caps-lock LED does nothing. The caps-lock itself seems to work fine, and the LED works at the BIOS and GRUB screens (so it's not broken). Any ideas?

---

