---
title: "Installation Failure"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by Mordak on 2006-06-18
I downloaded Ubuntu 6.06 and booted my computer from it. When I pressed enter to start/install ubuntu, i got some errors (listed below), but the cd continued booting and then ubuntu finally came up. I double clicked the install icon on the desktop and went through the 6 installation steps. When i clicked install, ubuntu began installing but then after a minute or two the progress window suddenly disappeared. i tried installing again and the same thing happened. the install just suddenly disappears. help!

---------
Erorr

Uncompressing Linux... Ok, booting the kernel.
[4294803.121000] hdc: ide_intr: huh? expected NULL handler on exit
[4294824.323000] hdc: ide_intr: huh? expected NULL handler on exit
[4294824.373000] Buffer: I/O error on device hdc, logical block 357298

---

### Post by Mirrorball on 2006-06-18
Did you test your CD for errors?

---

### Post by Mordak on 2006-06-18
no... although i dont see how there could be an error if the installation setup process went perfectly. ill check and report back

---

### Post by Mirrorball on 2006-06-18
I asked because I was getting this error too: '[4294824.373000] Buffer: I/O error on device hdc, logical block 357298.' And the cause was that the CD had errors.

---

### Post by Mike Wilson on 2006-06-18
Sounds like you installed from a 'Desktop' CD. I was upgrading, not installing, and hit all sorts of problems using that CD. Then I checked the wiki, and learned that (for upgrades, at least) that CD is unusable. The wiki gives instructions for using the 'Alternate Install' CD instead, though not for installing. A quick search on 'dapper install' at the wiki didn't turn up anything that looked useful. 8-(

---

### Post by Mordak on 2006-06-18
i did the cd check, walked away from my computer, and when i came back it was at the ubuntu desktop. so it appears that the cd is fine. i tried installing again and the same thing happened. the installation progress window disappeared. help!

---

### Post by Mordak on 2006-06-18
so mirrorball, did you reburn or redownload the iso and then everything worked fine?

---

### Post by Mirrorball on 2006-06-19
I cleaned my CD-RW and burnt the iso again. Did you disk fail the test?

---

### Post by Mordak on 2006-06-19
I'm not sure. I walked away from my computer when I selected the cd test and when i came back it was at the ubuntu desktop. it appeared as though it was going through the same steps that it goes through to boot to desktop when i did the cd test, before i walked away from the computer.

I tried torrenting the iso file i had downloaded and it wasnt fully downloaded, only like 98% and so that finished to 100%, and i burned it to a cd again, but i still got the same errors, so I don't know what to do.

---

### Post by Mirrorball on 2006-06-19
Did you get the same errors that you posted on your first message? hdc is probably your CD drive (is it?), that is where the errors are coming from. I suggest you test your CD with md5sum. Here are the official md5sums: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS](http://mirror.cs.umn.edu/ubuntu-releases/6.06/MD5SUMS)

I actually had to burn the CD three or four times, it only worked after I realized that I had to clean the CD-RW first. So burn it again, then get the md5sum for the CD you just burned and see if it matches the official one.

---

### Post by Mordak on 2006-06-19
i redownloaded the iso using torrent, reburned the iso, and used my other cdrom drive. using the other drive eliminated the errors. however, the installation still was not a success. i went through the 6 steps again and pressed the install button, then it said 'installing system', then it said checking swap partition until 14%, then it went back to installing system, then it started up the partitioner and when that finished it went back to installing system and thats when it keeps disappearing. the install window just disappears, and i have no idea why. i need help again!

---

### Post by Mirrorball on 2006-06-19
At least we made those errors go away. But I have no idea why the installer disappears, sorry.

---

### Post by Mordak on 2006-06-19
well hopefully someone else can help... are there any other install methods? i would love to fix this issue though

---

### Post by Mirrorball on 2006-06-19
There is the text-based installer in the alternate CD.

---

### Post by Mordak on 2006-06-19
could you possibly point me in the direction of a guide or documentation on how to install using the text-based method from the alternate cd?

---

### Post by Mirrorball on 2006-06-19
It's just as simple as installing from the graphical installer, just not as pretty.

---

