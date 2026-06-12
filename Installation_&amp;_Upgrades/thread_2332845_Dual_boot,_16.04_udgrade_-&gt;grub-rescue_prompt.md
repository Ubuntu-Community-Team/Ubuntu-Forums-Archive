---
title: "Dual boot, 16.04 udgrade -&gt;grub-rescue prompt"
date: 2016-08-04
forum: Installation &amp; Upgrades
---

### Post by Chris_Dinant on 2016-08-04
[COLOR=#000000][FONT=UICTFontTextStyleTallBody]I have a dual boot system with windows 10. I hadn`t touched ubuntu for about a year. Now I upgrade to 16.04 and it wont boot anymore.[/FONT][/COLOR]

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]I get the grub rescue prompt. [/FONT][/COLOR]

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]So I used the live disk to get into boot-repair. before running it asks if the 120Gb disk (the SSD it should boot from), is portable or not (it is not) and tells me to look at the options because it found a separate /usr on a different drive (I put that folder on a larger HD). Not sure what options to change or why it should matter.[/FONT][/COLOR]

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]After I run the repair it ends with an error message: Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again. No package managers open.[/FONT][/COLOR]

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]I uploaded a boot info script file created by boot-repair here: [/FONT][/COLOR][http://paste2.org/vNCXNLWe](http://paste2.org/vNCXNLWe)

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]I would be eternally grateful if someone could have a look and help out.[/FONT][/COLOR]

[COLOR=#000000][FONT=UICTFontTextStyleTallBody]Chris[/FONT][/COLOR]

---

### Post by oldfred on 2016-08-04
Boot-Repair cannot fix a system with its commands as it does not mount separate system partitions except /boot if that is separate. So your /usr and /var prevents Boot-Repair from making repairs. You have to chroot into system manually including the extra mount of /usr and /var. Most instructions will not show that.

Update: It looks like Boot-Repair now does try to mount /usr.

Did you have Ubuntu fully updated for trying to update to 16.04?
And did you have any ppa or proprietary drivers. Those have to be commented out or reverted to defaults or you often have blockage on upgrade which prevents it from finishing.

And good idea to houseclean old logs & kernels before upgrading to new version.

Your still showing older kernels, so I do not think upgrade completed at all.

While a chroot & major repairs is possible, it may just be easier to backup your data and reinstall.

---

### Post by Chris_Dinant on 2016-08-05
I did do all the updates before upgrading, but I think it asked me during the updates if I wanted to update grub and I said no, because I thought it might break the boot. Perhaps I should have said yes...

I will try a reinstall. thanks.

---

