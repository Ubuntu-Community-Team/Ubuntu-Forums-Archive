---
title: "Keyring issue"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by BigDope on 2010-10-03
after trying to disable the keyring thingy by following the guide [http://www.techtipsgeek.com/disable-gnome-keyring-password-request-ubuntu-10-04/9635/ ]("http://www.techtipsgeek.com/disable-gnome-keyring-password-request-ubuntu-10-04/9635/")

i found that i have problem in ubuntu, so i re- opened the gedit /etc/pam.d/gdm and removed the "*@include common-keyring*" at the end of the file...

but even after that, i am having problems with installing softwares from the software center..
i get "failed to download- check internet connection" error....

i am not sure if this problem is because of one more action that i did = use open dns {i used opendns for two days, before using it the software center was working fine, i didn't check if the software center worked when i used open dns though... but i reverted back today }

---

