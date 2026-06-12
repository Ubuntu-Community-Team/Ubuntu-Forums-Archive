---
title: "Had to reinstall, question about grub"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by daedalusman on 2006-06-22
Well I was having some trouble with my computer the other day and had to reinstall from stratch. When I did this I though my main hard drive (hda) was dead so I had it disconected, this is the harddrive with windows installed. So now that I have my computer back up and running I have now have grub on my sda1 partition and have found out that my hda harddrive isn't dead. My quest is how to I know what grub thinks my hda drive is now? I mean it use to have hda ans hd0,0 but it now has sda1 as hd0,0. How can I make grub boot windows without having grub installed on my hda drive anymore? I have attached my grub menu list so you can see, I also have added the section for windows from my previous grub menu list that I had backed up a while ago. Thanks for any help.

---

### Post by Herman on 2006-06-22
Heelo, daedalusman, why don't you just ask GRUB? GRUB is actually more than just a bootloader, it's  almost a small operating system in it's own right, some say it *is* an operating system.
You can use GRUB's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") to ask GRUB what it thinks about your computer.
Regards, Herman :D
[ ]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

---

