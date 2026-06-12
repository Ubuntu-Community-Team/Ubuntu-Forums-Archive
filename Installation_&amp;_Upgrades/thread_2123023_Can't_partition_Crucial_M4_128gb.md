---
title: "Can't partition Crucial M4 128gb?"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by nachomaster on 2013-03-06
Hi, I want to install Ubuntu 12.10 on my M4 128gb ssd drive. I have windows 8 installed on it with a few programs. I have 72gb left of space which is plenty to install Ubuntu. I tried using the disk manager in windows 8 to shrink the volume but it wont let me shrink it past 3gb. Using a usb and running the ubuntu installer i cant partition the ssd either. What am I doing wrong? How can I seperate around 30gb for root and swap? I have 8 gigs of RAM. Any suggestions? Thanks!

---

### Post by Cheesemill on 2013-03-07
Try defragging it a couple of times from Windows first, this sometimes allows the disk management software to shrink it further.

---

### Post by nachomaster on 2013-03-07
defragging an ssd should not be done. It is pointless and it reduces the lifespan of the ssd. Any other suggestions :S

---

### Post by Cheesemill on 2013-03-07
It's pointless for performance reasons, yes.

But it does usually consolidate all of the used blocks at the start of the drive which leaves you with more contiguous free space to shrink the Windows volume.

---

