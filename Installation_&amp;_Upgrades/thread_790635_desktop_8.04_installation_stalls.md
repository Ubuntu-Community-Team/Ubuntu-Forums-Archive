---
title: "desktop 8.04 installation stalls"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by jlaurent on 2008-05-11
Hi 
I have a desktop with gigabyte GA-7N400Pro2 and Athlon XP 2600.
I have the desktop ubuntu 8.04 LTS i386 iso on the CD.
I can see the ubuntu splash and the orange bar going back and forth.
after sometime the orange bar becomes a progress bar and stay stuck at about 15%.
what is wrong?
how can I check where is it failing.

thx

---

### Post by louieb on 2008-05-11
A bad burn is a common cause of CD boot failure. Do you get to the 1st menu?
Did you run the check media for defects option? All it takes is a few twisted bits to turn the CD into a coaster.

---

### Post by jlaurent on 2008-05-11
I can see the first menu where I can choose the language and then do the "pre-install test" or do the normal install. While loading the install that the system stops, always exactly at the same time (on the progress bar)
thx

---

### Post by louieb on 2008-05-11
Have you selected the check media for defects option?
What did it do? 
If it passed the media check, you can presss ctrl+alt+f1 to see the messages (that is if i remember right). Its been awhile since I've used the Desktop CD. 

You can try the alternate install CD. Thats what I normally use.

---

### Post by jlaurent on 2008-05-12
so I did that with the alternate all the installation is happening fine in fact all the test pass and everything is happy. when I reboot the systems stops at b43_legacy phy0 Broadcom wlan found or something like this and this is where it get stuck. But I don't think I have any wlan on this desktop. I checked the BIOS and nothing refers to wlan B43 device.

any clue?
maybe I should look for some tip on this error...

---

### Post by louieb on 2008-05-12
Next ? How much ram?  If you have 256MB the alternate CD should work . With 512MB or better either CD should work. 

Have you tried some of the other Linux flavors such as Pupply, DSL, or Knoppix? (the last 2 like Ubuntu are Debian based). Just to see if the PC is Linux compattable.

Maybe you'll need to add a boot option. Some common ones are **noapic, irqpoll **and **nolapic**.   
Heres how to do it. [BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

Normally these aren't needed  but sometimes.... that why their there. Just have to try some, Probably the ones that alter pci or irq handling. Heres a couple of list. Good luck.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

---

