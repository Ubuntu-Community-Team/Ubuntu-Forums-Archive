---
title: "how to get back ubuntu after installing windows"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by nageshrk on 2010-03-28
hi all,

i have a problem , i am not able to get back my installed ubuntu after installin windows xp,

i tried typing fdisk -l from live ubuntu cd 
it gives me a error saying 
cannot opn /dev/sda

what do i need to do if need get the harddisk information.

thanks

---

### Post by zvacet on 2010-03-28
To avoid misunderstanding type in terminal (when you are running live CD)

```
sudo fdisk -l
```

What is output?

---

### Post by theozzlives on 2010-03-28
You running GRUB2 or Legacy GRUB?

---

### Post by presence1960 on 2010-03-28
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

