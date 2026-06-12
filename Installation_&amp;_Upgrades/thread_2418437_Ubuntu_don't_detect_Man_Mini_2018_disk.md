---
title: "Ubuntu don't detect Man Mini 2018 disk"
date: 2019-05-06
forum: Installation &amp; Upgrades
---

### Post by rlemoal on 2019-05-06
When I boot Ubuntu from a USB key, Ubuntu can only detect my extra external hard drive but can't detect the internal Mac Mini 2018 disk. So it is impossible so far to install Ubuntu as a standalone OS. Do you have suggestions ?

I have already remove the T2 chip security and the SIP security (not sure what it is). Impossible to find on Google a guy who did that ...

---

### Post by mörgæs on 2019-05-07
Hi, welcome to the fora.

If we forget installing for a moment: Are you able to do a live boot?

---

### Post by Rubi1200 on 2019-05-07
If you can boot from a live USB then please open a terminal with CTRL+ALT+T and run this command:

```
sudo fdisk -l
```

post the results here in code tags (Go Advanced and look for # symbol).

Thanks.

---

