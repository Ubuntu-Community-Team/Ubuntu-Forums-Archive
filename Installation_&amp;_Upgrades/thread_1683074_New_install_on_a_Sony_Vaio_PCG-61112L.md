---
title: "New install on a Sony Vaio PCG-61112L"
date: 2011-02-07
forum: Installation &amp; Upgrades
---

### Post by topgun98 on 2011-02-07
Hello,

I just did a fresh install on a Sony Vaio PCG-61112L with nvidia graphics.

The standard live CD did not work, so I used the alternate install CD, which worked great.

Upon booting, however, the screen becomes very garbled.

I assumed this was a graphic issue.  So, I attempted to boot into single user mode so that I can create an xorg.conf file.

However, when I disable the splash screen and try booting into single using mode (using the "single" kernel parameter in GRUB), my system halts at these various points:

[IMG]http://farm6.static.flickr.com/5178/5422430759_9b8f1d738e_z_d.jpg[/IMG]

[IMG]http://farm6.static.flickr.com/5011/5423419060_45c1a21b30_z_d.jpg[/IMG]

[IMG]http://farm6.static.flickr.com/5292/5423763676_2444028f9b_z_d.jpg[/IMG]

And if I disable ACPI, it stops here instead:

[IMG]http://farm6.static.flickr.com/5252/5424172426_24f4c4d024_z_d.jpg[/IMG]

Can anyone tell me why this might be happening?

Thank you, in advance, for **any** help you can offer!  It is greatly appreciated.

---

### Post by topgun98 on 2011-02-07
Sorry, the kernel parameter "nomodeset" did the magic I was looking for.

All is well now.  Well, it will be once I get the nvidia drivers installed.

How do I mark this thread solved?

---

### Post by overdrank on 2011-02-07
> **topgun98 said:**
> 
How do I mark this thread solved?

At the top of the page, Thread Tools. :)

---

