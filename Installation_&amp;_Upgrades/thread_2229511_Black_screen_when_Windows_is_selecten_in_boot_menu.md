---
title: "Black screen when Windows is selecten in boot menu after Ubuntu installation."
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by soxterix on 2014-06-13
I have hp probook 430 g1 with pre-installed Windows 7. I wanted to install Ubuntu alongside Windows but all four primary partitions was created and used so I have changed size of Windows partition and removed HP_TOOLS partition. I have extended partition with logical partition for Linux. I have installed Ubuntu 14.04 and now when I chose WIndows in boot menu I see black screen with very short horizontal stripes. It lasts about 10-15 seconds and after that Windows starts normally.
Do you know what can cause this situation?
This is photograph of the screen I have described.
[ATTACH=CONFIG]253930[/ATTACH]

---

### Post by LastDino on 2014-06-13
You resized those partitions using Windows or Ubuntu live?

---

### Post by soxterix on 2014-06-13
It was clean Windows installation but I have defragmented hard drive and I used GParted to resize partition.

---

### Post by LastDino on 2014-06-13
You should always use Windows partition tool to partition windows drives to create an extra space for Linux.  You're lucky that its still booting.

---

### Post by soxterix on 2014-06-14
Thank you very much for your reply.
I reinstalled everything, used Windows tool to resize partition and it works fine.
I didn't know that it's important to use Windows software to do that. Thanks.

---

### Post by soxterix on 2014-06-15
It looks like not everything is all right.
This screen still appears from time to time. It looks like it appears when I boot Ubuntu and then restart computer and boot Windows. If I choose Windows after computer is turn on then this screen doesn't appear. And now computer freezed on this screen - Windows didn't boot.

---

