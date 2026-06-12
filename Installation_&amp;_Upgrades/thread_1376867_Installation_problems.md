---
title: "Installation problems?"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by killerfoot on 2010-01-09
I can't install Ubuntu. Last night I got through the rebooting process and it got stuck at 98%. I waited for about 3 hours and then I turned it off. Now when I try to reinstall Ubuntu when It tells me to reboot I get stuck at the Ubuntu Logo. I don't even get to the second part of the install.

The third time I tried it, I deleted the "Ubuntu" folder in C:/. Now I have 2 Ubuntu options and neither of them work.
Specs:
Windows 7
2.10ghz dual core processor
3g of RAM
Radeon HD 3200

(This is a Laptop)

---

### Post by darkod on 2010-01-09
Since you mentioned ubuntu folder in C: it seems you are trying to install wubi and not ubuntu. Is there any reason you don't want to try to install proper ubuntu, with its own partition and filesystem?
Wubi can be problematic, also with Win7 sometimes.
I would always recommend a proper ubuntu install and not a virtual wubi.

---

### Post by raymondh on 2010-01-09
> **killerfoot said:**
> I can't install Ubuntu. Last night I got through the rebooting process and it got stuck at 98%. I waited for about 3 hours and then I turned it off. Now when I try to reinstall Ubuntu when It tells me to reboot I get stuck at the Ubuntu Logo. I don't even get to the second part of the install.

The third time I tried it, I deleted the "Ubuntu" folder in C:/. Now I have 2 Ubuntu options and neither of them work.
Specs:
Windows 7
2.10ghz dual core processor
3g of RAM
Radeon HD 3200

(This is a Laptop)


This is from the [wubiguide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?") referring on how to remove the Ubuntu entry/ies .... after removing them from C: drive (thru the add/remove function)

Does/did the liveCD work ok vis-a-vis your system?  I know it's not a thorough 'compatibility' check but it does give one clues on how your system will react to the Ubuntu version.

Post back if you need assistance in trying to install ubuntu in its' own partition.  

Regards,

Raymond

---

### Post by killerfoot on 2010-01-09
I would of done a proper install, but really I don't know how. I downloaded the ISO file and burned it into a disc but nothing happened. It just appears as a WINRAR file on the CD.

---

### Post by darkod on 2010-01-09
> **killerfoot said:**
> I would of done a proper install, but really I don't know how. I downloaded the ISO file and burned it into a disc but nothing happened. It just appears as a WINRAR file on the CD.

Don't burn the ISO file directly to the cd. In the burning software you need to use an option called something like Burn Image to disc. If your software doesn't support it, ImgBurn is a very good free burning software for windows.
After burning when you look in the cd it needs to have loads of files and folders, not just one single file.
Then put that cd in the computer and ignore any message to install. Restart the computer and make sure in BIOS boot options CD is before HDD. With the cd inside your computer will boot from it.
Then you will have option just to Try Ubuntu without installing first, it will run from the cd.
Later when you decide, you can use the Install Ubuntu option and do a full install.
If you need more help just ask.
Screenshots of the install process here:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by killerfoot on 2010-01-09
Thanks guys! I got Ubuntu up and running, and it's awesome(except I'm on Windows 7 right now because I need to set my internet up)

I have another problem:

When I try to set the effects to "Extra" It won't let me. It says something like "Unable to detect hardware". What do I do? My card can run Half-life 2 on high!

---

### Post by darkod on 2010-01-09
> **killerfoot said:**
> Thanks guys! I got Ubuntu up and running, and it's awesome(except I'm on Windows 7 right now because I need to set my internet up)

I have another problem:

When I try to set the effects to "Extra" It won't let me. It says something like "Unable to detect hardware". What do I do? My card can run Half-life 2 on high!

Glad you got it running. That sounds like driver issue but I'm not too familiar with that. Maybe it just needs to update it once the internet is working. Usually it will detect new driver itself.
You'll get it going the way you like it now, bit by bit. :)

---

