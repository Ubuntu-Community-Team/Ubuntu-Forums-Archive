---
title: "Help Fix Vista/Ubuntu Dual Drive Boot"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by grimdeath on 2008-06-28
I have been pulling my hair out all night, I originally had Vista/Mac OS with easybcd running to control the dual boot. but when I installed uUbuntu the other night I removed Mac OSX from my second drive and replaced it with Ubuntu. I had issues getting it to work but I figured out that switching my boot order in my bios let me see grub, then I could either boot into ubuntu or click Vista and it would bring up the easyBCD option with vista/neogrub linux (i could never get easybcd working to control things).

I though I would try to clean things up and either get just easybcd or grub in control and remove this extra menu page. Unfortunatly I screwed up somehow. I followed a guide saying that having anything besides the plain vista mbr would screw things up so I restored that in easybcd and booted from my Ubuntu using the Live mode. I then followed the guide that had me install grub over my mbr but then after restart I could not boot into either system, grub would come up only and both ubuntu/vista would throw and error if I tried to load in.

I have since restored the vista MBR on my vista drive via "bootrec.exe /fixmbr" from my vista recovery command prompt but neogrub linux is not working and booting directly to the ubuntu drive gives me a "operating system not found" error. I know this just means grub is not working. I would like to know what I should do to:

-get vista back to default (easily done with restore mbr in easybcd)
-boot into ubuntu live cd and reinstall grub (properly!)
-have grub in control and have both ubuntu/vista working
-lastly, set vista to boot by default instead of ubuntu (to help my wife)

I am too frustrated to check back on this tonight but please leave feedback and I will do it first thing after I settle down tommorow. Thanks!

Here's my hard drive setup:
first drive, sata, vista installed (master)
second drive, ide, ubuntu installed (slave)

I have switched things around so much I do not know which drive is set for hd(?,?) right now. Let me know how to check that for you guys if you need it!

---

### Post by logos34 on 2008-06-28
If you're through with the EasyBCD and Neogrub methods, and want to revert to the native Vista boot manager for windows. while at the same time using grub to dual boot, it seems to me you have one option: 1. leave vista bootloader intact and write grub to the mbr of the ide drive and make that the boot drive. (The advantage of this method is that should linux/grub fail at some point, you could still boot windows simply by toggling the Bios hard disk boot order.).  However, chainloading vista with grub doesn't always work, which is why they recommend EasyBCD.  Another potential pitfall: you have a mixed sata and ide drive setup, which can confuse grub

Restore vista bootloader.

Make sure the IDE/linux drive is first in the Bios hard disk order.  

Use the ubuntu live cd or the Super Grub disk to [reinstall grub to the mbr]("http://ubuntuforums.org/showthread.php?t=224351") of the IDE drive.  

You should get the grub menu screen.  Select ubuntu.  If it gives an error, go back and press 'e' to edit, 'e' again on the root line and change it from (hd1,?) to (hd**0**,?).   'Enter' to save and 'b' to boot.  If that gets you into ubuntu, make the change permanent:

**gksudo gedit /boot/grub/menu.lst**

change 'groot' and 'root' lines to match.

Your windows list at the bottom should look like this (with 'mapping'):
> 
title        Windows Vista
root        (hd1,0)  (*or '**rootnoverify**')
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader    +1(*this assumes windows is on first partition)

give that a shot
[URL="http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc"]
Booting windows by default
[/URL]

---

### Post by grimdeath on 2008-06-28
thanks for the help, I am aware of the sata/ide issues but to be honest I have been running them for a long while with no real problems on two different motherboards. I think a majority of my problems last night were because I believe I misunderstood that guide I was following and installed grub over the windows drive mbr. I tried every combination I could think of with easybcd to boot into Ubuntu without luck otherwise I would love to use it. I will get this setup today and posts back if I have any questions or to tell you guys it worked out.

Thanks!

---

