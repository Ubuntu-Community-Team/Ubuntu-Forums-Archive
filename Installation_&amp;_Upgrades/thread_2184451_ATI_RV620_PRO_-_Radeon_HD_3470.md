---
title: "ATI RV620 PRO - Radeon HD 3470"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by kaefert66014235 on 2013-10-29
Ubuntu 13.10 live system won't correctly boot on one of my machines. I've checked the usb-stick and I've successfully used it to install 13.10 on another machine.

I think the problem is the graphics card:
VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV620 PRO [Radeon HD 3470] [1002:95c0] (prog-if 00 [VGA controller])

The other machine that I successfully installed 13.10 got an nvidia card.
I think I'll install 13.04 on this ati-powered machine. The negative thing about that decision is that support for 13.04 ends in 5 months, with no time-overlap to 14.04

---

### Post by kaefert66014235 on 2013-10-29
update:

Okey, so installing 13.04 worked, but graphics performance is really bad. especially when I try to open the unity dashboard, it takes a few seconds.

this is the driver that seems to be used by default:
```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV620
OpenGL version string: 1.4 (3.0 Mesa 9.1.7)
```

The binary ati drivers taken from the ubuntu repositories don't seem to fit my graphics card:
```
:~$ sudo aticonfig --initial
aticonfig: No supported adapters detected

```

I've used this guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
to download and install amd-driver-installer-catalyst-13.1-legacy-linux-x86.x86_64

With those I manage to produce a new xorg.conf file:
```
:~/Downloads$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-1

```

Though this crashed my Unity GUI completely, I've tested the same with 13.10 on the same machine, gave the same results.
```
:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

I think I will try Ubuntu 12.10 next... having a few seconds lag every time I want to open an application (unity dashboard with Gallium 0.4 graphic drivers) is no option for me.

Now I've tried Ubuntu 12.10 and with this installing the fglrx package from the default repositories gives this:
```
:~$ fglrxinfo
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
```

and after a reboot the same non working picture that 13.04 and 13.10 gave me. Though I find that a bit strange since Mint14 worked very nicely on this very same machine already, and Mint14 is based on Ubuntu 12.10.
though maybe the cinnamon desktop does work better with those fallback / opensource drivers..

Okey, now I've also tried 12.04.3 LTS - this has a better (useable) fallback once I've installed the ATI drivers, but also here neither the ones included in the repositories nor the ones downloaded from ATI work. I think I'm gonna go look at linux mint again, see if it magically makes those ATI drivers work, or if it just doesn't require that much graphics power so that it feels fine with open-source drivers. (Though the lag when opening the dashboard with 12.04 is already a lot less than with 13.04 and 13.10)

---

### Post by Mark Phelps on 2013-10-29
There are no proprietary AMD drivers that will work with your card and any Ubuntu version newer than 12.04.1.  Starting with 12.04.2, the X-server in Ubuntu was updated to a version that is incompatible with the X-server.  With those versions and newer of Ubuntu, you are relegated to using the open-source Radeon driver.

---

### Post by kaefert66014235 on 2013-10-30
okey, thanks for the info Mark!
I've now settled with Linux Mint 15 with Cinnamon on that machine, which has the advantage of a non-transparent main-menu which does not give me a lag of up to 1 second like ubuntu 12.04.3 to 13.10 do.

---

### Post by mastablasta on 2013-10-30
there is sitll image 12.04.1 availabel if oyu want to use proprietary drivers. 

people also downgraded their x-server to use legacy drivers on new 13.10 ubutnu (not really recomended).

have you tried the nomodeset boot option to boot into 13.10?: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

kernel in 13.10 has many imnprovements in the driver. i am not sure if exactly your card benefits, but i do know that AMD helped a lot with latest opensource driver.

---

### Post by kaefert66014235 on 2013-10-30
thanks for the reply mastablasta,
No I've not tried nomodeset boot option, but I managed to get a working 13.10 on that machine by installing 13.04 and upgrading it to 13.10. Performance of 13.10 was not better than with 13.04.

---

