---
title: "Live CD not working"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by Neefs on 2006-03-01
I recently decided to get Ubuntu for my computer, however I have had some trouble getting the live CD to work.  I downloaded version ubuntu-5.10-live-1386 and then used ISO recorder to get it onto a CD.  
     Once I put the CD into my computer a popup menu came up saying that I had to boot my computer from the CD to get Ubuntu to work.  When I restarted my computer nothing happened, so I turned it off and tried that.  It still loaded up as Windows though.  
     Did I do something wrong? or could it be my computer thats getting in the way?

Thanks in advance for your help

---

### Post by Stew2 on 2006-03-01
Good idea trying the live cd first! Then you can see how your computer works with Ubuntu and how you like  it before committing to an install. If your computer keeps booting to Windows on restart it probably means that the bios is set to boot off the hard disk first. Usually (but not always :) ) you can press the "delete" key when its booting to access the bios, then go to the boot menu and select cd rom as first boot device. Save the changes and restart with the ubuntu live cd in before you reboot and it should work. Some computers have diffrent key combinations to access the bios at startup like F1 or something. Hope this helps. If I have misinterpeted your question, please disregard this answer. Good luck! :)

---

### Post by Neefs on 2006-03-01
Thank you very much for your quick reply.  That sounds like it is probably my problem, and I will be trying it out as soon as possible

thanks again:D

---

### Post by Stew2 on 2006-03-01
No problem. Hopefully that gets it going for you. I had to do that on my desktop to get it to work. Usually the bios is set to read the hard disk first to speed up your boot times a little. I never noticed much of a diffrence myself :) . Welcome to Ubuntu :D 
Stew

---

### Post by Neefs on 2006-03-01
Well I'm back, unfortunatly from Windows.  I did what you suggested and pressed f12 at startup (the button that it told me to use) and ubuntu began to run, but when it got past most of the installing and was checking my graphics card, an error message came up and the whole system went down.  It took me to something the looked like dos, and was asking for me to prompt it, with what to do, but anything I tried just made pages of repeating text fly by.  :confused: 
I have an ATI Radeon 256 mb graphics card, and I have heard that they don't work with Linux, however I didn't think there would be a problem.  
Does anyone know what might be the problem?
sorry for being such a Linux noob, but I can't really help it

Thanks in advance again:p

EDIT:  I went back and retried the live CD and this time wrote down what happened when it stopped working for me
.        a popup window came up and had written "failed to start the x server (the graphics interface) likely not set up properly, would you like to review output signal and diagnose. YES/NO
but immeadiatly a line of diagonal (sp?) text came up that said ubuntu@ubuntu:~$ which let me type after it.  I typed reset and the text moved into proper colombs, but I still couldn't get past it. If anyone knows something I can do that would be great
Thanks

---

### Post by bluedog666 on 2006-03-02
As far as I know, the new Radeon ATI R5x0/R600 chips (x1300/x1600/x1800 cards) do not have linux support. What is your card model exactly ?

Alex

---

### Post by Neefs on 2006-03-02
It's a Radeon 9250 256 mb card

---

