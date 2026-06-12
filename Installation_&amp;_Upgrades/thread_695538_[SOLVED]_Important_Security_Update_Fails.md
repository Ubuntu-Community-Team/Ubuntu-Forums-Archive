---
title: "[SOLVED] Important Security Update Fails"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by Maverickprowls on 2008-02-13
I am trying to install the linux-headers-2.6.22-14-generic update as shown in my Update Manager, but each time I run install process, it fails with the following message:

> E: /var/cache/apt/archives/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb: unable to make backup link of `./usr/src/linux-headers-2.6.22-14-generic/include/config/net/act/police.h' before installing new version

I have tracked down the file in question, and oddly enough it seems to belong to a user and group described by two long (different, eight digit owner, nine digit group) numbers.  As a relative linux novice I don't know whether this is an error of some kind or perfectly normal for this file, and I'm wondering whether it is safe to simply alter the file permissions and ownership to root to allow the system to complete the update.

I should mention that I had some major hard-drive problems after a recent power-cut) I'd have a UPS if I could afford one) and had to run fsck manually, which basically meant pressing "YES" for everything it suggested as I don't have the knowledge that would help me guide the process effectively.  As such, it has occurred to me that this is some vestige of the HDD problems I had come back to haunt me.

Any advice would be welcome, thanks very much.

---

### Post by Maverickprowls on 2008-02-13
UPDATE:  I have ascertained that the file was borked by the recent HDD problems, as it's last modified date is June 2102.

My question now is how to modify the file's ownership and group.  ```
sudo chown root:root police.h
``` doesn't work, nor does a root-enabled nautilus browser.

Is there a simple way to modify this file's ownership and group, and is there some limitation on the sudo command which is preventing me from accomplishing this?

I have also tried booting from a Live CD, then mounting my filesystem and trying to either **chown** or **rm** the file in question, both of which fail, either saying "Operation not permitted" or simply causing the window I am using to hang, depending on my methodology.

---

### Post by Maverickprowls on 2008-02-13
FIXED IT:

In the end I noticed that the /act directory was still owned by root, so I renamed it ```
sudo mv ./act ./act-bk
```

I'm still a little worried that this isn't good practice, but it seems to have worked, the update ran with no errors, and now all I have to worry about is removing the file.

---

