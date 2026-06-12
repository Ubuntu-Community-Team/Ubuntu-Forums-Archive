---
title: "'error: unknown filesystem. grub rescue&gt;'"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by giraffe01 on 2011-01-19
Hey all, 

I'm an complete new beginner with the Linux platform. I have no  experiance with command line. I have only been using Ubuntu for about  one week. 


Today when booting ubuntu, i'm getting a error. 

'error: unknown filesystem. 
grub rescue>' 

I have no idea what to do, and i don't have a live CD. I installed the OS using a USB. 

What do i do? 

Thanks.

---

### Post by presence1960 on 2011-01-19
Ok so you have a Live USB which for all intents and purposes is the equivalent of a Live CD. We need more info about your set up and boot process. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by presence1960 on 2011-01-19
Ok so you have a Live USB which for all intents and purposes is the equivalent of a Live CD. We need more info about your set up and boot process. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

