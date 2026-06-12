---
title: "Upgrade from 8 to 10.4 - general error mounting filesystems"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by The Hypnotoad on 2012-08-28
Can anybody help me out with this please (I have already asked but I asked to start a new thread)

Basically my works computer with ubunutu has no internet access so I only bring it home to update it once every so often.

It was running Heron but I had a lot of problems recently so I took the computer home and updated via the terminal, the computer rebooted after the update and the boot menu loaded up showing I had updated to 10.4. When I go to run however I get a error loading up. I found this post in a previous thread that is basically the same issue as mine.

>                                   **Re: Upgrade to 10.4 - general error mounting filesystems**             
                                                                OK, so this  damn problem has put my linux computer out of commission since upgrading  to 10.04 several months ago. Believe me, I scoured every forum and  tried every other suggested solution out there. Thanks to mcilroy_je for  turning me onto what finally turned out to be the fix.

For any other newbies like me, here's a more detailed description of what to do. 

If you're getting an error something like:
[I]
ureadahead terminated with status 5.
udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2532) killed by ABRT signal.
General error mounting filesystems[/I] 

I suggest rebooting using CTRL-SHIFT-D, and logging into your recovery shell.
Then, try typing at the prompt: 
*locate menu.lst*

If your problem was anything like mine, you'll probably see something like 
[I]/boot/grub/menu.lst
/boot/grub/menu.lst~
/usr/share/doc/grub/examples/menu.lst/usr/share/doc/memtest86+/examples/grub-menu.lst
/var/lib/ucf/cache/:var:run:grub:menu.lst[/I]

The /boot/grub/menu.lst was my menu.lst from Ubuntu 8.04 (what I was using before the upgrade); I took a look at it (*less /boot/grub/menu.lst*)  and sure enough, I could tell it hadn't been changed by the upgrade.  Same old kernels, no changes to my dual boot instructions at the bottom  of the file. Some example menu.lst files in /usr/share didn't seem  weird. But the one in /var/lib/ did seem pretty odd. So I looked at that  (*less /var/lib/ucf/cache/:var:run:grub:menu.lst*) and sure enough, it looked like a newer version of menu.lst. 

So, I wanted to try moving the menu.lst in /var/lib to the boot  directory and try rebooting, in case the upgrade to 10.04 had mistakenly  put the new menu.lst file in the wrong place. To be safe, I first moved  /boot/grub/menu.lst to /boot/grub/menu.lst.save: 

*mv /boot/grub/menu.lst /boot/grub/menu.lst.save* 

Then I copied the other menu.lst into the grub directory: 

*cp /var/lib/ucf/cache/:var:run:grub:menu.lst /boot/grub/menu.lst*

Then I rebooted (CTRL-SHIFT-D), and voila, successful upgrade to Ubuntu  10.04. Hope this works for you. If you continue to get errors related to  flashplugin-nonfree, you might try following the instructions at the  top of [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) first. 

Cheers, and hope this helps someone. 

-Lewis
I tried to do this fix but when I try to move or copy the menu.lst it comes up with an file system error saying 'Read Only File System' error.


Once I can load the computer up hopefully I can upgrade to 12 but at the minute I cant get past this.

Thanks

---

### Post by The Hypnotoad on 2012-08-28
Sorrry to push this but has anybody got any ideas. Ive gone a day without my works computer I cant really go another.

thanks

---

### Post by oldos2er on 2012-08-28
Please do not bump your post more than once every 24 hours.

---

