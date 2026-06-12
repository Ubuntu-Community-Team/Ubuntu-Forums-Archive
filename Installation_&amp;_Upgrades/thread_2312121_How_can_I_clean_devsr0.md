---
title: "How can I clean /dev/sr0 ???"
date: 2016-02-02
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2016-02-02
The  /dev/sr0  of my installation is 100% full
how can I clean it.
Tks

---

### Post by deadflowr on 2016-02-02
That's usually a dvd or cd.
Those will almost always read 100% used, regardless of size.
More likely still, it's probably set as read-only, anyway.
And set with write-protection, to keep it from ever being overwritten.

---

### Post by hoboy on 2016-02-02
Thanks for that info.

---

### Post by KenSharp on 2016-02-02
Why would you even want to try?

---

### Post by Nuno_Abreu on 2016-02-02
That should be a CD/DVD drive or even a mounted filesystem for a live-CD - but there are a lot of situations where that can happen. I will assume the situations I know.
When you have CDs or DVDs, it is impossible to wipe them, unless they're rewritable - if they are not and you want to get rid of the files inside, the best you can do is to literally destroy the optical media. But if you have a rewritable one (CD-RW or DVD-RW), paste this on the command-line:
```
[COLOR=#333333][FONT=Courier New]cdrecord -v blank=fast dev=/dev/sr0
```
Of course, this would clearly wipe your installation.
Actually, to delete some content from the rewritable optical drives (and if your computer allows you to boot it), you can do a clean burn but without finalizing, letting you delete or add files - that's done when you're burning the installation in the first place.

When it is about mounting ISO files or device images to the sr0 file (virtual drive), the best you can do is unmount the drive and delete the source disc. To add to the file, you should consider not finalizing and mounting it every single time as a filesystem - if you have any doubts, I can explain that thoroughly.

[/FONT][/COLOR]

---

