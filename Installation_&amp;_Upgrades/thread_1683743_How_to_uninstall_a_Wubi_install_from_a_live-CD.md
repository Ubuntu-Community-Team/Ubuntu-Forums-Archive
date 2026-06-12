---
title: "How to uninstall a Wubi install from a live-CD ?"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by YannBuntu on 2011-02-08
Hi all,
I have developed a [simple tool to easily uninstall any Ubuntu (or other Linux distro)]("http://ubuntuforums.org/showthread.php?t=1615667") from an Ubuntu live-CD. It works very well for any Linux installed on a separate partition. :guitar:

Now I am wondering if it is possible to add it the possibility to uninstall a Wubi installation. Maybe some of you may know how to help me.

For the moment, I know how to detect a Wubi install (just need to detect a /ubuntu/disks/root.disk file).

Then, all tutos I found use Windows tools, but [this "How do I manually uninstall Wubi?" paragraph]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?") gives clues to do it from a live-CD :
- Remove C:\ubuntu and C:\wubildr* : ok
- remove Ubuntu from the Windows bootloader : do you know how to do this from a live-CD for Vista and Seven ?
- remove Ubuntu from the registry : do you know how to do this from a live-CD

---

### Post by pmlxuser on 2011-02-08
[http://www.techrepublic.com/blog/networking/modifying-the-windows-7-boot-loader-with-the-boot-configuration-data-editor-tool/1709](http://www.techrepublic.com/blog/networking/modifying-the-windows-7-boot-loader-with-the-boot-configuration-data-editor-tool/1709)

for editing windows vista or 7 bootloader hope it helps

---

### Post by YannBuntu on 2011-02-08
Thank you, but the blog mentions Bcdedit, which cannot be used from a Ubuntu live-CD. I am looking for commands that can be used in the Ubuntu terminal, not the Windows one.

Any other idea ?  ):P

---

