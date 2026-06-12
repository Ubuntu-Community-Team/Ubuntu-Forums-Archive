---
title: "Can't use apt since it shows an error"
date: 2023-09-04
forum: Installation &amp; Upgrades
---

### Post by matefon on 2023-09-04
Hi there,
I tried apt clean, --reinstall the packages, autoremove, and installing the packages separately.
Can someone help me please?
The error is in the screenshot.


Thanks!

---

### Post by Impavidus on 2023-09-04
There are two files that are provided by two different packages on your system, which is an error. One comes from both libgstreamer-plugins-bad and libgstreamer-plugins-good. It only belongs in the latter. Those packages, in particular the former, are not essential. The other conflicting file comes from two different versions of libsgutils. Only one of those is present in currently supported Ubuntu releases. It appears you've got some packages on your system that don't belong there.

Can you tell us which version of Ubuntu is on your computer? And could you simply copy the terminal output as text to your forum post and enclose it in [noparse]```
code tags (like this)
```[/noparse]? That's easier to read and allows me to copy it from your post and paste it somewhere else. And saves you from having to deal with screenshots and attachments.

---

### Post by matefon on 2023-09-04
Okay, of course.
There is another problem: I installed the latest Ubuntu Lobster, but now somehow neofetch thinks it is Kali Linux 2023.2

---

### Post by matefon on 2023-09-04
I just realized that a lot of pictograms are missing from my system, for example the previous and next icons when browsing apps, or the little icons in settings.

---

### Post by ian-weisser on 2023-09-04
> **matefon said:**
> now somehow neofetch thinks it is Kali Linux 2023.2

The most common cause is installing katoolin packages.
Regardless of the cause, Ubuntu to Kali is a one-way trip.
It cannot be undone. Kali makes too many changes.
Time to reinstall.

---

### Post by matefon on 2023-09-05
That is unfortunate.
Can I reinstall the system without losing my personal data?

---

### Post by Rubi1200 on 2023-09-05
Do you have your personal data on a separate /home partition?

If yes, then you can reinstall but making sure to point the installer to just the /root partition.

If not, then backup everything important and then reinstall.

Actually, you should backup everything anyway just in case.

---

### Post by ajgreeny on 2023-09-05
> **matefon said:**
> That is unfortunate.
Can I reinstall the system without losing my personal data?
Sure you can!

Backup everything in your /home to an external disk or a separate partition, which you must always do anyway (you do that don't you?) then reinstall the OS and lastly restore your files.

Backing up personal files is essential practice for any computer user; installing or reinstalling the OS is a few minutes job but recovering personal files without backups is very different and once lost they may be lost forever.

---

