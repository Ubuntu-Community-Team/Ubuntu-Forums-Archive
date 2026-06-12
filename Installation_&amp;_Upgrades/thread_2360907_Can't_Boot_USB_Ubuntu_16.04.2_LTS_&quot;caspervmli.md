---
title: "Can't Boot USB: Ubuntu 16.04.2 LTS &quot;/casper/vmlinuz.efi: file not found&quot;"
date: 2017-05-09
forum: Installation &amp; Upgrades
---

### Post by Pieni_Sieni on 2017-05-09
On initial boot of a bootable Ubuntu USB drive; boot loader gives error "**/casper/vmlinuz.efi: file not found**".

*To replicate:*

**Step 1.**

Download ubuntu-16.04.2-desktop-amd64.iso & Rufus 2.14. Write to USB according to official "How to create a bootable USB stick on Ubuntu" instructions.

[[IMG]https://www.elftronix.com/wp-content/uploads/Ubuntu-16.04.2-LTS-Rufus-2.14-thumbnail.jpg[/IMG]]("https://www.elftronix.com/wp-content/uploads/Ubuntu-16.04.2-LTS-Rufus-2.14.png")


[B]Step 2.

[/B]Boot drive. The first screen I see is this.

[[IMG]https://www.elftronix.com/wp-content/uploads/vmlinuz-file-not-found-thumbnail.jpg[/IMG]]("https://www.elftronix.com/wp-content/uploads/vmlinuz-file-not-found.jpg")

---

### Post by wildmanne39 on 2017-05-09
Please use thumbnails or Url's when posting images because many people have slow internet connections and loading pages with large images is very difficult for them.

---

### Post by Pieni_Sieni on 2017-05-09
Thank you for the advice. I changed to thumbnails optimized with ImageOptim; around 10KB each.

---

### Post by Pieni_Sieni on 2017-05-09
[SIZE=3]This seemed to be a problem with the environment/compatibility issue with USB drive.

The above problem occurred when running WMware Fusion on Mac OS; with Windows 7.

Replicating the above steps with a native Windows 10 environment worked fine![/SIZE]

---

