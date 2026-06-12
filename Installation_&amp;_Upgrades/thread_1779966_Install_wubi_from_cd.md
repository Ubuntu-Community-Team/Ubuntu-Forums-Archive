---
title: "Install wubi from cd?"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by bikeman123 on 2011-06-11
I downloaded and burnt an install disk because the Wubi bit torrent was so painfully slow and now i find that despite having everything required on the disc the install still initiates a torrent download.
Why doesn't Wubi install from the cd?

---

### Post by Rubi1200 on 2011-06-11
Hi,
there are 2 possibilities to deal with this:

1. download the wubi.exe for the relevant version and place it together with the iso image in the same folder and then run the executable

2. if the above doesn't work, then first check the md5sum matches:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

if it is good, then force Wubi to start without this check:

To modify arguments, right-click Wubi.exe and select "Create Shortcut".  Then right-click the shortcut, select Properties, and modify the target  line, for example: "C:\Documents and  Settings\<user>\Desktop\wubi.exe" --skipmd5check

---

