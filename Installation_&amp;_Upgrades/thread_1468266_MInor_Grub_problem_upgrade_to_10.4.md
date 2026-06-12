---
title: "MInor Grub problem upgrade to 10.4"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by raybarrow on 2010-05-01
Dual boot Ubuntu/Vista laptop

Upgraded from 9.10 to 10.4 online. Everything went smoothly although it took over three hours.

Grub Menu shows the Ubuntu options as expected. The Vista option is shown as 'Windows Recovery Module...'

It boots into Vista just fine, but before I upgraded it was called 'Windows Vista...'

As it's Grub 2 I can't see a way of altering the text to 'Windows Vista...' as I could have done in Grub 1.

I have run sudo update-grub.

I know it's minor as it all works but it would be nice to sort it.

Cheers,
Ray.

---

### Post by oldfred on 2010-05-01
This is one thing that grub2 does not make easy. Grub2 is now mostly scripted to auto generate the grub.cfg file you you do not edit. 

You can modify the scripts to see the correct name. You can turn off the script function for other systems and paste in the current entry into 40_custom which then is totally editable. I have done a little of both.

Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

OR:
Copy your current windows entry into :
/etc/grub.d/40_custom

edit the description the way you want 

run:
sudo update-grub

You should have your original entry and the new entry. Make sure the new entry works.

Then so it does not automatically find your recovery entry:
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

Update grub.cfg again
sudo update-grub 

OR:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

IF you want windows first:
If you save the file you create with the custom entry to, say, 09_custom, it will not be over written and will be at the beginning of your menu
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)

---

### Post by raybarrow on 2010-05-03
Thanks Oldfred. That looks comprehensive enough to sort it out. It's curious as to why it chose that option when the 9.10 I upgraded from chose the 'correct' one.

When in the upgrade process it asked about do I want to keep the 'local copy of Grub'(which was Grub2) or choose 'the installers version' I chose the installers version. I can't beleive that made the difference. I'll see what happens when I upgrade the desktop which is Dula boot with XP rather than Vista.

Thanks again,
Ray.

---

