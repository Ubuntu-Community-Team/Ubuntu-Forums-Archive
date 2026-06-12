---
title: "regarding compatibilkty with dual core!"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by aditya.kichu@gmail.com on 2008-03-24
hi all,
my name is aditya.i had  installed ubuntu on my intel dual core 3.0ghz processor.i had a few difficulties in using it and so i had to delete it.kindly clarify my doubts.
1.i couldn't install codecs for mp3,avi etc.
2.most of the softwares like media players,sound recorders etc couldn't be installed on my comp.i want to know why?
3.is it because dual core is a 64 bit processor?
4.will all these problems get rectified if i install ubuntu 7.10?
please help!
thanking all those who'll help out in advance!
aditya

---

### Post by oldos2er on 2008-03-24
It would help if you would show us any and all error messages you receive when trying to install codecs or other packages.

 I seriously doubt it's because of your processor--unless you're trying to install 64-bit packages on a 32-bit install of Ubuntu. Please also tell us which version of Ubuntu you're trying to install.

---

### Post by aditya.kichu@gmail.com on 2008-04-01
the error message i get is this error: I386 .i tried this in ububtu 7.04.currently i don't have ubuntu on my comp!
thanks!

---

### Post by Ideal@EFnet on 2008-04-01
> **aditya.kichu@gmail.com said:**
> most of the softwares like media players,sound recorders etc couldn't be installed on my comp.i want to know why?

When you installed did you get a message saying some updates couldn't be run etc..?
I had the same thing happen when I installed, because the computer wasn't connected to my network & internet. So the updates didn't run, and then the install commented out the addresses to get the updates, meaning the installs and updates won't install, and it gives the error message you describe "wont install on your system: i386"..

You have to go in terminal, and then do: sudo gedit /etc/apt/sources.list
Then just remove all the #'s that are in front of the addresses, and save the file.
# means that line won't be used.

Then the update and add program thing will work.

I'm new at this too, so I'm not the best at explaining these things, but I tried my best :lolflag:

---

### Post by aditya.kichu@gmail.com on 2008-04-08
oh ok thanks
i'll try it out soon and tell you!

---

### Post by scragar on 2008-04-08
i386 is refering to 32 bit systems, you said you have a 64 bit processor, so I'm guessing that is your problem. Did you download/install the 32 or 64 bit version of ubuntu, and same goes for the programs you cannot install.

it is possible to install a 32 bit O/S on a 64 bit computer, but performance suffers slightly.

---

