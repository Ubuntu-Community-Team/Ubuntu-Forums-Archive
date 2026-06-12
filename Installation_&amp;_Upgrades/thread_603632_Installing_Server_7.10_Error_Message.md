---
title: "Installing Server 7.10 Error Message"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by JS2955 on 2007-11-05
Hey First time User. I am trying to install the server edition on an old IBM x series 220 box. Its a P3 833, 512 RAM, 18.2GB SCSI HDD etc. I proceed to install it but at some point I get the error message

> ACPI - Resource is not an IRQ Entry  

The installation starts up fine but then I an error message saying the CD could not be read. I have tryed 3CD's to rule this out. I'm guessing that the errors are related in some way. 

Similar to this thread but as you can see there are no reply s

[http://ubuntuforums.org/showthread.php?t=439353](http://ubuntuforums.org/showthread.php?t=439353)

Any advice would be greatly appreciated. Thanks

---

### Post by James Wilford on 2007-11-05
> **JS2955 said:**
> Hey First time User. I am trying to install the server edition on an old IBM x series 220 box. Its a P3 833, 512 RAM, 18.2GB SCSI HDD etc. I proceed to install it but at some point I get the error message

 

The installation starts up fine but then I an error message saying the CD could not be read. I have tryed 3CD's to rule this out. I'm guessing that the errors are related in some way. 

Similar to this thread but as you can see there are no reply s

[http://ubuntuforums.org/showthread.php?t=439353](http://ubuntuforums.org/showthread.php?t=439353)

Any advice would be greatly appreciated. Thanks


Try putting "noacpi" on the end of the kernel options in grub.

---

### Post by JS2955 on 2007-11-05
Thanks, I did that and it got rid of another error about an MP BIOS Bug that I was having. I still get the original error though :confused::(

---

### Post by az on 2007-11-05
I think that error is benign.  Perhaps the problems you are having are due to your cdrom drive?

---

