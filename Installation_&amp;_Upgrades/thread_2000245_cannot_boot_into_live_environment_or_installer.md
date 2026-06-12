---
title: "cannot boot into live environment or installer"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by icon-x on 2012-06-09
hello forum, 

i have an i7-asus P8H67-V machine which i plan to build a triple boot system containing win7, ubuntu studio 12.04 and mint 13. 
win7 is installed with an usb stick and have been working fine by now.
today, i burned the ubuntu studio and mint 13 iso's to the dvd's and i couldn't boot into the live systems or the installers.

in both dvd's i could be able to reach the installation menu and be able  to choose to boot into the live system or install directly. (or test  memory which works fine) 
but when i choose live or install, all i get is a black screen with a  blinking cursor. i measured the intervals between the blinks for 15  minutes and the result is cons...(what the??) anyway looking at the  blinking cursor for a few minutes gave me an idea (eventually) so i  burned the iso to usb stick with the universal usb installer 1.9 and  visited the (holy) efi bios.

in the efi bios (which seems like a normal bios with fancier design and mouse control)
i was able to choose between two options; to boot the usb drive or to (die!) boot the efi:usb drive (hmm) 
-booting the usb option took me to the same menu as the dvd and the same  blinking cursor eventually (intervals were the same so i was very  comfortable. it was like seeing an old friend) 
-booting the efi:usb took me to grub menu and i was able to reach the same blinking cursor of mine (oh yeah)

after a little debate with the blinking cursor, i decided to change the  monitor cable from hdmi to vga (the cursor gave me this idea) and guess  where i reached by selecting "install ubuntu" from the grub  menu........black screen with no blinking cursor!!.....

now my dear friends, i feel not far from the solution but i cannot  produce any ideas at this stage of installing. if you can help me at  this point, please don't hesitate to offer. 
thank you

---

### Post by darkod on 2012-06-09
The black screen can be related to video driver. Especially if you are running nvidia you can try the nomodeset parameter first:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

If you are using EFI boot and plan to dual boot win7 and ubuntu, you need to do some further investigation first because right now I think EFI dual boot is not straightforward. I don't have any links myself since I haven't played with EFI, but I've seen couple of threads on the forum.

---

### Post by icon-x on 2012-06-11
yes i have an nvidia card and nomodeset option can help me boot into live session. 
but i am confused about installing now... my win7 hard disk is formatted as MBR so i was feeling like i wasn't booting into efi mode and efi dual boot problems were not my concern. 
am i wrong?

---

### Post by darkod on 2012-06-11
You should be right. Win7 can work with EFI only on gpt. So, if you have msdos table, you are not using EFI boot.

You should be OK if you install. On first boot you will need to use nomodeset again as explained in that link.

---

