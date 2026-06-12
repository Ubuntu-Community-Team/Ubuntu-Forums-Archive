---
title: "Blank screen on first boot"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by NextEvolution on 2011-03-22
okay so, i have a toshiba satelite pro laptop (can't think of the exact model at the moment) with 4gb ram + 320gb hard drive. i have been dual booting ubuntu for roughly a year, and throughout all that time windows has become less and less used, therefore last night i took the plunge, and went about installing ubuntu(10.10) as my main operating system and removing windows, i did this via a usb, using Unetbootin.
 
i used one of the .ISO's from the official ubuntu site, and went through the installation processall went well, no errors within the installation process, hard drives were partitioned fine etc, however when i've come to turn my computer on for the first time this morning i get a black screen with a blinking underscore straight after the toshiba logo flashes up and i get the choice to go to bios options.
 
If i do go to bios options my hard drive is listed fine, and if i try to boot from my usb again, it doesnt work, and attempts to verify dhcp and eventually tells me it couldnt find a boot file, my laptop however is plugged in via an ethernet cable. it doesnt work with or without the ethernet cable. i have tried leaving it for about half an hour and nothing has changed, i also can't boot to GRUB. :/
 
Cheers in advance :)
 
EDIT: i genuinely apologize for the god awful grammar, and lack of paragraphs, got like an hour of sleep trying to sort my laptop i wasn't all here

---

### Post by Dutch70 on 2011-03-22
Hello & welcome to UF

 Try choosing nomodeset when you boot the live cd. If it doesn't work, at least you'll have that ruled out, but you'll probably have to boot the live usb in order to check out your problem. 

[[COLOR="Blue"]How to choose nomodeset[/COLOR]]("http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html")

---

### Post by Quackers on 2011-03-22
If Dutch70's suggestion does not work, please check your bios boot settings and then boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

