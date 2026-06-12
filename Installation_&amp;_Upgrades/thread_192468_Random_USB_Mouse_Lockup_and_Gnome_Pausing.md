---
title: "Random USB Mouse Lockup and Gnome Pausing"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by sgbeamer on 2006-06-08
I upgraded from Breezy.  The update manager worked great!  Thanks.

My USB mouse works fine for a while then goes into slow motion.  About the same time Gnome starts pausing, firefox loads but then the screen freezes for a while but it comes back eventually at full speed.  If I go to a terminal screen, I'm getting an error message like this:

usb 5-8 not accepting address 3, error 110

Any clues?  I don't think it's a Gnome problem because the other WM do the same Icewm and KDE.  It must be usb related.

I am running the 386 version of Ubuntu on a Mach Speed 939 AGP motherboard with Athlon 3200, NVidia Card, VIA K8T800 Pro North Bridge, VIA VT8237 South Bridge, VIA VT6103 10/100 ethernet, AC'97Audio, 1G RAM

---

### Post by ramcosca on 2006-06-09
I get the same problem sometimes when my ZSNES freezes up... let's see if someone has a solution or at least enlight some knowledge to us.

---

### Post by sgbeamer on 2006-06-09
As a quick follow up I freed up some space on my backup drive and did a fresh install of Dapper and the same issue occurred.  I'm thinking it might be a kernel or kernel module problem from the error messages.  I'm going to build a vanilla kernel and see if that removes the problem.

---

### Post by sgbeamer on 2006-06-10
Tried a vanilla kernel 2.6.16.20, same outcome.  I booted into my latest Breezy kernel 2.6.12-10-386 and all is well.  Dapper seems to be doing fine with the older kernel.  I guess I'll just run this way until I get it sorted out.  Problem seems to be USB resetting

Jun  8 03:46:38 localhost kernel: [4295263.276000] usb 5-8: reset high speed USB device using ehci_hcd and address 3
Jun  8 03:46:49 localhost kernel: [4295274.912000] usb 5-8: reset high speed USB device using ehci_hcd and address 3
Jun  8 03:47:01 localhost kernel: [4295286.548000] usb 5-8: reset high speed USB device using ehci_hcd and address 3
Jun  8 03:47:11 localhost kernel: [4295297.078000] usb 5-8: reset high speed USB device using ehci_hcd and address 3
Jun  8 03:47:22 localhost kernel: [4295307.506000] usb 5-8: USB disconnect, address 3

---

### Post by sgbeamer on 2006-06-11
I found the problem to be in the configuration of EHCI when I compared the new config file to the previous breezy config file (2.6.12-10-386)
 #
 # USB support
@@ -2648,8 +2871,9 @@
 # USB Host Controller Drivers
 #
 CONFIG_USB_EHCI_HCD=m
-CONFIG_USB_EHCI_SPLIT_ISO=y
-CONFIG_USB_EHCI_ROOT_HUB_TT=y
+# CONFIG_USB_EHCI_SPLIT_ISO is not set
+# CONFIG_USB_EHCI_ROOT_HUB_TT is not set
+# CONFIG_USB_ISP116X_HCD is not set
 CONFIG_USB_OHCI_HCD=m
 # CONFIG_USB_OHCI_BIG_ENDIAN is not set
 CONFIG_USB_OHCI_LITTLE_ENDIAN=y
@@ -2660,17 +2884,16 @@
 #

The new config that worked for me to solve the problem is (I built a vanilla 2.6.16.20 kernel from source):

#
# USB support
#
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB=m
# CONFIG_USB_DEBUG is not set

#
# Miscellaneous USB options
#
CONFIG_USB_DEVICEFS=y
# CONFIG_USB_BANDWIDTH is not set
# CONFIG_USB_DYNAMIC_MINORS is not set
# CONFIG_USB_SUSPEND is not set
# CONFIG_USB_OTG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_EHCI_HCD=m
CONFIG_USB_EHCI_SPLIT_ISO=y
CONFIG_USB_EHCI_ROOT_HUB_TT=y
# CONFIG_USB_ISP116X_HCD is not set
CONFIG_USB_OHCI_HCD=m
# CONFIG_USB_OHCI_BIG_ENDIAN is not set
CONFIG_USB_OHCI_LITTLE_ENDIAN=y
CONFIG_USB_UHCI_HCD=m
CONFIG_USB_SL811_HCD=m

---

