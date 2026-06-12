---
title: "Oh boy... general state of panic!"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by robenroute on 2006-06-14
Well, that's slightly exaggerated, but something rather serious did happen. Just to make this clear, it's all my own doing, so :-$ ...

I installed Dapper LTS and instead of using the alternative version, I used the bs (bog standard) one. Hey, how was I to know? Wizzing through the installation process, I got to the partitioner and after setting it all up, I rebooted, just to find out that my BootIt NG (boot manager) had been sent into the big blue void; grub was now residing on my mbr (instead of the partition boot record, as I expected). Oh fiddlesticks!

The new grub boot menu shows my different partitions and bootable systems, but, of course, they're not bootable since the entries in the menu.lst files are wrong! Wrong? Yes, wrong. What's happened is that all (indeed, not a single one is unaffected) my partitions got a new partition number. Example:

XP, used to be /dev/hda1, is now /dev/hda5
Breezy, used to be /dev/hda6, is now /dev/hda7

Of course I've edited the /etc/fstab and the /boot/grub/menu.lst files. I've also installed grub to the "new" partitions (with grub-install). Alas, no success. It looks like good old Breezy is going to boot just fine, when selected from the grub menu, but it somehow can't figure things out...

Does any one have an idea to help me out here? Might there be a simple way to reorder/move the partitions? Much obliged.

Regards,

Rob

---

### Post by zxee on 2006-06-14
If you can get into the grub command line i.e grub>  then you can type find /boot/grub/stage1 <enter> that command should return partitions in grub notation e.g. (hdx,x) where the x's are the actual numbers of the drive & partition. If you get that (grub outputting a partition it finds stage1 on) then you can type setup (hdx,x).
You can also chroot to any of your partitions and do the sequence I've outlined above from that.  If grub successfully sets up the partition it so indicates. You should then be able to re-boot and see that it works. Hope that helps.

---

### Post by robenroute on 2006-06-14
Hi zxee,

Thanks for your reply. Unfortunately, I get thrown back at the shell (#) and I'm unable to get into grub (grub command doesn't do anything, apart from not being recognized). I'm not sure I understand what you mean with the chroot command. Typing chroot /dev/hda7 "command" results in being notified of the fact that nothing has been mounted on /dev.

Am I missing something?

Thanks again.

---

### Post by ikd69 on 2006-06-14
Well,  try with a live CD and see if it works.  Otherwise, do as I did and reinstall everything from the beginning :sad:  You may have to do so, if your system is beyond repair.  

I.

---

### Post by mjm115 on 2006-06-14
It appears that the MBR has been hosed.  Reinstalling would probably be the easiest option.

---

### Post by ikd69 on 2006-06-14
[QUOTE=mjm115]It appears that the MBR has been hosed.  Reinstalling would probably be the easiest option.[/QUOTE]

Yes, do so.  After wasting two afternoons and several CDs, I finally opted for the clean install route, and everything worked fine.  Besides, if the trouble is with the mbr, you may not have much of a choice.

I.

---

### Post by robenroute on 2006-06-14
[QUOTE=ikd69]Yes, do so.  After wasting two afternoons and several CDs, I finally opted for the clean install route, and everything worked fine.  Besides, if the trouble is with the mbr, you may not have much of a choice.

I.[/QUOTE]

Fair enough, re-installing is an option. However, I do believe there is a way of moving partitions about. Admittedly, I have never heard about it, but it just sounds too logical (and too good?) to not be an option. I will start mucking about and report back with the results.

In the mean time, if anyone knows of measures that would get me in the right direction, please, don't hesitate posting them!

Thanks for all the replies guys....

Rob

---

### Post by robenroute on 2006-06-20
After long trying, mucking about and pulling my hair, I decided to just wipe the whole HD clean. I had XP on the old setup, but it's not there any longer.... We'll see how it goes without Windows.

Thanks again.

---

### Post by robenroute on 2006-09-10
Stumbled across this ol' thread of mine; thought I'd let you know how I've been keeping my life together without XP. Well, it's been fair, sunny, warm and pleasant so far. Haven't had any spells of rain, hail, snow ot otherwise impeding weather (apart from the rather clumsy release of that X.Org update that swept Drakie's legs from under him). Perhaps I could sell my XP-Pro license back to MS, hmmm...

---

