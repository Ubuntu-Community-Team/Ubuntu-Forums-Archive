---
title: "cant get updates in xubuntu 13.10"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by leeper692 on 2013-10-28
Hi  *am not able to update to the latest kernal* or initramfs-tools. how can i send you a copy of what I get in terminal when I type in sudo apt-get upgrade so you can see the full page of error codes?

---

### Post by J&#7885;hn on 2013-10-29
```
sudo apt-get upgrade | tee -a ~/errcodes
```

Should do it. The output will be in ~/errcodes.

---

### Post by fantab on 2013-10-29
Just copy all the error messages from the Terminal and paste here with "Code Tags".

---

