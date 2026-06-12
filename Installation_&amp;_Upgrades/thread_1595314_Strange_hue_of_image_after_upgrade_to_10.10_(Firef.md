---
title: "Strange hue of image after upgrade to 10.10 (Firefox only?)"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by misetusame on 2010-10-13
Hi,

using the proprietary ATI drive for ATI Radeon HD 2400 XT.

Since upgrading to 10.10 from 10.04, some sites in Firefox display images with the hue off. I mean, the images seem very green and purple. This only applies to some images. All text seems to be displayed correctly, as with the rest of the operating system. A majority of images display with correct colours.

Not sure where to go from here, any pointers?

Thanks.

---

### Post by misetusame on 2010-10-13
It is only in Firefox.

I saved a JPG that was discoloured in Firefox, viewed it in the image viewer, and suddenly it looks fine.

---

### Post by lovinglinux on 2010-10-13
Explanation and solution at [http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html)

---

### Post by misetusame on 2010-10-14
Thanks for the pointer.

Under about:config, setting *gfx.color_management.mode* value to *0* worked.

I suspect that by using the [Color Management]("https://addons.mozilla.org/en-US/firefox/addon/6891/") addon in Firefox and pointing it to a color profile would work, although I won't spend time looking how to do that.

---

