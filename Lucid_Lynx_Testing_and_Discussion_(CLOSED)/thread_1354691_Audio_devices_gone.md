---
title: "Audio devices gone"
date: 2009-12-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by vhaarr on 2009-12-14
Hey!

Today I decided to reboot for the new -8 kernel, and when I got back in xfce, I didn't have any audio devices except "Dummy Output"!

So, I rebooted and changed back to the -7 kernel which I had been using previously, because I know everything works there.

But still nothing!

aplay -l doesn't list any devices.
pavucontrol only lists "Dummy Output".
the pulse volume "applet" only lists "Dummy Output".

I tried modprobe -r snd_hda_intel and then modprobe snd_hda_intel, no errors, but no devices either.

lspci shows
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
like it should.

No apparent errors in any of the /var/log files.

Help? :D

---

### Post by ranch hand on 2009-12-14
Works fine on this box.

---

### Post by Gina on 2009-12-14
Fine here too.

---

### Post by vhaarr on 2009-12-14
I just fixed it, and the problem was simple;

I had removed GDM and was using XDM to log in to my xfce desktop.

Reinstalling GDM and rebooting "fixed" it.

Obviously GDM does some magic for ubuntu that should be handled at some other level.

---

### Post by aapo4 on 2010-04-08
I'm using openbox without any login manager. I realized I have gdm still installed and when I removed it, my audio breaks. Pavucontrol shows Dummy Output.

I reinstalled gdm and now audio are working again. Weird.

---

