---
title: "Ubuntu boots to tty1"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by kedar5 on 2013-02-13
Hi  ):P 

I am using Ubuntu 10.10. 
Uptil now I had installed NVIDIA graphics card on my machine, and had the drivers installed. Now I removed my graphics card, and my system boots to **tty1** virtual console. 
I am able to run the desktop in the safe graphics mode, but not in the normal mode.
Kindly help me if anyone has any idea.

Regards.

---

### Post by carl4926 on 2013-02-13
If you removed a graphics card
Did you replace it with another
Or is it using onboard

---

### Post by kedar5 on 2013-02-13
> **carl4926 said:**
> If you removed a graphics card
Did you replace it with another
Or is it using onboard

I am using the onboard graphics .i.e. Intel G41 chipset
My graphics card has gone bad (fan problem).

---

### Post by schragge on 2013-02-13
Try
```

sudo Xorg -configure
sudo dpkg-reconfigure `dpkg -l xserver\*|awk '/^ii/{print$2}'`
sudo update-initramfs -u

```

---

### Post by carl4926 on 2013-02-13
Possibly too

```
sudo apt-get remove nvidia-current
```

---

### Post by MAFoElffen on 2013-02-13
Actually, all above would work, but... With your old nvidia driver install and in 10.10, all that points xorg to that driver is the /etc/X11/xorg.conf file, device section, driver "nvidia"...

dkms didn't start until 11.04 so updating initramfs would have no effect/just extra work for nil.

So if you rename the xorg.conf file to anything but that name (example: xorg.conf.bak)... you are back in business.

Removing nvidia-current would have to be modified (namewise) if you are using a different nvidia driver package. "nvidia-installer" could remove if you installed an nvidia binary styled driver.
```

sudo nvidia-installer --uninstall

```
(with gdm stopped and not loaded)

---

### Post by kedar5 on 2013-02-14
I attempted to start the display from tty1 using startx.
Here is the tail of the o/p from **startx**

```

[   272.075] (WW) Falling back to old probe method for vesa
[   272.075] (WW) Falling back to old probe method for fbdev
[   272.075] (II) Loading sub module "fbdevhw"
[   272.075] (II) LoadModule: "fbdevhw"
[   272.075] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   272.075] (II) Module fbdevhw: vendor="X.Org Foundation"
[   272.075]     compiled for 1.9.0, module version = 0.0.2
[   272.075]     ABI class: X.Org Video Driver, version 8.0
[B][   272.075] (EE) open /dev/fb0: No such file or directory
[   272.076] (EE) intel(0): No kernel modesetting driver detected.
[   272.077] (II) UnloadModule: "intel"
[   272.077] (EE) Screen(s) found, but none have a usable configuration.[/B]
[   272.077] 
Fatal server error:
[   272.077] no screens found
[   272.077] 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   272.077] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   272.077] 
[   272.081]  ddxSigGiveUp: Closing log

```

Also I have purged all the nvidia files.

When I boot from failsafe mode, **/dev/fb0** is present.

```

#ls /dev/fb*
/dev/fb0

```

---

### Post by schragge on 2013-02-14
What kernel boot parameters are you using? And what version of GRUB?

For grub 1.9x, you probably need to add  *video* and/or *vga* to *GRUB_CMDLINE_LINUX* in */etc/default/grub*
Try something like
```

GRUB_CMDLINE_LINUX="vga=791 video=vesafb:mtrr,ywrap"

```
then *sudo grub-update* and reboot.

For grub-legacy, try to edit /boot/grub/menu.lst directly.

Also, see [uwiki]FrameBuffer[/uwiki] in Ubuntu Wiki.

---

### Post by bantuvez on 2013-02-14
What is the version of your kernel? Try updating it.

---

### Post by kedar5 on 2013-02-14
I am supposedly using GRUB2. Kernel is 2.6.35-22-generic.

This is my GRUB file.

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1024x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=" vga=791"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1024x768-24
GRUB_GFXPAYLOAD_LINUX=1024x768-16

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

I had added the line - 
GRUB_GFXPAYLOAD_LINUX=1024x768-16

when I was using NVIDIA card.

Also I get the following message when I boot in normal mode everytime for about 5-10 sec which is quite frustrating.
> 
vga=791 is deprecated, use set gfxpayload=1024x768x16,1024x768 before linux command instead.


---

### Post by schragge on 2013-02-14
> **kedar5 said:**
> Also I get the following message. Well, then remove "vga=791" from GRUB_CMDLINE_LINUX.

My suggestion is to install the package *fbset*, look at the output of *fbset -i* in safe mode, and read up the man pages [fbset(1)](http://manpages.ubuntu.com/manpages/precise/en/man1/fbset.1.html) and [fb.modes(5)]("http://manpages.ubuntu.com/manpages/precise/en/man5/fb.modes.5.html") as well as package documentation in */usr/share/doc/fbset/*, especially [/usr/share/doc/fbset/kernel-doc/vesafb.txt.gz]("http://www.kernel.org/doc/Documentation/fb/vesafb.txt"), [/usr/share/doc/fbset/kernel-doc/uvesafb.txt.gz]("http://www.kernel.org/doc/Documentation/fb/uvesafb.txt") and [/usr/share/doc/fbset/kernel-doc/intelfb.txt.gz]("http://www.kernel.org/doc/Documentation/fb/intelfb.txt")

As said in there, look for MTRR mismatches (*dmesg|grep mtrr*) and adjust mtrr parameter accordingly.

Don't think it makes any difference, but I'd also change the form of the *video* kernel parameter to the more concise one:
```
video=uvesafb:1024x768-24,mtrr:3,ywrap
```

Just curious, why the kernel video parameter says 1024x768-[color=red]24[/color], but GRUB_GFXPAYLOAD_LINUX=1024x768-[color=red]16[/color]?

Also, try to boot from a LiveCD/USB and look up the right framebuffer settings.

Another option is to remove all framebuffer settings from */etc/default/grub* and look what Ubuntu will automatically choose.

Also see:
[list]
[*][Framebuffer-HOWTO]("http://tldp.org/HOWTO/Framebuffer-HOWTO/").
[*]Answers and comments to [this question]("http://unix.stackexchange.com/questions/33596/no-framebuffer-device-how-to-enable-it").
[/list]

---

### Post by bantuvez on 2013-02-14
Yes. Remove any instances of "vga=" from GRUB_CMDLINE and also remove "nomodeset" from there. 

If it won't help I would try a newer kernel also.

---

### Post by kedar5 on 2013-02-15
> **bantuvez said:**
> Yes. Remove any instances of "vga=" from GRUB_CMDLINE and also remove "nomodeset" from there. 


I tried this one first and it solved the issue. Thanks a ton bantuvez and schragge.

---

### Post by kedar5 on 2013-02-19
I really want to rate this thread good, and mark the posts helpful.
but I have not found how to do it. Is there any way.

---

