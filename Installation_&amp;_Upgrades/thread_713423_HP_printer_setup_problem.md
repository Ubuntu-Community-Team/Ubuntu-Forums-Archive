---
title: "HP printer setup problem"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by kwandtke on 2008-03-02
So I finally install a new Gutsy setup on a brand new drive ... all is going along well until my wife on her Windows laptop wants to print to the printer that had always been shared on what until earlier that day a Windows machine sharing an HP LaserJet 2100.  So .. a few Google's later I' m pleased with myself .. I have CUPS up and I go to the Windows laptop, browse out .. define the printer ... ahh .. life is good.

Only I send a document and it prints a line of junk and then like 10 more blank pages.  I try to print from the Ubuntu box directly and the same things happens .. then I realize whats up .. the Ubuntu box found the printer on it's own and set it up with a PS driver .. I need it installed with a PCL driver ... (I think) .. thts the only thing I can think of .. I know it's sending PS since I can see that setup string when it prints the one line.

Can any body steer me on how to install a different driver?

---

### Post by ibgeorgeb on 2008-03-03
I'm having the same problem also. Help, anybody. Thank you.

---

### Post by ibgeorgeb on 2008-03-03
I got it working and printing. :lolflag:

I went to System > Administration > Printing > 

I selected the Laserjet-2100M choice; Manufacturer is HP, Model Laserjet 2100M, and the driver** hpijs - HPLIP 0.9.7**.

Using the "Connections Tab" I selected the usb://HP/Lasrjet 2100 Series. Since I'm using a usb hub.

This is only my third day of playing with Ubuntu and somehow, when I hit the "Print the Test Page," viola, out came a Ubuntu test print page. I then went to Ooo Word, used different variations of font/fonts, printed the puppy and it came out perfect.

I'm happy. Now, to get the fan and the hibernate mode to work on my trusty old Toshiba-Ubuntu M205 tablet. Goodbye M$ Vista.

I hope this helps. George

---

