---
title: "aborted install rendered laptop useless"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by mendo on 2008-07-20
alright - here's one for ya:

i pulled my old toshiba satellite 2805 laptop out of storage to try to install ubuntu and play.  it had winxp on it.  i put the live cd in and tried to install.  the install continually froze - every time i tried to install after a hard reset, i would get a bit further.

finally i had all partitions deleted, a 10GB ext3 partition mounted as root and a 4GB swap partition set up and i was installing.  the dialogue froze at something like "checking file system" or something like that - it was stuck at 15% complete.  since i had been continually hard resetting and starting the install over again, that's what i tried to do.  but this time, all the windows partitions had been deleted and i couldn't boot from the live cd.

i got an error that said "insert system disk in drive.  press any key when ready..."  i tried to boot from the alternate cd - same thing.  i checked in bios to make sure that cd was the first boot device - made no difference.  i even tried the original system restore cd that came with the laptop about 10 years ago - same thing.

i don't know what's going on here.  i don't understand why i can't boot from anything.  it's almost as if my cd-rom drive is dead, but it can't be - i was running the live cd from it all day.

any ideas what may have happened or what i can do to fix it?

thanks in advance for your help.  i am in awe of the ubuntu community and the movement.  i look forward to learning enough to help others someday.

thanks.

---

### Post by Wazoot on 2008-07-20
hmmm...
this looks like a hard problem to solve...
I can't think of anything.
Call toshiba for help maybe? if you want to wait through all the customer service stuff ;]
All i can think of right now is just keep trying
What version of ubuntu are you trying to put on?

---

### Post by mendo on 2008-07-20
i'm trying to install 8.04.  i am not getting anywhere with this thing.  i think i'm gonna get my winxp install cd and try to boot off that.  i'll keep you posted.  thanks for the reply.

---

### Post by Wazoot on 2008-07-20
anytime
just keep me posted ill help as much as i can =]
maybe if you can get XP back on there, you might be able to get somewhere with Linux. then you can take XP back off if u want.  {im not exactly a Ubuntu expert, but ive collected knowledge from messing around with it/from the internet. ^.^}

---

### Post by mendo on 2008-07-20
that's what i was thinking.  everything was clicking along when i had xp on there, maybe i'll get back to where i started and go forward from there.

---

### Post by Wazoot on 2008-07-20
yeah
do you have a diff computer you are using to post here?
lol
j/w =]
but yeah hopefully you can get things working on your laptop, post back if you have anymore help with it!

---

### Post by lisati on 2008-07-20
My Toshiba laptop came with a recovery DVD - if all else fails, you could use one to restore your machine to an "out of the box" state.  If you get stuck, feel free to ask questions.

---

### Post by upchucky on 2008-07-20
if this was in storage a long time the cmos battery is dead it lost the memory for the bios and went stoopit, need to set up bios and if it works then need new cmos battery.

google u pc to find out how to get into bios on boot, set parameters and try it. if it works and you have to do it everytime you turn off the machine then get a cmos battery.

---

### Post by Wazoot on 2008-07-20
ha
i never thought of a dead cmos battery.

---

### Post by mendo on 2008-07-20
thanks for replies.

the recovery cd that came with the computer won't work.  i get the same message every time.

i have checked the bios.  i don't doubt the battery could be going soon, but it's holding the settings for now.  set cd as first boot option, but no go.

are we in agreement that this isn't an ubuntu specific problem?  i think this is a more basic computer setup issue at this time.

---

### Post by mendo on 2008-07-21
ok - abort!!

for years, ever since i put a new cd-rom drive in that toshiba, i would get an error before windows loaded that said "ide #1 error".  i never gave it much attention b/c the drive worked when windows was loaded.  i just spent a while researching that error msg and it seems that the drive i put in the computer is probably flashed for the wrong master/slave setting for what the mainboard is expecting to see.  google ide #1 error and you'll get lots of info.

i feel confident that the problem here is that my cd-rom drive is jacked up and i can't boot from cd.  thanks for your help and maybe next time i post something it will be fixable by you very gracious ubuntu experts.  thanks.

i'll try to remember to post a "hooray it works now" post.

---

### Post by Wazoot on 2008-07-21
ha glad to hear you found somethin out man

---

### Post by mendo on 2008-07-25
just in case anyone should come accross this in the future:  i used this link with the great photos to solder pins 45 & 47 on my laptop optical drive to fix the 'ide #1 error' problem:


[URL="http://www.packardbellweb.co.uk/hdd/installguide/50-pin%20ATAPI%20interface%20connector%20for%20laptop%20and%20slimeline%20cd.htm"]
enjoy and good luck![/URL]

---

