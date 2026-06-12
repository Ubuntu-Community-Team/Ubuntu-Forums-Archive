---
title: "Ubunto 6.06 Dapper LiveCD broken when BIOS primary graphics dev is xcrs a PCI bridge"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by roytobin on 2006-06-09
Ubunto 6.06 Dapper LiveCD broken when BIOS primary graphics device is across a PCI bridge

Scope: running from 6.06 CD w/o installing (evaluation mode)

Subsystem: "Configuring X" portion of the LiveCD boot has bug

Setup: On a Dell OptiPlex GX110 that has built-in Intel i810 graphics as well
as a Nvidia Riva TNT2 graphic controller PCI card, with the later marked
as "default" in the BIOS, the Dapper LiveCD is broken.  This is not a
two-head setup -- the single monitor is connected to the Nvidia controller
only.  This is done for the superior graphics capability of the NV hw.

Symptom: Dapper desktop-i386.iso will boot the VESA (700x420@70Hz) portion fine,
using the Nvidia controller, which is correct for this is the primary
graphics controller.  Just after the message "starting GNOME X server"
(or something close to that), the screen goes blank, and the cursor in
the upper left isn't blinking.  The CD won't eject (presume still locked
in as mounted), yet the keyboard numlock will toggle.  Keying ctrl-alt-F1
doesn't work, Ctrl-c doesn't work, Ctrl-alt-del doesn't work.

I had tried booting in "safe" graphics mode with no help.

I had tried removing the 'xforcevesa' argument to the boot command line
using F6 (additional options) with no help.

Debugging: Helpful tips the Ubuntu forum indicated I should try to break
out of the graphics boot process with Ctrl-alt-F1, which I believe is
a way to get a virtual console in non-graphics (BIOS) mode.  I didn't
know exactly when to do this, so I hit Ctrl-alt-F1 about once per second
starting with the boot message "configuring restricted drivers."  I also
threw in some Ctrl-C's for good measure.  I ended up at a BIOS console
logged in as the LiveCD demo user 'ubunto' at a shell prompt.

Evidence: from here, I was able to look at /etc/X11/xorg.conf and confirm
that it had indeed been configured X to use the vestigial (non-primary)
i810 graphics controller.  I was also able to inspect /var/log/Xorg.0.log
to confirm the PCI probe successfully detected the nVidia card, and even
has an asterisk by it, which I theorize indicates that it is the default
(aka primary):

 (--) PCI: (0:1:0) Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] rev 3, Mem @ 0xf4000000/26, 0xff000000/19
 (--) PCI:*(1:7:0) nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] rev 21, Mem @ 0xfd000000/24, 0xf8000000/25, BIOS @ 0x80000000/16

The useful X log eventually discloses the root cause of the problem:

  (II) Primary Device is: PCI 01:07:0
  (WW) VESA: No matching Device section for instance (BusID PCI:1:7:0) found

That is, the Ubunto-specific "Configuring X" portion of LiveCD boot
algorithm is incompatible with the X Window System Version 7.0.0.
The former has the bug.

Solution: I was able to successfully go into graphics mode by adopting
portions of my working Redhat 7.0's /etc/X11/XF86Config, by fixing BusID,
and calling out the 'Driver' to be either 'vesa' or 'nv.' Both drivers
work, yet the later has much improved performance as one would expect.

Since I was logged in as the 'ubunto' user, I had trouble with device
permissions just running 'startx.'  I theorized no X Display Manger
had been started by the interrupted boot process.  I did 'sudo startx'
with success.

When finally in graphics mode (gorgeous 1600x1200@85Hz) as root I ran
Device Manger and found the nVidia device was depicted across a '82801AA
PCI Bridge' whereas the built-in i810 controller was hierarchically
directly under 'Computer' (not across a bridge.)  I don't know if this
fact fooled the "Configuring X" algorithm to construct an incorrect
xorg.conf or not.

Another theory: on this hw setup, the Intel i810e is PCI device
one (specifically, 0:1:0), whereas the Nvidia is device seven
(specifically, 1:7:0).  Furthermore, the i810 device is listed first
in the PCI probe in /var/log/Xorg.0.log.  Perhaps the "Configuring X"
algorithm constructs /etc/X11/xorg.conf based on the first graphics
device it finds?  I claim it ought to pick the primary device, not the
first (or any other ordinal position) one discovered.

I have all logs & config files, 3572 lines worth.  Contact me if you
want them to further investigate/resolve this bug, with thanks.

RoyT

---

### Post by HughR on 2006-11-09
I'm experiencing the same or similar problem.

Hardware: Dell small form-factor GX115.  Add-in card: nVidia 5200-based.

Distros tried: Ubuntu 6.06, 6.10, knoppmyth, Fedora Core 6 [not enough info about FC6 to be sure that it is the same problem, but it seems likely].

Stupid solution: install ubuntu without card.  Add card.  Boot fails to start GDM and gives console login. "dpgk-reconfigure -phigh xserver-xorg", telling it "nv" as controller family (I forget the exact wording of the question).  This, in fact, isn't enough.  Silly thing leaves the PCI number for the i810 in /etc/X11xorg.conf (Section "Device", line BusID) -- manually edit this to match what lspci tells you.

I don't know how the original installer intuits the device for X, but it is wrong.  X itself (vesa driver and i810 driver) is smart enough not to be willing to use the 810.

Is there a bug report for this?

---

