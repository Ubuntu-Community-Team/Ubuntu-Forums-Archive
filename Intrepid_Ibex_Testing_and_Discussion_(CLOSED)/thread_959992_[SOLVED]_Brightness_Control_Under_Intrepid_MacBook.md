---
title: "[SOLVED] Brightness Control Under Intrepid MacBook Pro Penryn"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mostlyalive on 2008-10-27
Under Intrepid Release Candidate with Pommed installed all of my hotkeys work except for brightness. The keys do nothing. Furthermore, xbacklight claims that I don't have any supported devices which is clearly untrue as gnome-power-manager manages to dim my screen when not on AC power. I would like finer grained control than that though preferably using my hotkeys as under Hardy. But getting xbacklight to work would be enough.

---

### Post by cyberdork33 on 2008-10-27
I think there is a bug. A patch has been submitted and fixed packages are in the Mactel-Support PPA

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/289520)

---

### Post by mostlyalive on 2008-10-27
Thanks for your quick reply, but that isn't it, I don't think. I already had the mactel ppa in my sources and picked up the new version a few hours ago... also when connecting/disconnecting AC power the brightness change is almost instant so I don't think I'm suffering from the same problem as in that bug.

---

### Post by cyberdork33 on 2008-10-27
> **mostlyalive said:**
> Thanks for your quick reply, but that isn't it, I don't think. I already had the mactel ppa in my sources and picked up the new version a few hours ago... also when connecting/disconnecting AC power the brightness change is almost instant so I don't think I'm suffering from the same problem as in that bug.
OK, give me a sec... I have a MacBookPro4,1 that I can test the RC on...

EDIT: Well, nothing works at all for me so apparently the functions are all dependent on extra packages, but I cannot install them right now. Sorry. Might wait for kosumi68 to respond. He can probably help.

---

### Post by mostlyalive on 2008-10-27
O.K. thanks anyway. Yes, I figured it would be you or he that would come up with something.

---

### Post by kosumi68 on 2008-10-27
1. pommed is not needed, deinstall it to avoid confusion.

2. you need the mbp_nvidia_bl kernel module installed in /etc/modules.

3. hal might interfere: remove your macbook model from /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi.

4. LCD backlight should work automatically via gnome-power-manager which uses xrandr (same as xbacklight). Use the mactel version of g-p-m.

5. Keyboard backlight works through the hal-applesmc package.

Hopefully these things does it for you :-)

---

### Post by mostlyalive on 2008-10-27
Thank you. That was it, I tossed pommed away and added the module, one reboot later and success.

---

### Post by kosumi68 on 2008-10-27
> **mostlyalive said:**
> Thank you. That was it, I tossed pommed away and added the module, one reboot later and success.

Great! Would you mind marking the thread as SOLVED? It is helpful to others who come across the same problem.

---

### Post by herzzreh on 2008-10-28
> **kosumi68 said:**
> 1. pommed is not needed, deinstall it to avoid confusion.

2. you need the mbp_nvidia_bl kernel module installed in /etc/modules.

3. hal might interfere: remove your macbook model from /usr/share/hal/fdi/policy/10osvendor/10-macbookpro-utils.fdi.

4. LCD backlight should work automatically via gnome-power-manager which uses xrandr (same as xbacklight). Use the mactel version of g-p-m.

5. Keyboard backlight works through the hal-applesmc package.

Hopefully these things does it for you :-)

This won't work for a Macbook 2.1, will it?

---

### Post by mostlyalive on 2008-10-28
I'm not positive, but I don't think so. If I recall I found a bug somewhere related to the file 10-macbookpro-utils.fdi... and it said it only needed to be fixed for 3,1 and up. On yours it "should" work out of the box I think?

---

