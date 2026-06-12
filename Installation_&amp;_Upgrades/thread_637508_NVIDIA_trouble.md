---
title: "NVIDIA trouble"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by smukketorben on 2007-12-11
Hi,

I have just installed 7.10 and it is a pleasure so userfriendly it has been. I just have one problem:

I have installed restricted extras to use my NVIDIA GF4 GFX, but I cannot change resolution without the graphics to mess up. When I try to select another monitor with higher resolution than generic, windows miss their title bar, some cannot show the contents etc.

Any ideas??

Regards and thanks

Torben

---

### Post by Thanoulis on 2007-12-11
Try to change resolution editing your /etc/X11/xorg.conf file, not from the GUI application...:)(I had the same problem)

---

### Post by smukketorben on 2007-12-11
Hi

I will try this to edit xorg.conf. What do I have to write. Even if I just adjust the vertical og horisontal frequencies in xorg.conf, it messes up. Please mail the relevant part of xorg.conf.

Best Regards

Torben

---

### Post by ArchCorsair on 2007-12-11
Are you sure you are using the correct driver?

---

### Post by smukketorben on 2007-12-11
Hi,

I have installed Restricted Extras and the driver is set to be "NVIDIA". I tried installing nvidia-glx-new, but my GF4 is to old for that.

Best Regards

Torben

---

### Post by ken_vh on 2007-12-11
If you have a widescreen(16:9 or 16:10):
Did you enable the checkbox that says "widescreen" in the monitor selection window?

This enables the correct screen resolutions. After a reboot, I set the resolution with "sudo nvidia-settings" and I let this tool write my xorg.conf file. Another reboot and all was well :)

---

### Post by smukketorben on 2007-12-11
Hi,

I will try this - nvidia-settings and let it edit the xorg.conf.

Thanks.

Best Regards 

Torben

---

### Post by ken_vh on 2007-12-11
> **smukketorben said:**
> Hi,

I will try this - nvidia-settings and let it edit the xorg.conf.

Thanks.

Best Regards 

Torben

Just make sure you get correct monitor set up first(with the widescreen checkbox checked or not) through the gnome screen configuration program, so you can actually select the correct screen resolution and so it uses the correct refresh rates for that monitor.

Good luck!

---

### Post by Yellowdog428 on 2007-12-11
I was having some of the same problems and installed Envy, now no problems.

It installed the right drivers and even put a Nvidia settings link in system tools!

Cheers

---

### Post by smukketorben on 2007-12-11
Hi again,

I have just tried nvidia-settings, but I cannot tell it the horisontal and vertical refreshrates of my Samsung monitor (1600x1200x75). It just detects the generic monitor capable of 1024x768x75 and nothing more. 

Any ideas?

Best Regards

Torben

---

### Post by ken_vh on 2007-12-11
> **smukketorben said:**
> Hi again,

I have just tried nvidia-settings, but I cannot tell it the horisontal and vertical refreshrates of my Samsung monitor (1600x1200x75). It just detects the generic monitor capable of 1024x768x75 and nothing more. 

Any ideas?

Best Regards

Torben

You shouldn't fill these values in manually.
First go and configure your monitor correctly in: System->Administration->Screen and graphics
When that's set up, you can start using nvidia-settings.

---

### Post by smukketorben on 2007-12-12
Hi,

It messes up, just if I choose the correct monitor and don't change the resolution. I just got the advise to try the nvidia-glx-legacy driver and I will try this afternoon.

Thanks.

Best Regards

Torben

---

### Post by smukketorben on 2007-12-13
Hi,

I got the advise from a Danish LUG to use nvidia-glx-legacy driver. This works with all monitor setting, but unfortunately not with Compiz 3D desktop. The nvidia-glx driver should though work with GF4 cards.

Another possibility is to use Envy to install the latest nvidia driver from nvidia, but I then have to run it everytime I upgrade the kernel.

I will keep on using the nvidia-glx-legacy until the nvidia-glx is updated. How can I se the version numbers of this package??

Regards

Torben

---

### Post by ken_vh on 2007-12-13
In the terminal:
apt-cache show [package-name]

Or you could use the gnome package manager and search for the package there. Then you can right-click and check its properties.

---

