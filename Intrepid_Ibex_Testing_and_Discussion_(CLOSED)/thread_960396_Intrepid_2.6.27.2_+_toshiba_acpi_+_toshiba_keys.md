---
title: "Intrepid 2.6.27.2 + toshiba acpi + toshiba keys"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sk4os on 2008-10-27
Hello.

I have upgraded from 8.04 to 8.10 and now fnfx (toshiba keys) doesn't work, because it is not suported by the default kernel. I've tried to recompile the kernel with toshiba acpi suport and toshiba keys suport, but it returns this error:

sudo dpkg -i linux-image-2.6.27.2.271008_2.6.27.2.271008-10.00.Custom_i386.deb

.....
.....
.....
.....
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.27.2.271008.postinst line 1181.
dpkg: error processing linux-image-2.6.27.2.271008 (--install):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
linux-image-2.6.27.2.271008


sudo fnfxd:

FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or [http://fnfx.sf.net/index.php?section=doc#kernel](http://fnfx.sf.net/index.php?section=doc#kernel).

sudo toshset:
required kernel toshiba support not enabled.

---

