---
title: "Do I flag /boot as bootable?"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by pedrogent on 2008-03-01
Hello.

I've installed Ubuntu on a number of machines but this is the first time I've tried the text installer. I'm trying my best but it ain't good enough it seems.

So I'm partitioning a new hard drive to install Ubuntu:

/boot
/
/home
swap

Which of these should I flag as bootable?

Furthermore, under 'Typical usage' I see these options:

standard
news
largefile
largefile4

What do these things mean and which should I select for each of the partitions I will be creating?

Thanks very much in advance.

---

### Post by bapoumba on 2008-03-01
I usually place the boot sector on my / (also using the text-mode install) without creating a /boot partition.
For "Typical Usage", I do not recall anything about it. So if "Standard" is selected by default, chances are I left it that way.

---

