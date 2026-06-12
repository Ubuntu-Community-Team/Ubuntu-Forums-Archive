---
title: "tiny setup text"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by pcreqeust on 2014-04-26
Installing lubuntu 14.04 and the text is absolutely tiny in the dialog boxes during and after install. Dell Dimension 4550 from a decade+ ago.

This seems like a bug.  Looked fine on a laptop.

---

### Post by SeijiSensei on 2014-04-26
Does the machine have an NVIDIA graphics adapter?  I've seen this problem on machines with NVIDIA cards in the past.  If you're comfortable with the command prompt, here's an overview of how to fix it.

1) Boot the machine into recovery mode, open a console, and run nvidia-xconfig.  It should create a file called /etc/X11/xorg.conf.  If you choose the "root shell" option from the recovery menu, you'll first need to remount the root filesystem read/write like this:
```
# mount -o remount,rw /
```
Note there is no space after the comma.  Then run "nano /etc/X11/xorg.conf".  You don't need sudo in this instance since you have root privileges by default.

2) In the Monitor section [add the line](http://www.mythtv.org/wiki/Specifying_DPI_for_NVIDIA_Cards):
```
    Option    "DPI"  "100x100"
```

3) Save the file, exit the recovery shell, and choose the menu entry to continue the boot process.  Any better?

---

### Post by pcreqeust on 2014-04-26
My monitor (sony hdtv) unfortunately will not display anything (recovery options) during bootup after the Dell startup screen.  I didn't try running nano /etc/X11/xorg.conf while in the regular desktop (non recovery mode). 

I did run Customize Look and Feel, and bumped up some text number from 11 to 40, and that made some things readable now.  But many things like title bar text is still tiny.  I coun't find any info on the Video card in Profiler.

---

### Post by SeijiSensei on 2014-04-26
Try opening a terminal and running 
```
lspci | grep VGA
```
That will show what graphics adaptor(s) you have.  See an NVIDIA?

---

### Post by pcreqeust on 2014-04-26
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] 128 PRO Ultra AGP 4x

---

### Post by SeijiSensei on 2014-04-26
Well, the NVIDIA solution won't help with that, I'm afraid.  [I don't think ATI supports that adapter in Linux any more either]("http://ubuntuforums.org/showthread.php?t=2219411&p=13000995&viewfull=1#post13000995").  You'll have to rely on the open-source driver, which is the one you're probably running already.

---

### Post by pcreqeust on 2014-04-26
So, why is the text so small?  Why is it related to driver?

---

