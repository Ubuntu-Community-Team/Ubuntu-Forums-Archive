---
title: "HOW TO - Feisty with ATI's legacy fglrx (8.28.8) driver for older cards"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by slowth on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/85907](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/85907) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I upgraded to Feisty a couple of days ago and quickly discovered that the included fglrx driver won't work anymore with the ATI card in my laptop. ATI dropped support for this card some time ago and the latest working driver is 8.28.8. 

There are patches available for the fglrx kernel module to make it work with the 2.6.20 kernel included in Feisty but the x.org driver is binary only and will only load in x.org 7.1 while Feisty uses x.org 7.2. Using the open source radeon driver isn't an option for me since I cannot get my nice 22" extrenal widescreen monitor to work properly with it. 

In short here's what I did to get fglrx to work with my hardware: First I downgraded x.org to 7.1 using the packages from Edgy. Then I used [Alberto Milone's Envy]("http://albertomilone.com/nvidia_scripts1.html") application to install the legacy fglrx driver for my card.

**NOTE 1**: This worked for me with my card (lspci says "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)"). Your mileage may wary. Also, as I'm writing this after I got this to work there might be some errors in the description below. If you find one please let me know.

**NOTE 2**: DRI doesn't seem to work for me right now. I haven't looked into it any further. Let me know if you get it to work.

[SIZE="4"]Instructions[/SIZE]

To downgrade x.org I had to add the Edgy repositories to /etc/apt/sources.list. Just copy the lines for feisty and replace feisty with edgy. Here's what my sources.list looks like:

```
deb http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

deb http://dk.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://dk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
```

Then you might want to tell apt that feisty is the default release to be used. To do this create the file /etc/apt/apt.conf.d/02version with the following contents:

```
APT::Default-Release "feisty";
```

apt now has to be told that the x.org packages from Edgy should be used instead of the Feisty ones. Create the file /etc/apt/preferences with the following contents:

```
Package: xorg
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-dev
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-core
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-all
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-mouse
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-video-all
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-video-ati
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-evdev
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-kbd
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-mouse
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-synaptics
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-wacom
Pin: release a=edgy
Pin-Priority: 1001

Package: xserver-xorg-input-elographics
Pin: release a=edgy
Pin-Priority: 1001
```

Now a simple

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-core
```

should remove x.org 7.2 and install x.org 7.1. You should probably close down X first before you attempt this.

The final step is to download Envy and use it to install the fglrx driver. It will detect the card you have and download the correct driver:

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.1-0ubuntu4_all.deb
sudo dpkg -i envy_0.9.1-0ubuntu4_all.deb
sudo apt-get -f install
sudo envy -t
```

Choose option 3 in the menu. Answer yes when Envy wants to reboot. Make sure your /etc/X11/xorg.conf file uses the fglrx driver (Envy might take care of that for you, I'm not sure) and then start X.

---

### Post by rodrigochinaski on 2007-05-04
I tried to follow this guide.

However, if you use the envy version described on the guide, it says ENVY does not support my operating system (feisty)
If i get a newer ENVY, it says ati legacy drivers aren't supported by my operating system.

I need badly run 8.28 on feisty, otherwise I can't get TV-Out for this damn Radeon Mobility 9000...

---

### Post by mwacky on 2007-05-06
Envy gives me the same error, does not support operating system.  I recently upgraded to Feisty and have not been able to get Google Earth to work properly.  My card is a ATI Radeon 200M.  I was able to get it working on Edgy by following [this]("http://ubuntuforums.org/showthread.php?t=321766").    I'm too much of a newbie to be able to update my driver with the new kernal, any suggestions?

---

### Post by rayene.benrayana on 2007-05-10
For those who are still here 

You have to replace the

envy_0.9.1-0ubuntu4_all.deb

with 

envy_0.9.2-0ubuntu4_all.deb

and the error disappears ;)

Hopefully another error appears :)
```


Package fglrx-kernel-src was not built successfully, see /var/cache/modass/fglrx-kernel-src*buildlog* for details!


```

And for sure, the log file is empty :)

any idea ?

---

### Post by rodrigochinaski on 2007-05-11
try
module-assistant -v -t build fglrx (to see the error messages, not to solve the problem :)

I already downgraded my X to 7.1, but still stuck trying to compile the fglrx 8.28 for the 2.6.20 kernel.



I have a Radeon Mobility 9000 on my laptop and the ATI Open Source driver works well with 3-D. It supports AIGLX and I can run compiz or beryl with it, something I never accomplished to do on edgy/dapper, and I tried a lot messing with ati driver/fglrx driver/aiglx/xgl. 

But I'm more interest in TV-Out support than 3D support/aiglx/xgl support. 

So the ati/radeon open-source driver aren't TV-Out capability, that's right?

I want to run fglrx 8.28 on feisty to get tv-out support. 

gatos and atitvout doesn't work for my card (lspci says: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)

