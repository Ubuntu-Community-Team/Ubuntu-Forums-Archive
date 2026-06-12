---
title: "Fiesty and fglrx"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by AquaFox90 on 2007-04-24
I just upgraded to fiesty, a long, tiring install, and I got it working except for the fact that if I use fglrx I get the 'No device found' error. I want 3D, I am a gamer and love enlightenment so please help me somehow :). Thanks.

I have the restricted modules and fglrx installed. All the log file says is (EE) No devices found.

Thanks.

---

### Post by rbmorse on 2007-04-24
you have to do some things to a fresh install:

1. backup /etc/X11/xorg.conf and then edit to add the following to the end of the file:

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

save xorg.conf

2. from a console run

```
sudo aticonfig --initial
```

3. from a console run

```
sudo aticonfig --overlay-type=Xv
```

4.Make sure all work in other windows is saved then restart x with <ctrl>+<alt>+<backspace>

---

### Post by jdong on 2007-04-24
Also, what kind of video card is it?

---

### Post by AquaFox90 on 2007-04-26
It did not work I got a device not found in Xorg.0.log. It's an Ati Radeon 9200 SE. It was working in Edgy.. Are the restricted modules working well? I might try older kernel versions.

---

### Post by jdong on 2007-04-26
The most recent releases of fglrx have dropped support for your chipset. Since AMD has effectively said that they are only supporting their newest versions (as opposed to nVidia pledging security and critical bugfixes to 3 branches of their drivers),Ubuntu has no choice from a support point of view than to follow fglrx's release schedule.

If you are dissatisfied with this decision, let AMD know. Otherwise, you can either manually install an old, unsupported version of the driver, or use the Open Source ati driver.

---

### Post by AquaFox90 on 2007-04-27
I want to use the open-source ATi driver, what's it called and is there a guide to installing it?

---

### Post by thallam on 2007-04-27
A search of Yahoo gives - [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

Looks like it might be of some help but not tried it.

---

