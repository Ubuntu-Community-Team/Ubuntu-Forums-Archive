---
title: "Installing 16.04 video issues"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by deamon_knight on 2016-06-02
I'm having some problems with a new install of Lubuntu 16.04. I have the following hardware,
AMD Athlon 7850
[Gigabyte GA-MA78GM-US2H]("http://www.gigabyte.com/products/product-page.aspx?pid=2995#ov")
4GB RAM
a 500GB HDD, a USB 3.0 Card, and a Hauppauge 1800 PCI tv capture card.

The system will post, and will eventually load to the desktop, however, there is about a 30 second period when I'm seeing an "no video output" alert from my monitor. If I hit the keyboard it loads to the desktop more quickly. Once instead of the "no video" I saw the Grub menu. I'm not sure what key combo I hit, so I'm not sure if this was a fluke or a result of something I typed. I suspect there is a video issue in GRUB perhaps, but I'm not sure how to solve it.

Any Suggestions?

---

### Post by yoshii on 2016-06-02
I believe pressing and holding(?) SHIFT during boot gets to the grub menu.  
As for the graphics in (L)ubuntu v16.04, there is a known hardware incompatibility with AMD/ATI graphics and the new Ubuntu software/firmware.  
It is scheduled to be fixed later this year and both AMD and the Ubuntu people are working on it.  

Check the (L)ubuntu v16.04 Release notes.  And search the web for other articles about it.  You'll see what I mean.  
There are also some other threads here written about the incompatibility.  

You may need to enable the "nomodeset" kernel feature so that your screen doesn't go blank with no video input.  
It has to be set for the boot session, and in the /etc/grub file (and then sudo update-grub and reboot after that).  

Sorry I don't have the procedures memorized but I did post some other info about it since I also own an AMD graphics card.

---

### Post by deamon_knight on 2016-06-03
Thanks for the reply, I think I was misdiagnosing the problem. I can get to grub, with video, but after Grub it begins to boot and turns off video. From that point it is stuck (i've let it sit for ten mins) unless there is some keyboard input , at which point it loads. If I hit a key as soon as the display goes dim, it loads right up. Not sure if this related to the modesetting video issue or not. I'll keep looking I guess.

---

### Post by deamon_knight on 2016-06-07
I solved the problem. Properly described, my system will load grub, but fails to load further after selecting the Lubuntu boot image. My monitor would act as though there was no video at all, and the system would not proceed any further without keyboard input. After keyboard input, it would load the desktop properly.  Here is what worked for me. I had to modify my grub2 boot options, and changed "splash" to "nosplash". I followed the advice [here]("http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/") for modifying my boot options. 

Now, I get some messages instead of the splash screen, but this is expected. I'm not sure what underlying problem with the splash this solved, but it boots without any user input as I needed.

---

