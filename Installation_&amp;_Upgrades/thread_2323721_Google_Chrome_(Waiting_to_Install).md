---
title: "Google Chrome (Waiting to Install)"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by anon24 on 2016-05-07
Google Chrome will not download. I couldn't even get it to install via the terminal with apt-get. Is there a fix for this?

---

### Post by oldos2er on 2016-05-07
Google recently dropped support for 32-bit Chrome; are you running 64-bit Ubuntu? Otherwise go to [https://www.google.com/chrome/browser/desktop/](https://www.google.com/chrome/browser/desktop/)

---

### Post by anon24 on 2016-05-07
I am running 64-bit. That's the link that I used initially and I still ran into this issue. I just rebooted and tried it again, same issue.

---

### Post by oldos2er on 2016-05-07
Try ```
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

---

### Post by anon24 on 2016-05-07
Ok, so it did something, but when I search my computer for Chrome... There is nothing there.

~$ wget [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
--2016-05-07 14:05:57--  [https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb](https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb)
Resolving dl.google.com (dl.google.com)... 2607:f8b0:4002:c03::88, xx.xxx.xxx.xxx, xx.xxx.xxx.xx, ...
Connecting to dl.google.com (dl.google.com)|2607:f8b0:4002:c03::88|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 48371848 (46M) [application/x-debian-package]
Saving to: &#8216;google-chrome-stable_current_amd64.deb&#8217;

google-chrome-stabl 100%[===================>]  46.13M  4.79MB/s    in 11s     

2016-05-07 14:06:08 (4.11 MB/s) - &#8216;google-chrome-stable_current_amd64.deb&#8217; saved [48371848/48371848]

---

### Post by oldos2er on 2016-05-07
You need to install the deb. ```
sudo dpkg -i google-chrome-stable_current_amd64.deb
``` And you might need to run ```
sudo apt-get install -f
``` too.

---

### Post by anon24 on 2016-05-07
Awesome, it worked ! Thank you. :)

---

