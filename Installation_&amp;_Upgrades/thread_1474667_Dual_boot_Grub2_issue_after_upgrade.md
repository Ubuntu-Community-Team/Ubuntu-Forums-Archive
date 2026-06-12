---
title: "Dual boot Grub2 issue after upgrade"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by politenessman on 2010-05-06
I'm running an Acer 1810Tz, dual boot with win7.
Under 9.10 and Grub I had no boot issues, however I have just completed the upgrade to 10.04 and upgraded GRUB to GRUB2.

Everything boots just fine into Ubuntu, and my GRUB menu looks right, but when I select the Windows 7 option, the machine just hangs with a black screen, white cursor top left. 

I'm sure this is a trivial problem, something overwritten that shouldn't have been perhaps, but I have no clue where to start. Can anyone point me in the right direction?

---

### Post by dino99 on 2010-05-06
so boot with lucid, then:
you need to know where lucid is installed:
 into console: fdisk -l

check that the old grub menu.lst is removed completly; into synaptic:

remove/purge ALL the grub packages installed then install grub-pc and grub-common
when asked, install grub on the lucid mbr partition 

sudo grub-mkconfig && update-grub

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14 

(hope the actual problem is not due to windows bootloader been erased by grub)

---

### Post by sylvester_0 on 2010-05-06
Try running sudo grub-install and see where that gets you. If that doesn't work, you could follow the tutorial [here]("http://ubuntuforums.org/showthread.php?t=1014708") to restore your Windows 7 bootloader (I believe this will get rid of GRUB) then boot up a live image of Ubuntu and run sudo grub-install again.

---

### Post by politenessman on 2010-05-06
> **dino99 said:**
> so boot with lucid, then:
you need to know where lucid is installed:
 into console: fdisk -l

Lucid = 10.04?

Right now Ubuntu works fine, its Win7 I can't boot into.

---

### Post by politenessman on 2010-05-06
I think this is the problem ([From this thread](http://ubuntuforums.org/showthread.php?t=1469475))

> Re: Known Lucid Lynx issues/bugs with workarounds
A lot of users are overwriting their windows boot sector due to a confusing message with the grub2 install. It says something like 'Choose where to install grub. If you are not sure select all partitions'. And this leads some to select their windows partition.

The fix and diagnosis is at: [http://sourceforge.net/apps/mediawik...ms:Boot_Sector ](http://sourceforge.net/apps/mediawik...ms:Boot_Sector )courtesy of meierfra.

Note this is not the same as the bug that caused the re-release of certain iso's. That had to do with the windows not being listed in the grub menu. In this case, the windows option is listed but fails to boot.

---

### Post by kansasnoob on 2010-05-06
Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by rotosvili on 2010-05-07
> **kansasnoob said:**
> Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Don't know about the OP, but this did the trick for me. I had just the same problem, only a blinking cursor appeared  when trying to boot into Windows XP. Thanks a lot.

I think I got into this mess when updating to grub2 and it prompted to select where grub should be installed and I selected windows drive and linux drive. Somehow this corrupted the boot sector of the XP.

---

### Post by mkehinde2 on 2010-05-07
<snip>
I can confirm that this fix worked for me with Windows 7 and Ubuntu 10.04 dual boot

---

