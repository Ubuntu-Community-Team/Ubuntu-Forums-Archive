---
title: "Is Karmic featuring the new 2.6.31 kernel?"
date: 2009-07-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JohnLau on 2009-07-09
):PI just went to ubuntu package search and I found that there are packages for kernel 2.6.31 on karmic. Anyone recieved this as an update? How is it when comparing to 2.6.30 kernel?

---

### Post by dino99 on 2009-07-09
hey,

i'm running 2.6.31-2-generic & it's more stable than previous kernel

On some old mobo, sometime need to add noacpi nolapi to boot line, but not a big problem):P

---

### Post by JohnLau on 2009-07-09
Does the fglrx provided by karmic repository support the new kernel?

---

### Post by alphacrucis2 on 2009-07-09
> **JohnLau said:**
> Does the fglrx provided by karmic repository support the new kernel?

No.

---

### Post by jerrylamos on 2009-07-09
> **dino99 said:**
> hey,

i'm running 2.6.31-2-generic & it's more stable than previous kernel



Well, 2.6.31-2 with the updated Gnome crashes randomly on my IBM Thinkpad R31 intel i830 graphics and my IBM ThinkCentre A30 intel i845 graphics.  Seems to be a little better this morning with "splash" deleted from the grub2 kernel boot line.  Why this should matter after boot completes I have no idea.  I also have screensaver turned off and 2 hours set.

On my Compaq Presario Radeon Xpress 200 the new KMS graphics feature is turned off by default since the display with KMS is vertical colored bars and no desktop.

Join the fun....

Jerry

p.s. video speed with KMS on the i845 and i830 on 32 bit as measured by GtkPerf from Ubuntu Synaptic is twice as slow as intrepid.

---

### Post by pferraro on 2009-07-09
> **jerrylamos said:**
> Well, 2.6.31-2 with the updated Gnome crashes randomly on my IBM Thinkpad R31 intel i830 graphics and my IBM ThinkCentre A30 intel i845 graphics.  Seems to be a little better this morning with "splash" deleted from the grub2 kernel boot line.  Why this should matter after boot completes I have no idea.

The crash to which you refer has nothing to do with the kernel, but with the new gdm:
[http://ubuntuforums.org/showthread.php?t=1202843&page=38](http://ubuntuforums.org/showthread.php?t=1202843&page=38)
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/396226)

Removing "splash" from the grub options is currently one of the known workarounds.

---

### Post by mrsurb on 2009-07-09
I prefer 2.6.31 on mine, because with my Intel 965 on-board graphics in my laptop it boots with much smaller fonts, so that tty1-6 can all display a lot more text on them.

However, I have been unable to get virtualbox-ose working on it, it says it wants the kernel to run with "nmi_watchdog=0", but changing this in grub's menu.lst has no effect.

---

### Post by Progressive on 2009-07-09
> **mrsurb said:**
> I have been unable to get virtualbox-ose working on it, it says it wants the kernel to run with "nmi_watchdog=0", but changing this in grub's menu.lst has no effect.

I can confirm this issue with the new kernel. Strange too since it was working at first for a bit.

Is this a known bug? Or shall I file one?

---

### Post by jerrylamos on 2009-07-09
> **pferraro said:**
> Removing "splash" from the grub options is currently one of the known workarounds.

Seems to have worked:

sudo gedit /etc/default/grub

remove splash

sudo update-grub

reboot.

Jerry

---

### Post by ktp on 2009-07-09
This seems like gdm bug; see this and fix/hack is provided:

[http://ubuntuforums.org/showthread.php?t=1206717](http://ubuntuforums.org/showthread.php?t=1206717)

---

### Post by wayne_cat on 2009-07-09
> **ktp said:**
> This seems like gdm bug; see this and fix/hack is provided:

[http://ubuntuforums.org/showthread.php?t=1206717](http://ubuntuforums.org/showthread.php?t=1206717)

Should be fixed in the latest gdm version:

gdm (2.26.1-0ubuntu5) karmic; urgency=low

```
* debian/gdm.preinst: Remove obsolete conffiles.
* debian/gdm.preinst: Migrate autologin settings from gdm.conf (which isn't
read any more) to custom.conf. (LP: #396459)
* Add 81_initial_server_on_vt7.patch: Force initial X server to go to tty7
instead of tty1. This is an Ugly Hack until we have a cleaner solution for
getty not to tramp over a running X server on vt1. This bandaids the
immediate problem of the first X server being killed after a few minutes
due to getty on tty1 timing out. (LP: #396226)

[https://lists.ubuntu.com/archives/ka...ly/003831.html]("https://lists.ubuntu.com/archives/karmic-changes/2009-July/003831.html")

```

---

### Post by buzzmandt on 2009-07-10
> **mrsurb said:**
> I prefer 2.6.31 on mine, because with my Intel 965 on-board graphics in my laptop it boots with much smaller fonts, so that tty1-6 can all display a lot more text on them.

However, I have been unable to get virtualbox-ose working on it, it says it wants the kernel to run with "nmi_watchdog=0", but changing this in grub's menu.lst has no effect.

I LOVE the smaller font with tty1-6.  but not getting the promised performance of UDX or G or whatever it is.  glxgears is outdated but with real world applications it's suppose to rock.

Can't play neverwinter nights.  Slow graphics lag bad.  2.6.30-10 kernel was great for me.  nwn played good, wifi automatic.

2.6.31 nwn forget it, wifi not happening.  Trying to get at the root of the problem with wifi on launchpad, so hopefully we'll get that one straightend out.

graphics issue might be more xorg then kernel, not sure.  Hope it improves though.  Seems a lot of issues with graphics so I'm not alone here.

---

### Post by psyke83 on 2009-07-10
> **buzzmandt said:**
> I LOVE the smaller font with tty1-6.  but not getting the promised performance of UDX or G or whatever it is.  glxgears is outdated but with real world applications it's suppose to rock.

Can't play neverwinter nights.  Slow graphics lag bad.  2.6.30-10 kernel was great for me.  nwn played good, wifi automatic.

2.6.31 nwn forget it, wifi not happening.  Trying to get at the root of the problem with wifi on launchpad, so hopefully we'll get that one straightend out.

graphics issue might be more xorg then kernel, not sure.  Hope it improves though.  Seems a lot of issues with graphics so I'm not alone here.

It's called UXA. What graphics chipset do you own? I also notice severe regressions in 3D performance with the 2.6.31 kernels; I'm thinking of filing a bug, but I want to know if other chipsets are affected.

```
conn@inspiron:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

---

### Post by buzzmandt on 2009-07-10
IF you do I will second the motion....
> buzzmandt@buzzmandt-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


---

### Post by Eclipse. on 2009-07-10
> **mrsurb said:**
> I prefer 2.6.31 on mine, because with my Intel 965 on-board graphics in my laptop it boots with much smaller fonts, so that tty1-6 can all display a lot more text on them.



Thats kernel mode settings (KMS), it does much more than give you nicer fonts in tty's. ;)

---

