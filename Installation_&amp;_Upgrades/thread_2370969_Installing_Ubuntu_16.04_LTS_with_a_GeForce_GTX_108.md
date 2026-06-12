---
title: "Installing Ubuntu 16.04 LTS with a GeForce GTX 1080 Ti"
date: 2017-09-09
forum: Installation &amp; Upgrades
---

### Post by martine-dee on 2017-09-09
Good day : )

This morning I attempted USB installation of Ubuntu 16.04 LTS on a new blank PC.
First thing I encountered was the gfxboot.c32 error; got past it and selected live-installation.

Soon after that, display would show some six seconds worth of lines such as [below], and then freeze. Meaning, neither changes happen on the screen, nor restart happens on keyboard's* ctrl+shift+del.

```
...
[06.432831] nouveau 0000:65:00.0: fifo: SCHED_ERROR 08 []
...
```

The card is **ASUS GeForce GTX 1080 Ti Strix Gaming 11G**, the mobo is **ASUS ROG STRIX X299-E GAMING**. It doesn't look like the mobo has an integrated graphic card that I could use here.

Meanwhile, I gave the box test ride with Windows 10; all seems to be in order there.
It also means that I am out of the Ubuntu installation USB for the time being, since I had to overwrite it; but I should have another one ready soon.

Basically, a quick trick to bypass this would be **great** if someone had it ready.
Also, this may need come confirming to make sure it is a GC issue.
In any case, let's discuss this here. I'd like to have this box running Ubuntu. (Thanks!)

* - The keyboard was plugged in a USB 2.0 if that matters.

---

### Post by Bashing-om on 2017-09-09
martine-dee; Sure !

> 
In any case, let's discuss this here. I'd like to have this box running Ubuntu.

We can do that !
It is no big deal, once you know .

We want to boot with the nomodeset boot parameter to force the system to boot the the fall back graphic's driver:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Once booted then install the graphics driver:
```

sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

where I do expect the system to choose to install the 375 version driver. This driver should suffice. 
However: nvidia recommends the 384 version driver for the 1080 ti card .
[http://www.nvidia.com/download/driverResults.aspx/123103/en-us](http://www.nvidia.com/download/driverResults.aspx/123103/en-us)
 IF the 375 version driver does not work - then we have that 384 driver in our trusted PPA.  We get to that step if and when required.
Be aware that nvidia says :
> 
Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

We do follow that advisement and take the driver from ubuntu resources .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by martine-dee on 2017-09-10
> **Bashing-om said:**
> We want to boot with the nomodeset boot parameter to force the system to boot the the fall back graphic's driver:
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
Hi. I actually attempted to do this, per another thread that suggested adding a boot param would help. However, on this box I am not showed the regular grub menu. It was more like this message repeating:

```
Missing parameter in configuration file. Keyboard: path
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
gfxboot.c32: not a COM32R image
boot:
...
```

There, one can hit TAB to get a list of boot options, and type one back. But did I miss how to edit them?

Maybe it is just me, I'd find it comfiest if this could be edited on the USB stick before it is plugged in for an installation. A way to do this?

---

### Post by Bashing-om on 2017-09-10
martine-dee; Hummm ....

I have to question the integrity of the USB medium.

Verify the .iso hash:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

verify the copy to the USB:
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Once the foundation is secure then we look at it as a possible booting issue .

[INDENT][INDENT]ducks in a row
[/INDENT][/INDENT]

---

### Post by martine-dee on 2017-09-11
Very well. The checksum of the iso image matches. The USB's check tells: Check finished: no errors found; Press any key to reboot your system*.

One new thing: now it takes some seven seconds worth of nouveau errors for the computer to freeze:

```
...
[    7.456683] nouveau 0000:65:00.0: fifo: SCHED_ERROR 08 []
[    7.457766] nouveau 0000:65:00.0: fifo: SCHED_ERROR 08 []
[    7.461305] nouveau 0000:65:00.0: fifo: SCHED_ERROR 08 []
```

The only change that seems related is I turned down the turbo mode on the CPU**.

What next? : )

* - The check itself also requires graphic environment; which means it fails the same way as installation does on my new box; I ran the check on my currently functional box.
** - This took its frequency down from 4GHz to 3.6GHz.

---

### Post by Bashing-om on 2017-09-11
martine-dee; Huummm .. odd
to say the least .

Let's try to boot the liveUSB with the boot parameter " nouveau.modeset=0 " (F6 at the boot menu ) to disable nouveau and force the system to use the fall back graphics driver.

If this works, we can do the same in the install.

Once we get the system booted up we can install the proprietary driver for the nvida card .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2017-09-11
The  "gfxboot.c32: not a COM32R image" can result from creating the install media on an older release of Ubuntu with "Startup Disk Creator" -- an old copy of syslinux gets pulled off the running system instead of using the one from the ISO.  See [https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image)
Using dd or mkusb will avoid this mixup.

---

### Post by martine-dee on 2017-09-23
Got some other stuff to resolve first. Back here.

> **ubfan1 said:**
> The  "gfxboot.c32: not a COM32R image" can result from creating the install media on an older release of Ubuntu with "Startup Disk Creator" -- an old copy of syslinux gets pulled off the running system instead of using the one from the ISO.  See [https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](https://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image)
Using dd or mkusb will avoid this mixup.
Great tip, thanks! Pointing out the Startup Disk Creator as the guilty side in the gfxboot.c32 matter helped a lot. Got myself mkusb and that usb worked like a charm.

Things were still broken with the graphic card, but solving the gfxboot.c32 thing allowed pressing F6 and editing the command. Adding 'nouveau.setmode=0' to the command got things going.

There are more hardware related issues now, e.g. integrated wlan is 'unclaimed' with no drivers in sight, but the OP issue has been resolved. Again, in two tips:
- Do not use Startup Disk Creator, per above. You may use **mkusb**.
- Do edit the install command you are about to run to include option **nouveau.setmode=0**

Thanks all! : )

P.S.
Just one more time. : ) Pressing F6 during the gfxboot.c32 flow didn't give any results.

---

### Post by Bashing-om on 2017-09-23
martine-dee; Outstanding.

Making good progress.

If you have not yet, open a thread on the WIFI issue.
As this matter is now concluded
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]glad to be a bit of help
[/INDENT][/INDENT]

---

