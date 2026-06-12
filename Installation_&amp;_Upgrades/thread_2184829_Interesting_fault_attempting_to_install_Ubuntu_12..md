---
title: "Interesting fault attempting to install Ubuntu 12.0.4.3 OR 13.10 on MSI GS70 2OD-001U"
date: 2013-10-30
forum: Installation &amp; Upgrades
---

### Post by jajed on 2013-10-30
[COLOR=#333333][FONT=UbuntuRegular]Attempting to install Ubuntu on an MSI GS70 2OD-001US notebook pre-installed with Windows 8.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]For the record this is what I have attempted:
[/FONT][/COLOR]
*OF NOTE: EVEN LIVECD/USB WILL NOT LOAD*

[COLOR=#333333][FONT=UbuntuRegular]All cases were attempted with Ubuntu 12.0.4.3 AND 13.10 images via USB drives 
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Case 1 - Attempt no changes and simply boot from USB[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Result: It seems to want to work initially. The Ubuntu logo pops up and the dots start moving. After a few seconds the dots freeze and this screen is shown: [http://i.imgur.com/C7pyMRk.jpg](http://i.imgur.com/C7pyMRk.jpg)
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Case 2 - Start playing with BIOS - In Windows turning off fast boot - In BIOS turning off Secure boot - In BIOS turning off UEFI and selecting LEGACY[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Result: Brought to a black screen with a - blinking at me.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Case 3 - Alternating BIOS settings - In Windows turning off fast boot - In BIOS turning off Secure boot - in BIOS turning off UEFI and selecting UEFI with CSM[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Result: Brought to a black screen no other indication of change.
[/FONT][/COLOR]
I've gone through quite a number if posts regarding this, and seen people have success... 

[COLOR=#333333][FONT=UbuntuRegular]It's pretty frustrating to feel locked out of a laptop that I have paid good money for, I'm sure I am not alone in that case. It does however appear that there has been some success, so I am hopeful that someone might be able to help me.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]FYI: Dual booting is not necessary for me, if that helps at all...[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I'm not sure if this is a reasonable option, but if I completely wipe clean the hdds, no particle of Windows at all, would this still be a problem? Also would opening up the laptop and replacing the HDDS with brand new ones be a solution as well?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks for any input or suggestions.

*update*

of note, attempting to install Debian via USB results in similar failures

*update #1*

i found this which specifically references a similar model of my laptop: [/FONT][/COLOR][http://askubuntu.com/questions/272728/ubuntu-12-10-black-screen-after-grub-cant-install-uefi](http://askubuntu.com/questions/272728/ubuntu-12-10-black-screen-after-grub-cant-install-uefi)
although nothing new was suggested, i followed the instructions on the answer to no avail. Same stopping point at the fault or black screen of nothing.

*update #2*

from the MSI forums this appears to be a very specific thing that MSI has done to their UEFI implementation (likely in cahoots with Microsoft)  there may be solutions in the future but for now steer clear of MSI 2012-2013 notebooks if you aren't happy running Windows on it.  Notebook is being returned. Such a shame, the hardware was fantastic.

---

### Post by lode.cools1 on 2013-11-03
Exactly the same problem here on 13.10... MSI GE70-2OE.

[http://i.imgur.com/LvYzFne.jpg](http://i.imgur.com/LvYzFne.jpg)

I have also tried 12.10 & 13.04: there i just get the GRUB screen and then a blank black screen when trying to run ubuntu live or install.  I tried to solve that using many suggestions on the net (adapting command: 'nomodeset' etc...) ... didn't work.

Hopefully some brighter minds can find a solution :)

---

### Post by jajed on 2013-11-03
From this bug list it looks like the issue is with the [COLOR=#333333][FONT=Ubuntu Mono] NVidia GTX765M[/FONT][/COLOR] graphics card preventing the kernel from loading: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1225646](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1225646)

If that looks to be the same issue (which I think it is safe to say) then feel free to file a report, or check in there that you are also affected.

---

