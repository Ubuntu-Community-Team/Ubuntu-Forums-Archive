---
title: "Properly multi-booting grub with Windows first"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2010-03-05
I wanted windows to appear first in my grub2 menu so I renamed the 30_os_probe file(or whatever it felename is) to 09_os_probe so that it comes before the 10 linux file, problem is whenever these files get updated the updater is unable to find the 30_os_probe file since I renamed it and recreates it... leaving me with two versions (09 and 30) with 09 being of course outdated.

The updater also fails to run update-grub and instead attempts to update grub.cfg manually... and fails. I had to manually do a sudo update-grub.

Is there any way to fix this so its all updated automatically while leaving windows the top choice? No manual intervention required beyond clicking "install updates"?

Also, is it possible to JUST have the Windows and Ubuntu choices, no Ubuntu recovery, memtest, alternative(older) kernels for Ubuntu, etc in the grub menu?

---

### Post by Timothy Taylor on 2010-03-05
You used to be able to edit /boot/grub/menu.lst, but this file seems to have disappeared in 9.10

Try searching for help on GRUB menu options??

---

### Post by leandromartinez98 on 2010-03-05
Check this post of mine. You can easily edit the 06_custom I provide
to put windows first. And it is updated automatically.

[http://ubuntuforums.org/showthread.php?p=8280606#post8280606](http://ubuntuforums.org/showthread.php?p=8280606#post8280606)

Be careful to check the details of the Windows drive specification, copy
them from your current /boot/grub/grub.cfg file.

---

### Post by oldfred on 2010-03-05
Did you make the new 09 executable and turn off the executable on 30?

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)
sudo chmod 755 /etc/grub.d/09_custom

Or you can add this, but I do not know if it will run your 09_custom?
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

Alternative way:
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

---

### Post by hatalar205 on 2010-03-05
Why don't you try "StartUp-Manager"? It is so simple and useful.

---

### Post by Cyber Akuma on 2010-03-05
> **Timothy Taylor said:**
> You used to be able to edit /boot/grub/menu.lst, but this file seems to have disappeared in 9.10

Try searching for help on GRUB menu options??

The new grub uses a grub.cfg file that you are not supposed to edit, because its generated off of several separate modular files and its THOSE you are supposed to edit. There is no more menu.lst

> **leandromartinez98 said:**
> Check this post of mine. You can easily edit the 06_custom I provide
to put windows first. And it is updated automatically.

[http://ubuntuforums.org/showthread.php?p=8280606#post8280606](http://ubuntuforums.org/showthread.php?p=8280606#post8280606)

Be careful to check the details of the Windows drive specification, copy
them from your current /boot/grub/grub.cfg file.

Wouldn't doing that just add two Windows entries, one at the beginning when it uses 06_custom and one at the end when it uses 30_os_probe? Not to mention IIRC there is a dedicated 40_custom file for these kinda things...

> **oldfred said:**
> Did you make the new 09 executable and turn off the executable on 30?

[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries)
sudo chmod 755 /etc/grub.d/09_custom

Or you can add this, but I do not know if it will run your 09_custom?
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER="true"

Alternative way:
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

I don't understand, what do you mean turn off the executable in 30? 30 didn't exist anymore, since I renamed it to 09. Problem is the updater didn't realize this and assumed 30 no longer existed and asked to re-create it, leaving me with an outdated 09 and updated 30.

I don't want to disable os probing, I just want it to run os probing BEFORE adding the linux entries, if there is a way to tell it to run 30 BEFORE 10 that would be ideal since then I wouldn't need to rename files.

Though I hope the other dialog I got because it couldn't update menu.lst/grub.cfg also goes away...

Not to mention I only want there to be one Ubuntu entry and no memtest entries...

> **hatalar205 said:**
> Why don't you try "StartUp-Manager"? It is so simple and useful.

Is that compatible with the latest grub? Would I need to run it every time there is a kernel update or update-grub is run?

---

### Post by meierfra. on 2010-03-06
> problem is whenever these files get updated the updater is unable to find the 30_os_probe file since I renamed it and recreates it.

You have to let package manager know that you renamed os-prober:

```
dpkg-divert  --local --divert /etc/grub.d/09_os-prober --rename --add /etc/grub.d/30_os-prober
```

> The updater also fails to run update-grub and instead attempts to update grub.cfg manually... and fails. 

What do you  mean with "attempts to update grub.cfg manually"?

---

### Post by Cyber Akuma on 2010-03-06
> **meierfra. said:**
> What do you  mean with "attempts to update grub.cfg manually"?

You know how with the old grub, if there were too many manual modifications to menu.lst a dialog would come up with options like "keep the current version, update to latest version, do a 3-way merge, open it in a text editor" etc etc? That came up again, although I thought I would never see this thing again with grub2.

Thanks for the suggestion by the way, I will try it next chance I get, is there any way for me to just flat-out remove the memtest or older kernel Ubuntu entries by the way? I ideally I just want there to be two options in the menu, windows and ubuntu.

---

### Post by leandromartinez98 on 2010-03-06
> **Cyber Akuma said:**
> 
Wouldn't doing that just add two Windows entries, one at the beginning when it uses 06_custom and one at the end when it uses 30_os_probe? Not to mention IIRC there is a dedicated 40_custom file for these kinda things...


The good of being a 06_custom is that your custom menu will appear at the top, not after the buch of linux kernels that you don't want to see. Furthermore my 06_custom is such that it updates to the newest linux kernel on every update. Therefore, once it is there you don't mess up with these files anymore.

And yes, if you keep the 30_os_probe you will have two windows entries. But, as is explained there, there will be a separator between the two real options (Windows and Latest linux kernel) and the remaining options. From the point of view of functionality it is perfect (for me, at least). If you feel that it is unahesthetic you can remove the executable character of the other files (greater than 06), so that nothing else appears. 

Anyway, that example has everything you want, just use your creativity now.

---

### Post by Timothy Taylor on 2010-03-06
> **Cyber Akuma said:**
> The new grub uses a grub.cfg file that you are not supposed to edit, because its generated off of several separate modular files and its THOSE you are supposed to edit. There is no more menu.lst

Why was this changed?
Any idea which files you're supposed to edit? I tried searching help / man / info, but couldn't find any documentation on this.

:confused:

---

### Post by kansasnoob on 2010-03-06
> **Timothy Taylor said:**
> Why was this changed?
Any idea which files you're supposed to edit? I tried searching help / man / info, but couldn't find any documentation on this.

:confused:

Good place to start:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics)

---

### Post by meierfra. on 2010-03-06
> I ideally I just want there to be two options in the menu, windows and ubuntu.

Then I would  follow oldfred's last suggestion and use this [Howto]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

### Post by Timothy Taylor on 2010-03-06
> **kansasnoob said:**
> Good place to start:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics)

Blimey!
:eek:

It looks like they've taken something simple and straightforward and made it unnecessarily over-complicated.
:(

---