Is there anything I can do to get tv-out support without using fglrx ?

---

### Post by sebos69 on 2007-05-11
TVout is possible if you use the GATOS drivers. See

[http://ubuntuforums.org/showthread.php?t=215763](http://ubuntuforums.org/showthread.php?t=215763)

it works well on my Radeon 9200 SE.

---

### Post by rodrigochinaski on 2007-05-13
The latest patch on this site [http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html) is for xorg-ati-driver 6.5.8 and feisty uses 6.6.3.. 

however, I tried to compile the 6.5.8 driver, it says:

     
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT r128_accel.lo -MD -MP -MF .deps/r128_accel.Tpo -c r128_accel.c  -fPIC -DPIC -o .libs/r128_accel.o
r128_accel.c: In function 'R128CCEWaitForIdle':
r128_accel.c:247: error: 'errno' undeclared (first use in this function)
r128_accel.c:247: error: (Each undeclared identifier is reported only once
r128_accel.c:247: error: for each function it appears in.)
r128_accel.c:247: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEStop':
r128_accel.c:286: error: 'errno' undeclared (first use in this function)
r128_accel.c:286: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEGetBuffer':
r128_accel.c:1573: error: 'EAGAIN' undeclared (first use in this function)
make[2]: ** [r128_accel.lo] Erro 1
make[2]: Saindo do diretório `/root/xf86-video-ati-6.5.8.0/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/root/xf86-video-ati-6.5.8.0'
make: ** [all] Erro 2

---

### Post by sebos69 on 2007-05-13
> **rodrigochinaski said:**
> The latest patch on this site [http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html) is for xorg-ati-driver 6.5.8 and feisty uses 6.6.3.. 

however, I tried to compile the 6.5.8 driver, it says:

     
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT r128_accel.lo -MD -MP -MF .deps/r128_accel.Tpo -c r128_accel.c  -fPIC -DPIC -o .libs/r128_accel.o
r128_accel.c: In function 'R128CCEWaitForIdle':
r128_accel.c:247: error: 'errno' undeclared (first use in this function)
r128_accel.c:247: error: (Each undeclared identifier is reported only once
r128_accel.c:247: error: for each function it appears in.)
r128_accel.c:247: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEStop':
r128_accel.c:286: error: 'errno' undeclared (first use in this function)
r128_accel.c:286: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEGetBuffer':
r128_accel.c:1573: error: 'EAGAIN' undeclared (first use in this function)
make[2]: ** [r128_accel.lo] Erro 1
make[2]: Saindo do diretório `/root/xf86-video-ati-6.5.8.0/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/root/xf86-video-ati-6.5.8.0'
make: ** [all] Erro 2

try this HowTo, it has the patches matching feisty fawn driver.

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

---

### Post by aulio on 2007-05-18
> **rayene.benrayana said:**
> For those who are still here 

Hopefully another error appears :)
```


Package fglrx-kernel-src was not built successfully, see /var/cache/modass/fglrx-kernel-src*buildlog* for details!


```

And for sure, the log file is empty :)

any idea ?

Any solution to this?

I'm trying to get dual head working with ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]. Any ideas?

---

### Post by mwacky on 2007-05-19
I received the same error message when trying to run envy with an older kernal, make sure you see the update from  rayene.benrayana  above and that you are using the kernel packaged with Feisty.

> 
You have to replace the

envy_0.9.1-0ubuntu4_all.deb

with

envy_0.9.2-0ubuntu4_all.deb

---

### Post by rodrigochinaski on 2007-06-08
Still can't make TV-OUT work on a Radeon Mobility FireGL 9000 (R250) with Feisty Fawn.
Any REAL solution?

---

### Post by amar611 on 2007-06-12
well well.. I got my big fat dell monitor 2007 flat monitor working with (lspci) 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)

Followed slowth's instructions and was stuck at envy error

Package fglrx-kernel-src was not built successfully, see /var/cache/modass/fglrx-kernel-src*buildlog* for details!

installed 
xorg-driver-fglrx_7.1.0-8.28.8+2.6.17.5-11_i386.deb from [http://mirror.x10.com/mirror/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/](http://mirror.x10.com/mirror/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/)

Then,
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

Slowth Thanks alot for your instructions :popcorn:

upgrade successful.
Thanks.

-amar

---

### Post by ravalox on 2007-06-15
I think the simple answer here is to revolve your OS back to the previous version.  Dapper supports the legacy cards out of the box; no complicated jiggery pokery.

---

### Post by rodrigochinaski on 2007-06-22
I want to have TV-Out on Radeon Mobility 9000 using my shiny Feisty, not buggy Edgy!

---

### Post by rodrigochinaski on 2007-08-17
Any progress making TV-OUT work with ATI Opensource drivers on Feisty Fawn?
Or, at least, a clean way to install ati's fglrx legacy on Xorg 7.2 and kernel 2.6.20 ?

---

