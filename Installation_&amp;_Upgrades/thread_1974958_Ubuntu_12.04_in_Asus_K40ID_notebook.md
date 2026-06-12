---
title: "Ubuntu 12.04 in Asus K40ID notebook"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by muski on 2012-05-06
Hi,

I have an [Asus K40ID]("http://www.cahpacing.in/asus-k40id-specifications") laptop. My internal hard disk failed and I replaced it with another one I have (has 3 partitions, XP + ubuntu 10.04 + unformatted partition in it). Unfortunately, my CD drive also failed some time ago so have to make do with a USB stick.

I used my desktop to download ubuntu 12.04 iso (which worked perfectly on my desktop as I installed it via wubi)
For laptop I used Unetbootin windows version to create the bootable usb.
unfortunately, in laptop bios "select boot device" menu, usb stick was not being detected. So I made USB as primary Harddisk and main hard disk as secondary. (now bios detects usb in "select boot device" menu) and proceeded with installation. Took 25 minutes to reach a menu where it asked for network selection. I did that and clicked next. Waited for next 7 hours for the screen to move (went for a swim + movie etc in between) When I came back I assumed it to be stuck downloading something at very low speed so restarted the process.

This time didn't select the network. clicked next. nothing happened and went to sleep. 9 hours later as I woke up, it had went to the next screen and asked me to fill name/password/timezone etc. then I clicked next and installation started. I selected the "use entire HD" menu for installation. Now I have a "welcome to Ubuntu 12.04 LTS" screen stuck for about 11 hours and I am off to sleep. It is not hanged as I can use mouse to click next on the menu for different screens+am getting the shutdown option in top right. I hope by the time I wake up, things will move on (though not hopeful)

I am sure I must have made some stupid mistake somewhere so someone please advice me as to how I should proceed when I wake up in the morning? 
Should I ditch the whole thing and use USB version of Hiren's boot cd to reformat by HD and start afresh? 
Is it even possible to use USB to boot as bios didnt detect it as USB drive. 
or Should I buy a new cd drive as my last resort? (I dont want to as I have had no use of it for past 2 years)

any help is welcome.

Thanks and please ignore my rookie mistakes if any

Regards

---

### Post by jadtech on 2012-05-06
if you have win xp working on that lap top you can down load the wubi installer and install ubuntu that way then just migrate the wubi to its own partition ...

the usb should not by any means take that long to boot and install, im no expert but just looking at the specs on that lap top I think you might need the alternate ISO and it has a nivida graphics you might want to choose  add nomodeset before it boots also to speed things up as soon as   the machine can get booted  making a swap partition frist thing  will help...

I pernally would choose to not do updates during the install just let it install with basic drivers and get booted and set then install updates video drivers last, i have done 5 installs of Ubuntu twice 11.10 upgrade to 12.04 once beta  once release version 3 times  clean installs and I found install without updates work on the frist try with the least amount of issues or tinkering ...

---