### Post by grimdeath on 2008-06-28
I tried following the directions exactly and I was initially met with the first reboot after installing grub as "missing operating system" so I switched my drive order back to sata first and grub came up...so it looks like grub still installed on my windows drive :/ I followed the instructions for installing grub and here's what came up:

sudo grub
find /boot/grub/stage1 [COLOR="Red"]- this gave me (hd1,0)[/COLOR]
(hd1,0) [COLOR="Red"]is that right?[/COLOR]
setup (hd0)
quit

What did I do wrong?

another weird thing was after neither drive worked I restored the vista mbr using the vista install disk. but when I restarted and booted into the sata/windows drive I was met with the easybcd bootloader with vista/neogrub still showing...I SWEAR I used the "reinstall vista mbr" before I did anything else above.

---

### Post by logos34 on 2008-06-28
> **grimdeath said:**
> 
sudo grub
find /boot/grub/stage1 [COLOR=Red]- this gave me (hd1,0)[/COLOR]
(hd1,0) [COLOR=Red]is that right?[/COLOR]
setup (hd0)
quit

almost.  like this:

>  sudo grub
find /boot/grub/stage1 
**root** (hd1,0)
setup (hd**1**) [COLOR=Blue]*because you want it on the same drive (mbr) as ubuntu[/COLOR]
quitreboot and go into the bios and switch ide drive to first position

then if you get the menu but an error on ubuntu selection, do the 'e' edit routine I suggested above in #2

---

### Post by grimdeath on 2008-06-28
ahh thank you so much for helping me, I have now got grub loading first and ubuntu/vista options both work in grub.

however I am still seeing the vista/neogrub options coming up when I click the vista option in grub. do I need to manually delete the neogrub option to skip that whole screen? right now selecting vista two times in a row seems silly! this was where I was at last night when I tried fixing it and screwed things up :P

I can also just set the timer in easybcd to 1 seconds to make it load into it very quickly if nothing else I guess. I was under the impression "restore vista mbr" would just make that whole screen go away.

thanks so far, posting from my linux install again FINALLY!

---

### Post by logos34 on 2008-06-28
> **grimdeath said:**
> however I am still seeing the vista/neogrub options coming up when I click the vista option in grub. do I need to manually delete the neogrub option to skip that whole screen? right now selecting vista two times in a row seems silly! this was where I was at last night when I tried fixing it and screwed things up :P

...I was under the impression "restore vista mbr" would just make that whole screen go away.

yeah, going through two screens is annoying...I'll have to go back and check the easybcd page...maybe you need to actually uninstall easybcd to get rid of those files, then fix the boot of vista (not to be confused with restore bootloader to mbr) which will overwrite the bootsector of the vista partition...lemme see

---

### Post by logos34 on 2008-06-28
try this page:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD)

or maybe just remove the ubuntu entry from the easybcd/neogrub menu and the extra screen will go away:
[http://neosmart.net/forums/showpost.php?p=10239&postcount=2](http://neosmart.net/forums/showpost.php?p=10239&postcount=2)

---

### Post by grimdeath on 2008-06-28
thanks, I will give that a try next time I am in windows which probably wont be today :P

thanks for all your help. much MUCH appreciated.

---

### Post by Computer Guru on 2008-06-29
Just to make sure you understand what EasyBCD does: The menu that you see at boot time is *not* EasyBCD's menu, it's Vista's menu. All EasyBCD did is added an entry to it for Ubuntu (and any other OS you added via EasyBCD).

Uninstalling EasyBCD won't remove that menu.

The boot menu will show if the timeout is both greater than 0 and there is more than one entry visible in EasyBCD.

---

### Post by grimdeath on 2008-06-29
yea sorry I do understand that it is using vista's bootloader. I just referenced it as the "easbycd menu" because I was in a hurry to get things fixed :P

i removed the neogrub setting but havent booted into vista again yet today, I will need to put vista's timer to 0 though according to your instructions so thanks for the heads up!

---

