---
title: "[Ubuntu 10.04] Windows 7 not detected on GRUB"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by apreichner on 2010-04-12
**SOLVED:** See my post on the second page.

Alright, I know how much some people get annoyed when people post without searching first. SO I did my best and searched. I found a couple of things, but nothing really that helped.

I was running on a netbook with Windows XP and Windows 7. I deleted the Windows XP partition and installed Ubuntu 10.04 in place of that, after installation no option for Windows 7 was listed. There was an option for Windows XP, but that was for the 5gb recovery partition that ASUS includes on their Netbooks.

First thing I tried was sudo update-grub, that just found the same partitions as before, so no help.

Next thing I tried was this tutorial here: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)  

I might have done something wrong on that one, because i wasn't 100 percent sure which disk it was on, but either way, it didn't work

Next I read through some other posts about it, and couldn't find any answers. But I was able to gather that I should download the boot-info-script, so I went ahead and did that, and heres a link for my results:

**Boot-Info-Script Results:**
[https://docs.google.com/Doc?docid=0AQM8-PKA4rjzZGQ5Yng3Zl83M3RobW40Z2c&hl=en](https://docs.google.com/Doc?docid=0AQM8-PKA4rjzZGQ5Yng3Zl83M3RobW40Z2c&hl=en)

It appears Windows 7 is SDA2, besides that, I'm not sure what to do next. Any help would be appreciated :)

---

### Post by bcbc on 2010-04-12
Try this: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Before you try the above, I'd first boot ubuntu, mount the partition with Win7 (/dev/sda2) and backup anything important, if you haven't already done it.


Edit: Take a look at this link too (for more info): [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
It states that when you install a later version of windows on a computer, it boots via the older version. So when you wiped XP it took out the means to boot win7 too. The boot flag is still on partition that contained XP, now an extended partition containing Karmic. Anyway - hopefully the first link I supplied will solve your problem.

---

### Post by apreichner on 2010-04-12
Yeah it's looking more and more like its not going to work. So I think what Im going to do is backup my stuff and install a fresh Windows 7 and then install Ubuntu. Thanks for your help though.

---

### Post by wilee-nilee on 2010-04-12
> **apreichner said:**
> Yeah it's looking more and more like its not going to work. So I think what Im going to do is backup my stuff and install a fresh Windows 7 and then install Ubuntu. Thanks for your help though.

I suspect the W7 boot files were in XP if you did a fresh upgrade install of W7 with XP on there already.

You might check in at the W7 forums this is a fixable situation probably but a MS-centric person will probably be the best help.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

You might also consider running this bootscript, it is used all the time on this forum.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have nothing to lose though a fresh install of W7 first then Ubuntu is the easiest way of having it all work.

---

### Post by apreichner on 2010-04-12
> **wilee-nilee said:**
> I suspect the W7 boot files were in XP if you did a fresh upgrade install of W7 with XP on there already.

You might check in at the W7 forums this is a fixable situation probably but a MS-centric person will probably be the best help.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

You might also consider running this bootscript, it is used all the time on this forum.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you have nothing to lose though a fresh install of W7 first then Ubuntu is the easiest way of having it all work.

I don't think you read my entire post, because I posted in bold the results to the boot info script... Thanks anyways.

---

### Post by wilee-nilee on 2010-04-12
> **apreichner said:**
> I don't think you read my entire post, because I posted in bold the results to the boot info script... Thanks anyways.

Sorry about that.

---

### Post by DarkForest on 2010-04-12
Try "sudo update-grub2" rather than "sudo update-grub"

---

### Post by wilee-nilee on 2010-04-12
> **DarkForest said:**
> Try "sudo update-grub2" rather than "sudo update-grub"

Wrong!

---

### Post by Grenage on 2010-04-12
I recently did this; all that was required was update-grub, in theory.

That command threw up a few errors and didn't detect Windows.  In W7 partition was an extra *boot* folder, likely a result of my bungled attempt to reinstall grub.  After removing the extra folder (do not remove the W7 one), grub-update worked a treat.

I believe it would have worked straight away, if I'd simply done that from the start.

---

### Post by bcbc on 2010-04-12
> **apreichner said:**
> Yeah it's looking more and more like its not going to work. So I think what Im going to do is backup my stuff and install a fresh Windows 7 and then install Ubuntu. Thanks for your help though.

If you have nothing to lose, I'd go with that first link - at the end there's the 'nuclear holocaust' method.

Also, I may be wrong, but if you re-install win7 to it's current partition, you probably don't need to reinstall karmic as well. It will replace the MBR, but karmic should still be fine. Just boot using the live cd and then reinstall grub2 to the MBR: [http://ubuntuforums.org/showpost.php?p=6391959](http://ubuntuforums.org/showpost.php?p=6391959)

---

### Post by apreichner on 2010-04-12
**I found the solution! **

I had to first set the partition to active (or "boot" in Gparted), and then boot into recovery. Startup repair didn't work out for me, so I went ahead and did it the old school way. I booted up command prompt and did bootrec.exe /FixMbr, and then bootrec.exe /FixBoot. Now Windows is booting up on its own. Next thing I have to do is restore Grub, shouldn't be too hard.

---

### Post by bcbc on 2010-04-12
> **apreichner said:**
> **I found the solution! **

I had to first set the partition to active (or "boot" in Gparted), and then boot into recovery. Startup repair didn't work out for me, so I went ahead and did it the old school way. I booted up command prompt and did bootrec.exe /FixMbr, and then bootrec.exe /FixBoot. Now Windows is booting up on its own. Next thing I have to do is restore Grub, shouldn't be too hard.

Cool!

To reinstall grub to MBR. Boot using Live CD. Then
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
sudo update-grub
```

Edit: added update-grub to get Win7 in the menu

---

### Post by apreichner on 2010-04-12
> **bcbc said:**
> Cool!

To reinstall grub to MBR. Boot using Live CD. Then
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
sudo grub-install --root-directory=/media/sda5 /dev/sda
sudo update-grub
```

Edit: added update-grub to get Win7 in the menu

Thanks for that, it helped a lot. Although the last update-grub command had to be done inside Ubuntu itself as it would not work on the live cd. But that wasn't a big deal. Everything is perfect now, thanks so much everybody!!!

---

### Post by bcbc on 2010-04-12
> **apreichner said:**
> Although the last update-grub command had to be done inside Ubuntu itself
Oops, my mistake. Great you got it sorted.

---

### Post by overdrank on 2010-04-12
Moved to Lucid Lynx Testing and Discussion :)

---

