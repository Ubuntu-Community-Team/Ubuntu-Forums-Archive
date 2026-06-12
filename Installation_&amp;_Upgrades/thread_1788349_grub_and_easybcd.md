---
title: "grub and easybcd"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by wwe9112 on 2011-06-22
how do I change my boot up manager to be that easybcd program? when i click my w7 on the grub, and it comes to this other boot manager, when i click my linux - kubuntu - it just gives me a bunch or errors...i hope someone can help. sorry for the two problems in one. Thanks

---

### Post by wwe9112 on 2011-06-23
ANyone? Nowwhen I click on the linux one it just goes back to grub

---

### Post by Rubi1200 on 2011-06-23
Hi,
how did you install Kubuntu?

The easiest thing for us to help you troubleshoot this would be to post the results of the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

