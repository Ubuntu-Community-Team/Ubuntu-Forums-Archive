---
title: "Dual Boot Installation"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Norster on 2006-11-26
I have a dual boot system at the moment with windows 98 on drive C and XP on drive D. I do not use win98 anymore, and would like to try using Ubuntu. Is there any problems with installing Linux on drive C in place of win98 ?

Any help or advice would be appreciated.

:confused:

---

### Post by bulldog on 2006-11-26
Yes there are problems with that.
If you use your c:\ to install ubuntu I'm pretty sure you can't boot into XP anymore.
This is because the boot files for XP are on the c:\ drive.

If you want to keep XP,install it on the first primary partition and install Ubuntu on d:\ ,because Ubuntu don't mind where it's installed.

---

### Post by Norster on 2006-11-26
Thank you, Bulldog - very helpful.:-k

---

### Post by Bartender on 2006-11-26
Do you have your XP disc or can you get ahold of one?  I don't think this works with those stupid "Recovery CD"s you get from the big box manufacturers.  If you can find a genuine XP CD then see what you think of the following...

I'm not sure this would work but I think it will.  Go online and google "fix mbr".  There are guides on Elder Geek, Kelly's Corner, etc.  Print out a couple, read them thru until you feel like it makes sense.
Take your  second HDD, the one with XP, and do whatever you have to do to make it the primary HDD on your IDE cable.  Move the jumpers on the back of the drive, place the drive on the last clip on the IDE cable, that sort of thing.  If you have an 80-wire IDE cable I'd just set the HDD jumper to Cable Select, move the drive to the last clip on the IDE cable, then go into BIOS to make sure it's recognized as the primary IDE device.  Now boot from the XP CD.  Follow the steps to repair the MBR.  Unless I'm all messed up on this your XP disc should now function just fine.

If you were contemplating wiping the disc and reinstalling what have you got to lose?

Then search right here on this forum for some guides to dual-booting with a second drive.  I don't think it's much different than dual-booting on a single drive.  Use the Ubuntu install CD to reformat and install to the second drive, and install GRUB to the first drive (that'll be hd0 in "GRUBspeak") and you should be good to go.

I welcome second opinions!  Not sure if this is a viable procedure but think it is...

---

### Post by bulldog on 2006-11-26
Bartender you are absolutely right and I think it should work.

But you and I read the OP different :D 
Don't know who reads it right though ](*,) 

I had the idea he had just one hdd with two partitions,you saw two hdd's,maybe can OP enlighten us?

If he have two disks then the my answer is not the right thing to do.

---

### Post by Bartender on 2006-11-26
Whoops 

You're right.  I read it and assumed 2 separate HDD's although the OP didn't actually say anything to indicate that's the case.

Yeah, Norster, my proposal was based on 2 separate HDD's.

However, it sounds like Bulldog is saying it won't work?

*"If he have two disks then the my answer is not the right thing to do."*  


Maybe I shoulda just stayed out of this thread... :-#

---

### Post by bulldog on 2006-11-26
No glad to see you here,now we have two angles to look at.

If he has two drives he has to pick your answer,if he has just one hdd,he better listen to me :D

---

### Post by Norster on 2006-11-26
Actually, Glad both of you are here.

I didn't specify, but I do have 2 HDD.:oops:

---

### Post by daveg2 on 2006-11-26
I almost hate to get involved as I found my first dual-boot to be real frustrating---and I sure don't want to be considered an expert.  My 2c:

My proposal is to unplug the WinXP drive so that XP is safe.  Do the install of Ubuntu on the only drive, the Win98 drive.  Let it write grub to the MBR, the master boot record.  When you get done, you'll be able to boot into Ubuntu, but not XP.  Don't panic.

Now edit /boot/grub/menu.lst.  Find this line:
### BEGIN AUTOMAGIC KERNELS LIST

Put the following code right before the automagic line:
title Windows XP
map (hd1) (hd0)
map (hd0) (hd1)
root (hd1,0)
chainloader +1

Note the two map lines.  These are the key to making it work.  Windows requires that it be on the primary drive of the first IDE channel.  Grub fools XP into believing that it is on the first channel.  The chainloader command in grub runs the standard XP loader that is in the MBR of the XP drive.

Plug the XP drive back in, and grub should allow you to boot from the menu into either OS.

Now if I can be allowed to back-pedal.  This is based on two ide drives, both being primary on one of the two ide channels.  XP is the primary on the second channel, as apparently is yours.  It works for me, but things can go wrong.  Please search and review enough dual-boot threads and how-to dual-boot WIKIs so that it makes sense.  And please don't expect me to have the knowledge to solve it if things go wrong.  This is only a suggestion.  

Before doing anything, please unplug your Win98 drive and plug your XP drive in it's place.  Does WinXP boot?  If so, this should work, if not, then the windows loader is on the Win98 disk and all bets are off.

---

### Post by confused57 on 2006-11-26
> **Norster said:**
> Actually, Glad both of you are here.

I didn't specify, but I do have 2 HDD.:oops:
Here's how I have my system set up:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

This way you don't install grub to the Windows mbr...works for me, some use bios to boot the different drive OS.

---

### Post by Norster on 2006-11-26
Thanks, Confused57 - that's a real help.

---

