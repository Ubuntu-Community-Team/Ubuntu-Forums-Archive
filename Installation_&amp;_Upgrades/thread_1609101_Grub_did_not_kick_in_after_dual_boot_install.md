---
title: "Grub did not kick in after dual boot install"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2010-10-29
I installed windoz (sorry, but I had to) and then I installed Ubuntu 10.04. When I restarted, the was no menu, just went directly to windoz.
When I boot from the ubuntu cd I get the menu and can choose whichever OS I want.

I have tried my hand at fixing grub before and so I hate to ask this but do I need to repair grub?

If this is the case and it does not make it more complicated, I wonder if I should create a new partition and keep grub peperate from the system?

Please offer you advice.

---

### Post by Quackers on 2010-10-30
From your Ubuntu installation try running 
```
sudo update-grub
```
in a terminal and watch to see wether your Windows loader is picked up. If it isn't it is possible you will need to re-install grub.
To give a fuller picture it would help if you go to the site below and download the boot script to your desktop, then run the script with the command given on the site. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste it between CODE tags (for tags click on # in the New Reply window).

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sofasurfer on 2010-10-30
I haven't tried anything new yet. But here is some more info.
I reinstalled only ubuntu 10.04. Worked fine. 
Then I restored a backup of my /etc and /home folders. Worked fine. 
Then I reloaded my sources since I upgraded my sources.list with the backup copy. Worked fine.
Then I reinstalled my package list that was created from a previous (working) install of 10.04. System will not boot.
I installed live cd and chose "boot from 1st hard drive" on menu. Got a "GRUB Restore" prompt which I don't know what to do with.
Rebooted live cd and chose "try without installing". That is how I posted this letter.

What should I try next? Is the "GRUB Restore" prompt the best clue?

---

### Post by Rubi1200 on 2010-10-30
From the LiveCD post the results of the boot-script linked at the bottom of my post please.

Wrap the text with the # tag when posting the text back here.

Thanks.

---

