---
title: "Ubuntu upgrade Installation crashed, files locked/hidden in &quot;lost+found&quot;.Please help!"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by kingofpirates7 on 2013-10-28
I received the update message for the new Ubuntu OS upgrade, I proceeded with it. But the upgrade crashed in the middle and when I rebooted, it stated that file systems were missing and unable to boot into Ubuntu. Hence, I accessed the computer using the 12.10 version in my flash drive and reinstalled it in small partion (6GB), so that I don't accidentally erase the files on my harddrive, because Ubuntu was stating that a new installation will format and erase all data on the drive. But, now I'm locked out from the files and unable to see or access. It is now displayed as seperate disc which has two folders "deleted os" and "lost+found". Whenever, I click on the "lost+found" folder it gives me the message : 

> The Folder contents could not be displayed

"You do not havve permissions necessary to view the contents of "lost+found""

Please help I have 400 GB data, that I'm unable to access.

---

### Post by mörgæs on 2013-10-29
Does 

```
sudo chmod a+r lost+found

```
help?

---

