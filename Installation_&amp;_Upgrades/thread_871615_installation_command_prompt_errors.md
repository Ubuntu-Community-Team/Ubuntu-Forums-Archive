---
title: "installation command prompt errors"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by disc_man on 2008-07-27
Hey, I'm eager to try ubuntu, but ive had quite a few problems. I managed to solve the Buffer I/O error, but now what happens is that I get to the first screen (that has options to install, try without changing stuff etc.) select the first option, then the ubuntu logo comes and the bar moves, [I]then[I] it comes to a command prompt. it seems quite a few people get this error. i have tried this:


[COLOR="Red"]At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe ata_piix
modprobe ide_generic
exit

You will now boot into the LiveCD normally.
Above worked successfully and I hope your case is working fine.
[/COLOR]

didn't work. i'm reluctant to try everything in every thread now, because each time i get to the prompt, there is no way out so i have to switch the power from my computer. 

btw, my actual disc is fine.

could anyone help me?

---

### Post by wpshooter on 2008-07-27
Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried to start/install in safe graphics mode ?

If the 2 above don't work then try installing with the ALTERNATE (text based) version of Ubuntu.

---

### Post by disc_man on 2008-07-28
I tried checking the Ubuntu CD like how you said, but it also ended up at the busybox command prompt. Ditto for safe graphics mode. I also tried adding all_generic_ide. I'm thinking of trying the alternate cd now, but that means I can't trial Ubuntu. Just in case I hate it or my computer complains, is uninstalling Ubuntu as easy as deleting the partition in which it resides? (I have Windows XP in my single partition now).

---

