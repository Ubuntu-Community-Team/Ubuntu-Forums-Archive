---
title: "Screen Resolution"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by 1492 on 2010-12-09
I just upgraded from 10.04 to 10.10. However, the screen resolution is changed and the I can't choose the right resolution. Is there any way to fix this?

---

### Post by owiknowi on 2010-12-09
> **1492 said:**
> I just upgraded from 10.04 to 10.10. However, the screen resolution is changed and the I can't choose the right resolution. Is there any way to fix this?

Are the required video drivers for your video card installed (or available)?
Check by running 'Hardware Drivers' from System/Administration.

---

### Post by sikander3786 on 2010-12-09
If you can't find the drivers following the advise in above post:

Which graphics driver is there?

```
lspci | grep VGA
```

We would also want to make sure that you are not running Ubuntu as a Virtual Machine and it is a proper install?

---

### Post by 1492 on 2010-12-09
This is what I got when I put in "lspci | grep VGA" ```
02:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]
```This is not a virtual machine. It is a dual-boot Windows 7 & Ubuntu.

I assume it is installed properly

On Ubuntu 10.04 LTS, the resolution was correct. It was only when I upgraded to 10.10 that I had this problem.[ Additional Drivers.png]("http://ubuntuforums.org/attachment.php?attachmentid=177953&stc=1&d=1291935337")

---

### Post by sikander3786 on 2010-12-10
Try reconfiguring the graphics.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

It if says file not found, ignore and  proceed to the next one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

### Post by owiknowi on 2010-12-10
A workaround I used in openSUSE for a nVidea card:

In the xorg.conf file there often are several resolutions listed.
I used to remove manually all the resolutions not needed.

Maybe this works for you?

Note: this workaround can damage your v-card if used the wrong way!

---

### Post by joshlindem on 2010-12-10
if it is a VM how would one fix it?

I ask becauase I am in a VM and stuck at 800x600 and can't seem to make it go higher.
trying to figure out if there's a way to trick it into thinking I have a higher resolution monitor?

---

### Post by sikander3786 on 2010-12-10
> **joshlindem said:**
> if it is a VM how would one fix it?

I ask becauase I am in a VM and stuck at 800x600 and can't seem to make it go higher.
trying to figure out if there's a way to trick it into thinking I have a higher resolution monitor?
Install VMWare Tools.

[http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html](http://www.vmware.com/support/ws55/doc/new_guest_tools_ws.html)

Or Virtualbox guest additions, whichever applicable.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by joshlindem on 2010-12-10
> Install VMWare Tools.

[http://www.vmware.com/support/ws55/d..._tools_ws.html](http://www.vmware.com/support/ws55/d..._tools_ws.html)

Or Virtualbox guest additions, whichever applicable.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) 

my bad, I should have stipulated.  I'm running a Citrix VM, not VMWare. But with that said I'll double-check the senserver tools.

---

### Post by 1492 on 2010-12-10
It works. Thank you so much.

---

### Post by sikander3786 on 2010-12-11
> **1492 said:**
> It works. Thank you so much.
You are Welcome. Glad to know that it is fixed now :-)

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Happy Ubuntu-ing!

---

