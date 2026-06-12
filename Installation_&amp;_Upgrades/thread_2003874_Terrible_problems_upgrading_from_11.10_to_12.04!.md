---
title: "Terrible problems upgrading from 11.10 to 12.04!"
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by heynnema on 2012-06-14
Well, as a long time Ubuntu user, I'm stumped with trying to upgrade my Sony laptop from a solid 11.10 64-bit installation, to 12.04 64-bit. It's blown up THREE times already! I hope you can come up with some/any suggestions for me.

First try, I made sure that all of my 11.10 updates were current, then I clicked on the UPGRADE button in Update Manager. Mistake. I ended up with a totally fried system. With past upgrades, if there were upgrade problems, I could usually fix them. Not this one! I restored my OS from my backup.

I did some research, and there are mentions about needing to update APT and DPKG... but mine look like the correct versions required.

Then I tried booting to the Alternate CD, and hoped that it would ask me about doing an upgrade install. It didn't. I selected use the same partition that Ubuntu was currenly on, and it installed a minimal 12.04 system! All my apps were gone. The dock only had 3 icons. A mess. I restored again.

More research. I found mentions of disabling multiarch, and went to try again! This time I booted into my normal 11.10, inserted the alt CD, and approved the desire to upgrade. It wants to remove over 500 of my applications/etc! Stuff that I want/need. I aborted.

Help, please!!!

Al
:(

---

### Post by itpro007ca on 2012-06-14
You too,eh?

I had a usable 11.10 system,then I hit the upgrade button!

After it came back up,it hung and gave me a nice blank default screen(you know,the Unity coloured one?),but that's all.

Here's what I did.

First,after getting the menu,I clickede 'previous Linux versions' then booted into one of those.Then,I did a recovery mode and a dpkg repair.

This,FINALLY got me into 12.04 Gnome Classic.Then I made the mistake of trying to change to Unity....tried to switch back,but my menubar kept disappearing....anyway,to make a LONG story short...I have 'Gnome Classic(no effects)....so I'll live with that...for now.

In any event,'the experts' on here,might suggest something different,but that's what I did.In any event,It looks like I have Gnome Shell problems,so I'll see what is suggested to me.,also.

The last thing I want to have to do is download an ISO,burn a CD and do a complete new 12.04 install,but it may come to that,yet!

I hope you get it all back up!

---

### Post by firekage on 2012-06-15
> **itpro007ca said:**
> .Then,I did a recovery mode and a dpkg repair.


Can you tell me how to do a dpkg repair? 

Thank you.

---

### Post by itpro007ca on 2012-06-16
Don't quote me on this! :->

But....If I am recalling rightly.....

After you boot into the Grub Menu,you choose 'Ubuntu....Recovery Mode" ,after which there should be an option "dkpg repair."

*NOTE: If using Nvidia(ie: Gefor100 n405,like me|) that only 'gnome classic(no effects)' and 'Unity 2D' will work.Many having this 'no 3D Nvidia' problem.

---

### Post by heynnema on 2012-06-16
That's how I did the dpkg repairs...

still... it's hard to believe that there haven't been more responses to my thread... with suggestions on how to complete the upgrade... :-(

---

### Post by sky5564 on 2012-06-16
Why not just burn a ubuntu 12.04 install disc and erase the old install from the install screen.

---

### Post by heynnema on 2012-06-16
I've tried using both the Live CD and the alt CD. I don't want to erase the old 11.10 install, because I'll lose all of my apps and modified .conf files. I shouldn't have to start building the system from scratch all over again.

Al

---

