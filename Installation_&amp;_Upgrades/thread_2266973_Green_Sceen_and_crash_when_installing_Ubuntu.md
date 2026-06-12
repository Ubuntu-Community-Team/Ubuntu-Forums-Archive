---
title: "Green Sceen and crash when installing Ubuntu"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by rob120 on 2015-02-26
Hello,


Recently I thought I would switch from Windows to Ubuntu after a friend recommended it to me, so today I went ahead and bought a 4 gb blank DVD and burnt it on, that went well, so the instruction told me to boot via disc so I did that, i selected the language and selected the install ubuntu , it proceeds to the splash page where it has the dots below the logo after 3-4 minutes I get the a space-invaders/matrix looking screen and it freezes on that. I am slightly an amateur when it comes to software, but if anyone can help, it will be greatly appreciated!

[IMG]https://pbs.twimg.com/media/B-ygjYXXIAIACtw.jpg:large[/IMG]

Link to PC specs: [http://www.pcpro.co.uk/reviews/desktops/369727/acer-predator-g5900](http://www.pcpro.co.uk/reviews/desktops/369727/acer-predator-g5900)

---

### Post by rob120 on 2015-02-26
Also, I just tried installed Xubuntu and I had the same issue.

---

### Post by ajgreeny on 2015-02-26
It has an nvidia card so you probably need to use the nomodeset option to get to a usable but low resolution desktop for both the live system and the installed OS for its first boot from which you can then install the proprietary nvidia driver by using **Additional Drivers**

Boot the live DVD/USB again and at the first screen you see (or maybe  it's the screen where you choose to install or try, I can't remember)  hit F6 and there you can select from the available boot options.  Try  nomodeset first and you may get to a usable but low resolution desktop  which will allow you to install the OS.

If that works OK reboot and at the grub menu (hold shift at power-on if  you don't see a grub menu) hit "E" to edit, navigate to the line with **quiet splash** in it and replace those two words with **nomodeset**.  Hit **Ctrl+X**  to boot with that option, probably again low resolution, but it should  allow you to install a driver from Additional Drivers for your nvidia  card.  Reboot again and hopefully you will now have a system working as  you want.

---

