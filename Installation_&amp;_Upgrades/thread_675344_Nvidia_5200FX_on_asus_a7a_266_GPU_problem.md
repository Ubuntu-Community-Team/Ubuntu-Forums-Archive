---
title: "Nvidia 5200FX on asus a7a 266 GPU problem"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by kDDs on 2008-01-22
Ok so i have the latest ubuntu 7.10 and after installing the driver for my nvidia 5200 (From the "restricted driver" control panel) I get a problem where the screen doesn't properly connect. Im on a CRT on that comp and it just keeps clicking but no picture occurs...

I've drawn a few conclusions myself... here goes...

-The driver could be trying to make the monitor refresh to quickly/slowly (if thats the problem i don't know how to change it!!)

-As its an old mobo i had to installed ubuntu at "the start of the disk" so it woudn't return error 15/18 or whatever it was. Is it possible that the driver needs to be in this section to? (A bit of a longshot..)

Neway what are your suggestions? I can;t see ANYTHING so any suggestions would have to involve using the recovery console. I have also tried re-installing ubuntu on that comp, but it hasn't worked. Thanks in advance for any suggestions!

---

### Post by overdrank on 2008-01-24
> **kDDs said:**
> Ok so i have the latest ubuntu 7.10 and after installing the driver for my nvidia 5200 (From the "restricted driver" control panel) I get a problem where the screen doesn't properly connect. Im on a CRT on that comp and it just keeps clicking but no picture occurs...

I've drawn a few conclusions myself... here goes...

-The driver could be trying to make the monitor refresh to quickly/slowly (if thats the problem i don't know how to change it!!)

-As its an old mobo i had to installed ubuntu at "the start of the disk" so it woudn't return error 15/18 or whatever it was. Is it possible that the driver needs to be in this section to? (A bit of a longshot..)

Neway what are your suggestions? I can;t see ANYTHING so any suggestions would have to involve using the recovery console. I have also tried re-installing ubuntu on that comp, but it hasn't worked. Thanks in advance for any suggestions!

HI and have you  tried and boot into recovery mode. Then reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Then use the command ```
reboot
``` or startx,  hopefully this will get you to a GUI,

---

### Post by kDDs on 2008-01-24
Yer that got my back the GUI.... but still i really want the drivers installed... how can i do it without it screwing up?

---

### Post by osonegro on 2008-01-24
I was able to install my NVIDIA Gforce 5200FX by installing the program Envy.  It is available at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

After reboot I got a black screen but by using CTRL-ALT-+ on the num pad I was able to get to a resolution that my monitor and card liked.

Al

---

### Post by kDDs on 2008-01-24
I already tried envy, forgot to mention that.

Envy came with a similar problem only instead of nothing it had a lot of white rectangles over the scren that flickered... you couldn't make any sense of them of course!

Ill re-try envy, configuring the xorg myself

---

### Post by kDDs on 2008-01-24
Ok i tried it, and as i thought, no difference. It didn't come up with the dialogue to edit xorg. Any command i can use to allow me to edit it?

---

### Post by overdrank on 2008-01-24
> **kDDs said:**
> Ok i tried it, and as i thought, no difference. It didn't come up with the dialogue to edit xorg. Any command i can use to allow me to edit it?

HI and you can edit you xorg with the command ```
gksudo gedit /etc/X11/xorg.conf
```
Have you tried to adjust the resolution with the nvidia-settings ```
gksudo nvidia-settings
```

---

### Post by kDDs on 2008-01-25
All of those commands returned errors....

---

### Post by overdrank on 2008-01-25
> **kDDs said:**
> All of those commands returned errors....

Ok could you post the output of this command ```
 cat /etc/X11/xorg.conf
``` and what errors did you get from the previous command ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by kDDs on 2008-01-26
The first one said 

> "cat: /etc/X11/xorg.config: No such file or directory"...

that might be the problem...?!

The other command said 

> "(gksudo:5904): gtk-warning **: cannot open display"

---

### Post by overdrank on 2008-01-26
> **kDDs said:**
> The first one said 

...

that might be the problem...?!

The other command said

Ok is the restricted driver enabled? If so disable then reboot and try and enable them again. I have seen this issue a couple of times and the driver was enabled but not in use.

---

### Post by kDDs on 2008-01-28
Didn't work.... any other suggestions? Could it possible be a BIOS setting thats wrong?

---

