---
title: "Not recognizing second hard drive!"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by coryy21 on 2011-03-03
I have 2 Internal hard drives and have Windows 7 on the first and put Ubuntu on second. It worked fine, I was using the OS with no problems etc. and while it was updating the power flickers. I turn the computer back on and it is not recognizing the drive from Windows. *However*, when I unplug the Windows hard drive and only have the second plugged in it boots with a loooong screen of odd information. It seems like it is corrupt where it was in the middle of updating or something? Anyone have any ideas? I would be fine with reformatting and reinstalling but I don't know how to format the disk when it isn't being recognized from Windows. Any suggestions would be greatly appreciated.

---

### Post by sikander3786 on 2011-03-03
Can you please boot an Ubuntu Live CD/USB and post the output of this command while both your HDDs are connected.

Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

---

