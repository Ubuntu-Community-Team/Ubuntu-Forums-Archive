---
title: "dual-booting not working."
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by RossL on 2010-11-21
Hello all,

I recently did a side by side install of lubuntu on my windows 7 laptop. My HDD is actually 2 x 250GB HDDs. I have Win7 on the first, and chose to put Lubuntu on a part of the second. However, when I boot, I can only see the options for that second drive. when I went into the boot order It only shows the Harddrive as an option, not which one. Is there any way I can boot from my first drive again? I need to be able to get at my Windows 7, it is my main OS as I need Excel 07 for a college course. (due to auto-grading none others will work, not even office for mac (which is missing pivot-tables anyways).

So to summarize, I seem to have lost the ability to boot from the first hard drive, and cant find the separate hard disks in the boot order. Preferrablly I would like both OSes (Win7 and Lubuntu) to appear on the same boot choice list, but at least I would like to be able to access Windows7 and only use Lubuntu when I need it. (mainly for my Compouter Science coursework)

Thanks

---

### Post by RossL on 2010-11-21
I solved it, but I will say what I did incase someone else is confused like I was. I first tried "sudo os-prober", that resulting in nothing because i guess lubuntu doesn't ahve it by default. so i did "sudo apt-get install os-prober" and then "sudo os-prober" after it install. to my good fortune it foune my Win7 and surprisingly my old WinVista that I had updated over. I finally ran "sudo update-grub" , then when i rebooted windows7 and vista had been added.

---

### Post by ronparent on 2010-11-21
What does your setup look like if you boot to the live cd and run gparted (menu header Administration> gparted)?

---

