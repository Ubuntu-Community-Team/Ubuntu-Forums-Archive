---
title: "Cannot boot Ubuntu 10.04"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by 65Hyper on 2010-11-12
I installed using USB, I formated the hard drive that has Windows because I want Ubuntu my main operating system. I can boot from USB, but when booting after installation it said

[Some. Numbers] Disabling IRQ #4
[Some. Numbers] Disabling IRQ #5
[Numbers      ] Disabling IRQ #1
[Numbers      ] Disabling IRQ #1
[Some. Numbers] USB not accepting adress number 11 error-numbers

Boots to another one...

*moving quickly*         _ _
                         _ _
                         _ _
                         _ _
                         _ _
Boots again...
   afew4524rqwkfgrdmgsmekfresdmhbks5rthmgelkawfzgtis9rhwzmrklfmrhlksm5eglwame,sfmrhkrth
fwheufaw4g9i4jtwfgrmsgms,5et9f9wrq9384rw8tawu0fdurh9e0yug049wf9uaw4gu0a4gujegj
3ruaozgjs90eguw4fhjgseltgjaw4jglakwgma4gw *moving quickly*
Boots again with a cursor that has the loading sign. then never loads. I know ACPI is not enabled in my computer, but how do I disable it on Ubuntu?

---

### Post by cybergnome on 2010-11-13
Formatting isn't the step to keep the device from booting.  You need to remove the boot flag on the partition you formatted.  Or, disable booting in the BIOS on that drive.  Or, you could move the USB device up on the boot order in the BIOS so that it boots ahead of the hard drive.  :)

---

### Post by sikander3786 on 2010-11-13
Hi.

You need to make your USB drive as the first boot device as mentioned in the above post.

How was the USB created? That output doesn't seem to me like your computer is booting from USB or even trying to boot from it. You can create a Live USB following guide lines here.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

For acpi and other boot options, see this.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

