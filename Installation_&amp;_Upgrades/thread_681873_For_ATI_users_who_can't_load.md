---
title: "For ATI users who can't load"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by nethan_lor on 2008-01-29
Hi there ! Here's how I finally succeded in loading Ubuntu.
My initial problem was that I was not able to load pass the Loading boot script thing and then my screen was always going out of range and I could'nt do anything.

So this is how I finally got a working welcome screen.
First of all I did a dual boot installation with Windows XP.
Before installing, go get the Envy software [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and save it 
somewhere you will be able to access it via command line in Ubuntu. You can acces your windows partition in /media/hda0 or 1 i'm not at home rigth now... and then navigate in there until you reach the rigth directory. Then print the faq [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

I installed Unbuntu 7.10 with the alternate CD.
First you install the usual way. When it's done, you reboot and you will get stuck at the "loading boot script thing". Hit ctrl-alt-F1 and log with the username you created. Then go get the envy file where you saved it and do what's on the fact. When that is done, you should see the welcome screen in a crappy resolution. You can now log in.

It's time to install ATI driver. Go to ati web site and download the driver then follow up the instruction you printed before.
Go [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) and follow the Method 2: Install the Catalyst 8.1 Driver Manually

Hope this will help some of you.
Sorry for my bad english I did my best.

It's sure not a universal solution but it worked with me. I have a ATI X1300 graphic card by the way.

Thanks

---

