---
title: "Dapper with LILO dual boot"
date: 2006-05-28
forum: Installation &amp; Upgrades
---

### Post by wizzkid on 2006-05-28
Hi Guys, I just had fresh installed dapper. I used XFS, it says that using XFS on GRUB would be bad idea, so I used LILO instaed. after the installation, I reboot the system, then it says LILO {version number} loading linux ................................................................................   it took lot of time before it load, and also the dual boot to my windows was gone (the menu was gone) I checked my partition and the windows is there.

1. HOw can I make the loading of LILO faster? it took me around roghly 3mins before it boots.

2. How can I make the menu of lilo? so i could choose between kubuntu and windows.


Thanks so much

---

### Post by wizzkid on 2006-05-28
any clue on this ? :)

---

### Post by y0ssarian on 2006-05-31
I don't know exactly how to make lilo faster but in order to get the menu screen that will allow you to choose what to boot do this(backup your file first!):

1. Type '[FONT="Courier New"]sudo gedit /etc/lilo.conf[/FONT]' in terminal
2. Scroll down unill you see '[FONT="Courier New"]Default=Linux[/FONT]'
3. Change that line to '[FONT="Courier New"]prompt[/FONT]'
4. Save and close the file
5. Type '[FONT="Courier New"]sudo lilo[/FONT]' in the terminal
6. Reboot. You should see a menu with Linux, LinuxOLD, and Windows boot options

---

