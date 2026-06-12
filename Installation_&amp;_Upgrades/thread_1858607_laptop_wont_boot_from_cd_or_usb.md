---
title: "laptop wont boot from cd or usb"
date: 2011-10-12
forum: Installation &amp; Upgrades
---

### Post by ELD on 2011-10-12
I recently got the lenovo ideapad z570 and i cannot get it to boot into Ubuntu, i tested it on a burnt and cd and a usb stick, when booting the menu that comes up first so you select what to boot is completely distorted and after i select the first option, nothing at all happens.

Any ideas on what to do?

---

### Post by BHEJU on 2011-10-12
"screen distorted"?.. seems like the screen is messed up.. try attaching external monitor..

---

### Post by MAFoElffen on 2011-10-12
> **ELD said:**
> I recently got the lenovo ideapad z570 and i cannot get it to boot into Ubuntu, i tested it on a burnt and cd and a usb stick, when booting the menu that comes up first so you select what to boot is completely distorted and after i select the first option, nothing at all happens.

Any ideas on what to do?
What huh? That is a fairly new laptop with a some good NVidia graphics right?  BlueRay Disk Drive?

Is the ISO you downloaded good? (check the md5sum)  The initial screens should be in VGA.  At the first with the screen/person icon, it you press <esc>, it goes into a low graphics mode to the next screen... Where it has the advanced menu.  <F6> will bring up a dropdown for kernel boot options, which will work with your nvidia graphics...

But that does not explain why your graphics would be distorted in the first 2 screens. Odd.

---

