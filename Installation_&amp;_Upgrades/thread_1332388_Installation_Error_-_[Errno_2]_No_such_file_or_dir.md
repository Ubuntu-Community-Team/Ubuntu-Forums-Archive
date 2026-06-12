---
title: "Installation Error - [Errno 2] No such file or directory: '/taget/boot/vmlinux-2..."
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by uonedang on 2009-11-20
Hi all,

I built a liveCD with installation option ... but when I install the image on my server (tested on virtual server kvm/qemu, and real server with reformatting the hard drive) .. 

I got the following error when the installation process was about to complete ... ( 78 % copying file ) ... 

====================================================
The installer encountered an error copying file to the hard disk:
[Errno 2] No such file or directory: '/target/boot/vmlinuz-2.6.31-14-generic'

This is often due to faulty hard disk .....
====================================================

It also failed in the simulation (kvm/qemu) ... I am not sure what is missing from the *.iso ... 

When I run the *.iso as liveCD .. it came up OK .... 

Any suggestion what may have been wrong or missing ... 

Thanks

Dang

---

### Post by uonedang on 2009-11-20
Hi all,

I rerun the installation from the same iso image.. and I got different error (this error is  repeatedly happened ):

============================================
Installation System 

Creating ext4 file system for / in partition #1 of SCSI 1 (0,0,0..)

and the pop up error window:

Installed Crashed

(most recent call last)
File "/usr/lib/ubiquity/bin/ubiquity" line 457 in <module> main (oem_config)
File "/usr/lib/ubiquity/bin/ubiquity" line 444 in  main install(query=options.query)
File "/usr/lib/ubiquity/bin/ubiquity" line 245, in install ret-wizard.sun()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk-ui.py line 465 in run self.process_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/gtk-ui.py line line 978 in process_loop

===========================================


Please let me know if there is any suggestion ?

Thanks,

Dang

---

