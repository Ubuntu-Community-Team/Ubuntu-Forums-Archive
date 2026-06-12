---
title: "Summary about my 9.10 64 bits experience."
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by minimin on 2009-12-28
Hello to all.

This post is a summary about my experience installing and configuring/customizing the new 9.10 64 bits version. I was using 8.04 LTS 32 bits before and there are some issues and some advantages that I found (in my opinion). Maybe other users can complement this and help to improve features/solve problems for next versions and show appreciation for some features and fixes that they found out in this new release.

**A little bit about my context:**

I have an old notebook (HP DV2000) that I use for work and on this I installed Ubuntu 8.04 LTS 32 bits. This works like a charm and is very stable but due to 32 bits SO (and math restrictions... heheheheheheh) my 4GB RAM is not completely mapped. Another point is that my notebook videocard does not support advanced video effects and I like Compiz a lot. Based on that I decided to buy another notebook and give 9.10 64 bits version a try. I selected a simple notebook model and not very expensive (Asus K40IN) but with a configuration that matched my purposes. Here is a list of problems I faced and some workarounds I found:

**- Moomex and other themes does not work properly with firefox:**
In my 32 bits LTS notebook I use Moomex GTK theme and this works very well. All my softwares get the theme colors and customization. I tried to apply the same theme and configurations to my 64 bits version but firefox kept with odd colors for the location bar. A workaround for that was to install the old toolbar plugin. Other point is that the HTML components doesn't follow the colors applied by the theme (and it worked on 32 bits version). I even tried to remove firefox 3.5 and get back to a previous version but could not accomplish the process.

[COLOR=Red]PS: for this I decided to keep using the Human theme for GTK and customized emerald theme, AWN and menu bars to give a nice looking.[/COLOR]

**- Suspend/Hibernate does not work properly:**
If I allow my notebook to suspend or hibernate it does not recover from the hibernation/suspension. I found out that there are a bunch of threads about this already and no one could find out a solution. This problem affects a lot of different notebook models and not just mine. I use this feature in 8.04 LTS (HP DV2000) and it works properly.

**- Sound card not working:**
I had to flash my BIOS to make the external speakers work. That is not a problem since it is a good practice to keep your BIOS up to date. The workaround was to flash my bios to version 2.20 as mentioned before. I do not consider this a problem or an issue but just decided to put the procedure since others may have the same problem.

**- NVidia G102M does not work with repository drivers:**
My videocard (NVidia G102M) does not works with repository drivers. To wolve that problem I just had to download the latest release for the drivers from NVidia website and after that follow the install procedures. To install it you should stop GDM (sudo /etc/init.d/gdm stop), give the driver execution permissions (chmod +x NVIDIA_XXXX.sh) and then run it with super user privileges (sudo ./NVIDIA_XXX.sh). After that remember not to override your drivers with the ones provided by the repositories during update procedures. If you do that just make sure to install the drivers provided by the website again.

Well... those were the problems and issues I found until now and the workarounds I applied. Now let's go through a few things I enjoined in the 9.10 64 bits:

**- The new Human Theme is amazing.** I not even decided to change it or customize my GTK theme due to the improvements made to the colors and visual differences from 8.04 LTS. Congratulations Ubuntu team.

**- GDM Theme is awesome.**

**- My atheros wireless card worked out of the box and it doesn't happen in 8.04 version.**

**- The install process is much better and easier making new users go through it in minutes (that's my opinion).** The ubuntu install process was never complicated but it is getting easier for each new version. Congratulations on the improvement.

**- Brazilian Portuguese translation is better than previous versions.** Lots of wrong words were fixed in Gnome translation. Thanks guys.
[B]
- Cube deformation rox (for compiz cube engine).[/B]

I will keep posting my experiences when I find new problems or features that I think are much better than before. But my final considerations are that Ubuntu 9.10 64 bits is a very good and stable OS and I recommend it to people that needs to map their 4GB ram memory or want to enter the 64 bits generation. For work I'll stick with my 8.04 LTS version but maybe on next LTS I change to 64 bits even on my working notebook. 

To end this post I would like to change a little the subject:

[B]Two days ago I was remembering that to use Linux (I used Debian and Slackware before) at work was very difficult before due to crashes during update, lack of stability and lack of options for softwares (and incompatibility in some cases) in repositories. IMOH Ubuntu made Linux much more accessible and made my life much easier. I know that this is not too much but I would like to show my appreciation for your work, guys. Thank you.
[/B]

Cheers. :guitar:

---

### Post by minimin on 2009-12-28
There is still a pending problem but I didn't had time to take a look yet.

My Asus K40IN touchpad scroll is not working and I can't enable/disable touchpad. When I find out the solution I get back here and post the procedures.

Later I will compile the guides for the workarounds previously described.

Cheers :guitar:

---

