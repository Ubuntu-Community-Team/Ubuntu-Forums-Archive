---
title: "grub boot problem"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by damjan612 on 2010-03-01
hi 
can someone help me please
i have xp, vista and 7, then i was install ubuntu 9.04 and grub works great.. when i was power on my pc i  have options between ubuntu and vista loader ( xp, vista, 7 )
after that i was install mint 6 on different partition ( only swap is same with ubuntu ) and now on the  boot loader i have two options witch is mint and vista loader ( xp, vista, 7 ) but my ubuntu disappear from boot menu..
how i can fix this ?

---

### Post by presence1960 on 2010-03-01
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

