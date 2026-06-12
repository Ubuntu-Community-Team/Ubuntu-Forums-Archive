---
title: "where is usb kernel directory located at?"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by gabak on 2010-01-03
hi i have to install a webcam and i need to to this. Thank you guys for you help in advance.

Download and Patch
spca5xx-LE is provide as patch to the main kernel for convenience
to set up the patch you need the compressed patch:
usb-2.4.31LE06.patch.gz is the kernel patch to apply at the 2.4.31 kernel
or linux-2.4.31LE08.patch.tar.gz full kernel patch with support of the Usb Wifi ZD1211 and RT2570

	
	[COLOR="Red"]**patch -p1 < usb-2.4.31LE06.patch in the usb subdirectory of the kernel**[/COLOR]
	or
	patch -p1 < linux-2.4.31LE08.patch for the full kernel
your kernel have now support for the spca5xx-LE webcams as the other (ov511 pwc ....)
and maybe some Usb Wifi adaptator like the Linksys WUSB54GV4 or the D-LINK DWL-122 B1 or the Sitecom WL-113 :)
you need to configure the kernel with 
	make menuconfig
	and update the fields if needed:
		CONFIG_MODULES=y
		CONFIG_VIDEO_DEV=m
		CONFIG_USB=y
		CONFIG_USB_DEVICEFS=y
		CONFIG_USB_SPCA5XX=m
	save exit 
then compile
	make 
	make modules

---

