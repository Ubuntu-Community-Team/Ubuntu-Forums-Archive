---
title: "Please help me! I'm hopeless with this! &quot;Error Loading OS&quot;"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by dollarside on 2011-03-01
I am so frustrated from this problem and I hope that you can help me soon, because I need to use my laptop :(

I installed 10.04 (clean install) on a 250G drive (partitioned to 107G for the system files). It was working fine, until I wanted to install Window$ for the use of Adobe stuff. 

I popped the Windows XP disc in, it **loaded its files**, then I tried to choose a partition for installation. There was an error saying that I can't do that, and needed to delete a partition blah blah. I thought it was too much trouble, so I quit and just wanted to use my 10.04. 

Booted, and it says "Error booting operating system" I WAS SHOCKED.

I tried to install grub (but don't need that right? I DO NOT want to dual boot now), but the usual method ( the sudo grub; root (hd0.0)...) doesn't work ,because something like "stage1" is missing. 

I tried many methods by still the same error.


The reason I do not want a clean install is that I did many fixes on my 10.04 so that it would work with my EeePC 1001pxd, and I do not want to go through that again. 

I will be checking my email frequently on other computers if I have a chance. Here is my email if you can help me!! [email]dollarside@gmail.com[/email]


**ANY HELP IS VERY, VERY APPRECIATED. THANK YOU!:popcorn:**

---

### Post by Rubi1200 on 2011-03-01
Hi,
we need to get a better overview of your current setup.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

