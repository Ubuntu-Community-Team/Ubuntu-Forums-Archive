---
title: "Software Upgrade failure"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by UbunWannabe on 2010-09-03
When check for updates, this is successful and 15 are listed.  I select the option to install the updates and at the end I get an error message:
E:/var/cache/apt/archives/lnux-image-2.6.24-22.lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package 'libxcb-shape0' is missing final new line.

I also get a similar message when I try and install the skype application.

I am using a Dell netbook, ubuntu 8.04 (I think!)

If anyone can suggest how this can be fixed or a workaround or if this is a failure of Ubuntu and I have to live with it, I'd be grateful.  I have some IT knowledge, but Ubuntu is a completely different language to me and so any help or instructions may have to be rather simplified.

Hoping someone can help - soon. :)

Sharon

---

### Post by ajgreeny on 2010-09-03
Try clearing out the apt cache with ```
sudo apt-get clean
``` and try again.  Maybe one or more of the packages in the cache is corrupt after a bad download.

---

