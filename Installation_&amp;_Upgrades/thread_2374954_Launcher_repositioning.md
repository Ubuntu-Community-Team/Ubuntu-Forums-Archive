---
title: "Launcher repositioning"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by kelliewilliams on 2017-10-20
Hi, I just came back to Ubuntu on 17.04 have installed the 17.10, but am not able to reposition the launcher, I am not very savvy with all the technical jargon so need help in laymans  mode. Thanks in advance. :)
[IMG]https://ubuntuforums.org/asset.php?fid=272106&uid=2080409&d=1508524928[/IMG][ATTACH=CONFIG]277183[/ATTACH]

---

### Post by deadflowr on 2017-10-20
For unity run the command
```
gsettings set com.canonical.Unity.Launcher launcher-position Bottom
```
or install unity-tweak-tool, it has an option to move it in the Launcher tab.

For gnome-shell go to System Settings > Dock, you can set the launcher position here.
(or could last I checked)

---

### Post by kelliewilliams on 2017-10-22
Thanks, Did that and all is working fine, I love how clever people are in here. :)

---

