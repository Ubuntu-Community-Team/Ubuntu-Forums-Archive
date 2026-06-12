---
title: "no GDM (no screens found)"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-02-22
so I've had this 32-bit LucidLynx machine running fine
for a month or so, then last week after an update, I only get
a blank screen for tty7.
(I'm not blaming the update as I have 3 other machines
that are working perfectly fine.)

I can log in on the other tty's or ssh into the machine.
So the machine is running fine. Just no Display.

I've run `sudo dpkg-reconfigure xserver-xorg`
and rebooted a dozen times since last week.
This does nothing helpful.

I noticed in /var/log/Xorg.5.log, various errors.
Not sure which ones are normal and which ones are bad.

In either case, I don't know how to fix this.

Here are some of the errors or differences compared
to another Linux machne sharing the same monitor:

 Section "Screen"
    Identifier "Builtin Default nouveau Screen 0"
    Device     "Builtin Default nouveau Device 0"
 EndSection

.
.
.
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
(II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
(EE) VESA(0): No valid modes
(II) UnloadModule: "vesa"
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules/libint10.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules/libvbe.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by VMC on 2010-02-22
What graphics card?

```
lspci|grep VGA
```

Maybe try booting with  ***nomodeset*** , at the tail end of linux line.

---

### Post by gmoore777 on 2010-02-22
$ lspci|grep VGA
  01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2)

---

### Post by gmoore777 on 2010-02-22
I edited /etc/default/grub
and added what you said to this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

and rebooted. No improvement. /var/log/Xorg.5.log
has same errors.

I rebooted again, and hit "e" for edit in the grub menu.
I don't see the edit I made above. So then I made the edit on the spot. Hit <CTL>-X, to boot from there. Same problem. (blank/black screen)

---

### Post by VMC on 2010-02-22
I don't have a nVidia , but Intel. I have seen, however several topics on the subject using nVida. Also, check out this [blog]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html") on the subject.

---

### Post by gmoore777 on 2010-02-23
If I put the 32-bit LucidLynx LiveCD (that I burned a couple weeks ago) and boot up, it works: I get i nice display. So if the LiveCD can do it, what the heck do I need to do to get the installed LucidLynx to do the same.

I have a 64-bit LucidLynx up and running as well, using the same monitor, but different video card/chip. What configuration files or packages should I be comparing to see what's broken.

Or what configuration files and packages should I be noting with the machine with the LiveCD in it, for when I reboot it with the installed LucidLynx, to compare with.

(I know if I reinstall LucidLynx on the machine, it will all work, but really, I (or someone else) should know what the one command I need to do to repair this situation.)

Maybe I should purge some nVidia or X packages, then install them again.

---

### Post by gmoore777 on 2010-02-23
FYI:
I `dpkg --purge` all packages with "x11", "xserver", "nvidia" in the name. Then reinstalled them via `apt-get install --reinstall`.

That didn't help. 

Giving up.

Will be reinstalling 32-bit LucidLynx. (this is ridiculous)

---

### Post by gmoore777 on 2010-02-23
not giving up yet.
just found these 2 links:

This link:
[http://www.webupd8.org/2010/02/ubuntu-officially-switches-to-nouveau.html](http://www.webupd8.org/2010/02/ubuntu-officially-switches-to-nouveau.html)
says that LucidLynx has switched from nVidia driver to Nouveau driver. (that posting is dated 2/19/2010)

This link is the evaluation page for the Nouveau driver on LucidLynx.

So I now I think that the upgrade last week, must have tried
to make the switch to my drivers, 
and did a poor job at that.

I've posted my "evaluation" on that last site in hopes of getting some help. (otherwise, I will be starting from scratch)

---

### Post by gmoore777 on 2010-02-23
ok, now my console comes up fine if I choose the kernel without
the "-pae" suffix.
(and maybe doing all those other gyrations above helped as well.)

---

### Post by Awareness on 2010-02-27
may i ask you what did you do?

I am upgrading karmic to lucid in a vbox box. I think im having the same issue you were having...

---

