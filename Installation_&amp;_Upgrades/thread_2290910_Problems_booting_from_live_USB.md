---
title: "Problems booting from live USB"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by raen on 2015-08-16
I have an old netbook running 32-bit Lubuntu that I don't use that much anymore. The other day I finally got around to upgrading it to the latest version, but something went wrong and it got stuck in an infinite boot loop. I figure no big deal, I'll just boot from a live USB, make sure everything is backed up, and do a clean re-install.

So I plug in the USB, turn on the netbook, and now it's sitting there looking like this:

```

Missing parameter in configuration file. Keyword: path
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:

```

So I power it down, turn it back on and go into Setup. The boot priority order reads:

```

1. USB FDD :
2. USB HDD : General USB Flash Disk
3. IDE0 : WCD WD1600BEVT-22ZCTO
4. IDE1 :
5. Network Boot: Atheros Boot Agent
6. USB CDROM :

```

(Some of those Os might be 0s, it's hard to tell).

I move USB CDROM to the first position, but I get the same problem as above.

I used Startup Disk Creator on my 64-bit Ubuntu desktop to install lubuntu-15.04-desktop-i386.iso on a 2GB stick. Is there something I can do, or does it sound like a hardware problem?

Thanks.

---

### Post by yancek on 2015-08-16
I would move USB HDD to first position and give that a try.  If that doesn't work, try to boot it on another computer if you have one available to eliminate that as the problem.

---

### Post by raen on 2015-08-16
Didn't work, got the same results. Testing it on my desktop computer didn't do anything, it just booted up normally. I have a multi-boot system, so I'm not sure how to force it to boot from USB.

---

### Post by ajgreeny on 2015-08-16
First, did you check that the iso file you used to make the new USB install disk is a good one by checking the [md5sum]("https://help.ubuntu.com/community/UbuntuHashes")?

There is also usually a key to press when you power-on to change the boot device on-the-fly; on my old netbook it is F11, but it may be something else on yours.  The same may be true of your desktop machine, but this assumes that the USB really is bootable, of course; how did you make it?

Give that a try and you may be lucky.

There is also a bug for the error message you got which is discussed at [http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701) which must be worth trying if you can get to that point again.

---

### Post by raen on 2015-08-16
> **ajgreeny said:**
> 
There is also a bug for the error message you got which is discussed at [http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701) which must be worth trying if you can get to that point again.

That was exactly it. And now that I see it, I recall having to deal with that before when I was helping a friend with their computer.

Thank you!

---

