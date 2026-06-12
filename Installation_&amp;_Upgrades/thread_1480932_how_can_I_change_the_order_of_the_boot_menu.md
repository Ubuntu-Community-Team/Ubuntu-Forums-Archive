---
title: "how can I change the order of the boot menu"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by mjsilverstri on 2010-05-12
Hi,

I have installed 
1. ubuntu 10.04 on a different partition of a windows 7 machine.

and it is order of the boot menu is
1. ubuntu 10.04
2. memtest
3. window 7

Then I install kubuntu 10.04
and the boot menu is 
1. kubuntu 10.04
2. memtest
3. window 7
4. ubuntu 10.04

Can you please tell me how can I make ubuntu 10.04 my 'default' (i.e. if i don't select anything it will boot that OS)? How I need to scroll down to 4 and then click ENTER.

Thank you.

---

### Post by oldfred on 2010-05-12
You could reinstall grub2 from Ubuntu so it is the grub in charge.

You can just do this:
[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.

Or if you want to totally customize menu:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
OR:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

---

