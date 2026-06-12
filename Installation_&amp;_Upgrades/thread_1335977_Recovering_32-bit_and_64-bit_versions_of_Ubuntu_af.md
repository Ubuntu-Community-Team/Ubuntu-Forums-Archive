---
title: "Recovering 32-bit and 64-bit versions of Ubuntu after upgrading to Windows 7"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by Professor_Ding on 2009-11-24
Hi all,

I've tried searching a few forums, but I think I have a fairly specific problem on my hands. A few months ago I bought a new computer and installed Vista. I then installed Ubuntu 9.04 64-bit as a dual boot since I needed to use a specific specialist program. Said program didn't work in 64-bit mode however, so I next installed Ubuntu 9.04 32-bit and the program worked as intended. So I had a triple boot system going, but I'd only use the 32-bit version of Ubuntu.

Recently I upgraded from Vista to Windows 7 using an upgrade disc which was supplied as part of the recent promotion. Following that my computer would only load to Windows 7. So I did the usual fix for that by putting in the Ubuntu CD (I tried using the 32-bit one), running a live session, reinstalling GRUB, and then going back to edit GRUB later on to have it point to Windows 7 again.

My problem here is that the version of Ubuntu that was restored was the 64-bit version, and that I don't know where the 32-bit version is anymore. So, is there a way to get back the 32-bit version?

I have a very good feeling that I'm missing several key bits of information that will be needed to get a solution from you guys, but I'm away from said computer so I can't quite fill in all of the details at the moment, but will get back with more info where needed. 

Some vague recollections: I think each time I installed Ubuntu (64- and 32-bit) I set aside different partitions, but I can't remember if they ended up sharing the same swap disk. I think the first installed one, 64-bit, had the partitions hd0,5 and hd0,6, and the second one might have had 7 and 8, I'm not too sure.

My other question is following all of this, how do I go about uninstalling the 64-bit version? I probably should've done that before updgrading to Windows 7, but at the time things were working fine anyhow.

Thanks for reading.

---

### Post by darkod on 2009-11-24
If the 64bit ver was not useful to you, you should have just installed 32bit over it (using the same partitions). That would achieve two things, your 64bit will be gone and 32bit will be installed as you needed.
But anyway, you are right. If you have them on separate partitions it's just a question modifying /boot/grub/menu.lst to add another entry for Ubuntu 32bit poiting to the correct partition.
Since 64bit entry in grub menu is working, my advice is to copy the whole entry in menu.lst which relates to 64bit and then change the title line something like:
title Ubuntu 32bit

and also the root(hd0,5) accordingly to where your 32bit version is. After the change save and close the menu.lst file, reboot and test your new entry.
In case you don't know how to edit the file:
sudo gedit /boot/grub/menu.lst

PS. If you re not sure on which partition is what, you can check with
sudo fdisk -l (small L)

That will list all partitions. If you are still not sure post the result here and we'll try figure it out.

---

### Post by Professor_Ding on 2009-11-24
Thanks darkod, I'll try that out later when I get home today (it being morning where I am at the moment). As it stands I use Ubuntu very little; perhaps I should start changing that. Thanks for the help so far though.

---

### Post by Professor_Ding on 2009-11-25
Ah, I figured it out, sort of. Partition 5 ended up being the 64-bit version I installed first, and partition 6 ended up being the 32-bit version (both using the same swap disk). I went over the original steps to reload GRUB and have it point to partition 6 instead, so now I'm back to having a triple boot selection again, which is still a little messy, but it's what I originally wanted at least.

I guess I didn't originally install the 32-bit over the 64-bit since I wasn't quite sure why the program wasn't working (not that I would've really known how to install the 32-bit over the 64-bit). That said, what would the steps be now to uninstall the 64-bit version? From the little that I've managed to gather reading forums, it sounds like I could format that partition and then simply delete the entry for it in the GRUB loader (and since GRUB will still be pointing to a valid Ubuntu things won't break as badly as it has for others I presume?).

Finally, given that I want to get rid of the 64-bit version, what are the steps to upgrading to 9.10? I'm planning on using the Alternate upgrade CD (having downloaded it already). Or should I not really bother: my main OS is still Windows and I only really use Ubuntu for one specific program (specialist calculations basically).

Thanks for reading.

---

### Post by coffeecat on 2009-11-25
A few thoughts.

Pause a moment before you delete the contents of your 64-bit partition. If you are using grub stage 2 and the grub menu from that partition you'll make your system unbootable - Windows included. Until you re-install grub stage 1 from the 32-bit partition that is.

Anyway, it seems to me that since your 64-bit partition is surplus to requirements, the easiest thing would be to install Karmic to that partition. You wouldn't even have to bother deleting anything, because the Karmic installer will reformat that partition before writing all the Karmic files to it. And the Karmic installer will re-install grub, detect your Jaunty and Vista partitions (hopefully :|) and set you up with a triple-boot menu.

One slight downside is that [Grub 2]("https://help.ubuntu.com/community/Grub2") comes with Karmic, which is a whole new ball game. Let me be clear :) - the downside is the new ball-game not grub2 itself which works quite well.

The advantage of doing that is that a fresh install avoids a dist-upgrade which some people report having problems with, and if Karmic doesn't live up to expectations, or doesn't like your machine, then you've got Jaunty to fall back to.

---

