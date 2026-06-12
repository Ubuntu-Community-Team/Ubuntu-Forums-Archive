---
title: "Need to get windows loader back and re-do grub"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by beartard on 2008-05-26
I helped a friend do a dual-boot install with Windows XP and Hardy on the same physical drive.  Unfortunately, GRUB over-wrote the XP loader, so he can't get into Windows.

I'm assuming I have to use a Windows boot CD to get the windows bootloader back.  After that's done, how do I get Linux to reinstall grub on the linux partition?

---

### Post by meierfra. on 2008-05-26
You don't need to reinstall the XP boot loader  to boot XP. XP just needs to be added to the "Grub menu". Post first let's check whether XP is intact:

Open a terminal in Ubuntu (Applications->Accessories->Terminal) and post the output of
```
sudo fdisk -l
```
( l is a lowercase L)

---

### Post by |{urse on 2008-05-26
insert the windows disk

press R at the first screen

it will ask

Which windows installation would you like to log on to?

press 1

type this at the prompt

FIXBOOT

then type

FIXMBR

to save you windows installation. After thats done let me know and ill show you how to reconfigure grub

*note you'll need the ubuntu livecd to do that.

---

### Post by meierfra. on 2008-05-26
Please do NOT use FIXMBR before you posted your fdisk. (Edit:  Turns out l{curse's recommendation was the way to go.)

---

### Post by beartard on 2008-05-26
I know that the windows partition is intact, as it can be mounted and things copied from it.  I just can't think of a way to get grub to chainload a bootloader that's been overwritten by itself in the mbr.

I'm not at my friend's house, but here are his partitions:
sda1 = windows xp on ntfs
sda2 = swap
sda3 = linux root
sda4 = linux home
sda5 = OEM recovery FAT32

If memory serves, both Linux partitions are logical.  I think swap is a primary one.

All my boxes have been linux-only, so I didn't think to make grub install in the linux root (it's under "advanced" in the install anyway.)

---

### Post by meierfra. on 2008-05-26
O.k then you have to  decide whether you want to add Ubuntu to the Windows boot loader or Windows to the the Grub menu.

The second option is  easier. 

For the first option I still would not do "fixboot" and "fixmbr" right now since you will end up booting into the LiveCD for no particular reason.

For either option please post the output of "sudo fdisk -l" for further help.

---

### Post by meierfra. on 2008-05-26
Didn't see your edit before my post, no need for "fdisk" anymore. So just let me know which way you would like to go.

---

### Post by meierfra. on 2008-05-26
> I just can't think of a way to get grub to chainload a bootloader that's been overwritten by itself in the mbr.

Overwriting the MBR does not destroy the Windows Boot Loader.  The windows boot loader sits in the boot sector of the Windows Partition. The MBR comes before that. 

Add this to the very end of the file  /boot/grub/menu.lst


title XP
root (hd0,0)
makeactive
chainloader +1

Also change 

"hiddenmenu" to "#hiddenmenu"

and 

"timeout 3" to "timeout 10"

and you should be all set.
Allthough I do not understand why the Ubuntu Installer did not allready to that.

---

### Post by meierfra. on 2008-05-26
Or did Grub actually got installed into boot sector of the windows partition, instead to the MBR (this could only happened if you used the "advanced") ? Seems unlikely.

---

### Post by beartard on 2008-05-26
Thanks for all the replies.  Just when you think you know what it takes to make things work, something makes you realize you're a newbie at something else. ;)

I'll see what I can get him to do and post back to you.

---

### Post by wzf851005 on 2008-05-27
These patterns are based on different foot type, weight, Speed, training programmes, gender and skill level design. These different styles, different prices and multi-purpose products, attracting hundreds of thousands of jogging, making them feel that [nike shoes](http://www.bestbuynike.com) is to provide the most complete variety of running shoes manufacturers, millions of range of ability Running to have that belief.   First-generation jordan shoes uppers, there is a conspicuous "Chachi basketball" signs in the use of trapeze signs ago, the first generation and second generation Chachi Jordan basketball shoes are used as signs. First-generation[jordan shoes](http://www.pickyourjordan.com) appeared in 1985, 1994 and 2001 NIKE companies produced twice again this shoes. For the classic colors with a red, black, and compared with black. [Air Jordans](http://www.oknike.com), published in 1991, jordan shoes91-92 season Zhanxue because jordan shoesin the Barcelona Olympic Games 92 wearing this pair of 7 and winning the title, the seventh generation in jordan shoesin the series, it is particularly valuable. 7 and the shape of the shadow of some six generations, the biggest feature is particularly color.  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.

---

### Post by |{urse on 2008-05-27
lol meierfra, why would reinstalling grub after a fixboot, fixmbr be such a bad thing? I mean, wouldn't that be the best way to fix his problem? Besides what harm does fixing windows then reinstalling grub do? I'm not arguing, just wondering why.

---

### Post by meierfra. on 2008-05-27
Let me explain my post #4.

At the time all I knew is that after installing Ubuntu, Windows did not appear on the boot menu. 

 Usually that means that Windows got erased during install. I guess Fixboot and Fixmbr won't  apply   in this case, and your recommendation does not do  any harm, just  some wasted time booting the Windows CD.

The second possibility I see is that, for whatever reason, Windows did not not get added to the Grub menu. In this case one simple needs to edit  "menu.lst".  Even in this case fixboot wouldn't do any good.  

Anyway, it seemed to me that the first course of action is to figure out whether Windows got erased or not.

> Besides what harm does fixing windows
 

Sorry, even until now I do not see any indication that windows was harmed. Overwriting the MBR does not harm Windows.

>  then reinstalling grub do? 
You and  I can reinstall grub in a couple of seconds. But the average  poster finds it rather difficult. So I just like to see "fdisk -l" first, so  that  (if needed) I can give easy direction  on how to reinstall grub. 


Mostly, I was  pretty much  convinced at the time  that "fixboot" and "fixgrub" will not change  anything.


Actually I just realized that I have been  assuming the whole time that Windows does not appear on the grub menu. Looking back over the thread, I'm not so sure sure about that anymore. 
If Windows does appear on the grub menu, then you course of action is much more reasonable, although one should still look at "fdisk" and "menu.lst" first to see whether grub is configured wrongly.

---

### Post by beartard on 2008-05-27
Ok, I got the info requested.  Hope the forums let me attach things. ;)

---

### Post by meierfra. on 2008-05-27
Both "fdisk" and "menu.lst" look ok. So what happens when you choose one of the Windows item at the Grub Menu at boot up. Do you get any error messages?

---

### Post by beartard on 2008-05-28
I had him change the main XP section to the above just for clarity.  The recovery partition boots fine.  The XP partition, when picked, gives no error message, but says "starting up..." and won't do anything.  That's a grub message, right?

---

### Post by meierfra. on 2008-05-29
Sorry, from the way you had described your problem, I had been convinced that "Windows"  does not appear on the Grub  Menu, and had based all my recommendation on that wrong assumption. So

follow |{urse's recommendation from Post 3

Hopefully that  will fix your booting problem. 
 

You need to reinstall grub afterwards. Boot from the LiveCD. Open a terminal, type 

```
sudo grub
```
and at the grub prompt:

```

root (hd0,5)
setup (hd0)
quit
```

---

### Post by beartard on 2008-05-29
Thanks to both of you for your help.  I'll see what we can do!

---

### Post by |{urse on 2008-05-30
I see where the confusion happened ^^ hopefully it all works out.

---

### Post by |{urse on 2008-05-30
It seems more and more people are needing to do a fixboot/fixmbr with later ubuntu installs (when windows actually shows up in grub.conf) and won't boot. Perhaps a crappy service pack was released, weirdness, whether the problem is on ubuntu or window's end it's still odd.

---

