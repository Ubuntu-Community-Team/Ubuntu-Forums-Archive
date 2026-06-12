---
title: "How to install on Toshiba Satellite A665?"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by djuliette on 2010-12-12
I'm trying without success to install 10.10 on a Toshiba Satellite A665 from a USB drive.  It will start to boot then gets stuck on:
NET: Registered protocol family 1

I've tried different iso's and different usb drives.

Other threads have mentioned that setting acpi=off might work but
1) how do I do that and 
2) what else might that effect?

---

### Post by sikander3786 on 2010-12-12
Gain access to the boot options page by pressing any key as soon as the computer starts booting from USB/CD, press F6 and enable apci=off and then try to boot.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Obviously, it disables acpi. More about acpi here.

[http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface)

If that doesn't work, there are 6 boot options under F6 menu and you may want to try all of them one-by-one. Any of them might work magically ;-)

---

