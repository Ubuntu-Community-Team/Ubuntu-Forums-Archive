---
title: "[SOLVED] remove extra kernels???"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by Victormd on 2008-06-03
After todays upgrade there are now 3 different kernels installed on my machine and I was wondering if there is a way to remove the two oldest kernels without affecting the existing install and if so, how?

I know I can remove them from the GRUB menu but I want to keep my ubuntu installation "clean"... this may be my previous windows experience/mentality coming into play and I'm not sure it's necessary, but I'd still like to know how to do it...

---

### Post by bigken on 2008-06-03
you can remove your old kernels in synaptic but be very careful

---

### Post by Victormd on 2008-06-03
Very careful with what? What could happen? Is there a risk that removing the old kernel will tamper with the new one? :confused:

In windows I would always try to clean my registry and remove unnecessary windows components and stuff like that to keep windows running as clean and smooth as possible. Is this something that I should be worried about with Ubuntu? Can having the other kernels installed result in extra stuff being loaded and taking up resources?

---

### Post by Joeb454 on 2008-06-03
It wouldn't tamper with them, but should something go wrong with the newer kernel, you would be left with an unbootable machine - so I'd recommend removing the oldest, and then hiding the 2nd one from your menu.lst :)

---

### Post by bigken on 2008-06-03
its always a good idea to leave at least one old kernel so you can rervert back to it 
what meant about being careful is not remove your current kernel

this not windows dont worry about things being installed

---

### Post by qamelian on 2008-06-03
> **Victormd said:**
> Very careful with what? What could happen? Is there a risk that removing the old kernel will tamper with the new one? :confused:

In windows I would always try to clean my registry and remove unnecessary windows components and stuff like that to keep windows running as clean and smooth as possible. Is this something that I should be worried about with Ubuntu? Can having the other kernels installed result in extra stuff being loaded and taking up resources?
Having the old kernels installed won't have any negative impact on your computer. It's actually a good idea to keep one or more kernels previous to the newest one in case a bug or other problem slips into a kernel update. At least by retaining a previous kernel, you have the option of booting into the older one to avoid the issue.

---

### Post by Victormd on 2008-06-03
Thanks!
I guess that answered all my questions!

---

### Post by Vrekk on 2008-06-03
i know this problem is sloved, but can i at least hide them on the list?

---

### Post by Joeb454 on 2008-06-06
> **Vrekk said:**
> i know this problem is sloved, but can i at least hide them on the list?

Yes!

```
gksudo gedit /boot/grub/menu.lst
``` Run that from a terminal, and then comment out the lines you don't want to appear by placing a '#' at the beginning of the lines :)

---

