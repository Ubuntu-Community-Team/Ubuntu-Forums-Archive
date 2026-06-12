---
title: "Scanner and Webcam Issues"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by wbar2 on 2010-04-13
I installed 10.04 beta2 on a 32-bit desktop, which has no webcam. It detects and uses my Lexmark x5650 just fine (printing and scanning).

I also installed 10.04 beta2 on a 64-bit laptop, which has an integrated webcam. I can print on my Lexmark x5650, but I have problems scanning. I am updating daily. I had the same issue with 9.10 on my laptop.

When opening Simple Scan from the menu it detects my webcam, but not my scanner. Even if I go to preferences, it is not an option - only the webcam is an option.

When I run sane-find-scanner it does find my x5650:
```

found USB scanner (vendor=0x043d [Lexmark], product=0x013f [5600-6600 Series]) at libusb:002:007
```

But I still can't get Simple Scan to use it. I've tried running it as root with "sudo" in the terminal, with the same results. Any ideas what this might be? Is this a bug (or just user error )?

---

