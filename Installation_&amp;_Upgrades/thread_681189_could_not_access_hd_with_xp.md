---
title: "could not access hd with xp"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by broekskw on 2008-01-28
hi all, had a spare computer with pent4 2.0gig, 256mb 40gb h/drive with xp on, so hooked up another 13gb hd and installed ubuntu, after some time past (about 3 months) i took out the 13gb hd and used it on another machine, so just this morning i fired up the xp maching  but kept getting this error gurb loading please wait, error 21, could not access this hard drive at all,put in the xp recovery disk and everything installed (quick reformat and install xp ) but on load up same error, took hd out and slaved it in another system hoping to reformat the slave and then restart all over but would not detect salve drive:confused::confused:

so as a last resort i put back and loaded a win98 start up disk from a drive  and ran fdisk, finally deleted  the non dos partition and reformated all the h/drive.so as i am typing this out win xp recovery disc is installing all (hope this works)ps and i also tried the live ubuntu cd to reinstall over everything but just kept locking up and error message to reboot.

so my question is, i have another winxp system with a slave ubuntu setup dual boot, if i decided to take away the ubuntu or the xp hd out would it still boot up in 
a: ubuntu (if i took away xp)
b: winxp (if i took away ubuntu)

i think if i took away either hd would i have to change the bootup sequence:confused:

ps looking to keep ubuntu and dropping xp soooooooooooooooooon:lolflag:

---

### Post by broekskw on 2008-01-28
ok installed winxp frome recovery disc and at load up keep getting this message

verifying dmi pool data
grub loading, stage1.5
grub loading please wait
error 21

:confused::confused::confused::confused:
what the beep????

is this hd screwed

---

### Post by Rocket2DMn on 2008-01-28
You should just be able to pop in the Windows cd, boot into the recover console and run
```
fixmbr
```
This will restore window's boot record and give it control of the boot process (no more GRUB).

---

### Post by broekskw on 2008-01-28
Rocket2DMn thanks for your advise, but how do i get a c:> in the recovery disk of win xp, did the recovery disc 2 times now and both times there was not section for a command line??
this win xp cd is a recovery disc not win xp original its from seanix

---

### Post by Rocket2DMn on 2008-01-28
When you put the disc in does it not give you the option to enter Repair by pressing R?
If not, you need to get your hands on a windows xp disc, surely somebody you know must be willing to lend you one.

---

### Post by broekskw on 2008-01-28
thats the only option it gives me so i select r for recovery mode
3 diff options in recovery mode, i keep selecting the one that is fast format and install

sorry mis understood that question 
r for recovery not repair, but i do have an original win xp cd, so try that cd and select repair??

---

### Post by Rocket2DMn on 2008-01-28
Yes, use the original cd please :)

---

### Post by broekskw on 2008-01-28
so Rocket2DMn how would someone take win xp out of a dual boot system then, just disconnecting the maste  hd with win xp on still would not work as ubuntu would not detect the second os correct??

---

### Post by broekskw on 2008-01-28
ok the cd repair option needs a password to run????
did not give this win xp a password??????????????????????????:confused::confused::confused::confused::confused:

---

### Post by Rocket2DMn on 2008-01-28
I'm not quite sure I understand that question, but let me try and explain what happens.
When you install Ubuntu, it sets GRUB as the bootloader and either wipes out window's MBR or sets it aside (not sure which is default, but you can do either).  So when a drive is removed from the system, if that is the drive that holds either the primary MBR or GRUB and is removed, there will problems (since one or both is missing).  
There are relatively easy fixes though.  If you want windows to just load up after Ubuntu is gone, you run the *fixmbr* command from windows' recovery console.  If your GRUB gets overwritten, you can follow any number of the steps found here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you never set a password, the password should probably be left blank.  If that fails, here is an alternative to using fixmbr which uses the Ubuntu LiveCd - [http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)

---

### Post by broekskw on 2008-01-28
Rocket2DMn you the man, at the repair password screen i just hit enter and then i had a c:windows> prompt, then i typed in  fixnbr and windows loads up for a fresh install.

again thanks for all your help.
:lolflag::guitar::popcorn:

---

