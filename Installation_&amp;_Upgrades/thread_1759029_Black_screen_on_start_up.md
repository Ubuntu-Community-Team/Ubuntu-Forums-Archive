---
title: "Black screen on start up"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by armendvisoka on 2011-05-15
Hi,

So I got Ubuntu installed alongside my Windows, but now when I start I get a message on my monitor saying about input not being support or something; usually happens if the resolution isn't supported. If I hit random buttons eventually Ubuntu will start up, but I don't want to be doing that every time :P I remember when I had an older version of Ubuntu a screen would appear where I could pick to start either Ubuntu or Windows, so I assume that's what's going wrong.

Any ideas? Thanks!

---

### Post by sikander3786 on 2011-05-15
I guess using the 'nomodeset' boot parameter would help. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

It was written for Maverick/Lucid but also works for Natty.

---

### Post by Rubi1200 on 2011-05-15
Is this a Wubi install?

Which version?

---

### Post by MAFoElffen on 2011-05-15
> **armendvisoka said:**
> Hi,

So I got Ubuntu installed alongside my Windows, but now when I start I get a message on my monitor saying about input not being support or something; usually happens if the resolution isn't supported. If I hit random buttons eventually Ubuntu will start up, but I don't want to be doing that every time :P I remember when I had an older version of Ubuntu a screen would appear where I could pick to start either Ubuntu or Windows, so I assume that's what's going wrong.

Any ideas? Thanks!
Please follow the Trouble Shooting Flowchart in post 1 of this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by armendvisoka on 2011-05-15
> **Rubi1200 said:**
> Is this a Wubi install?

Which version?

11.04, and I installed it from the CD from Windows, so yes it's Wubi :)

---

### Post by armendvisoka on 2011-05-15
> **MAFoElffen said:**
> Please follow the Trouble Shooting Flowchart in post 1 of this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I got onto this part: comment out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00. and rerun grub-update (from a LiveCD)

I'm not sure what it's telling me to do here, could you help?

Thanks!

---

### Post by MAFoElffen on 2011-05-15
> **armendvisoka said:**
> I got onto this part: comment out /etc/default/grub/ GRUB_HIDDEN_TIMEOUT=00. and rerun grub-update (from a LiveCD)

I'm not sure what it's telling me to do here, could you help?

Thanks!
Some people and their pc's have trouble getting to a grub menu.  If Ubuntu is the "only" OS on your PC, then Grub tries to skip over it's menu.  Pressing the shift key a few times, is supposed to bring it up when this is happening, but sometimes doesn't.

If it doesn't > Boot on a LiveCD, mount your drive (instructions in post 3 of my sticky), edit the /etc/default/grub file and add a "#" character before that line.  While mounted to your drive and sys, rerun the update-grub to pick up that change... That sometime works to get to a grub menu, when other ways fail.  If this still doesn't help, then there might be a problem with grub and it might have to be reinstalled.  There is a rare current GNU Bug that is doesn't display at all, which is usually corrected by a reinstall).l

The info that hasn't been seen here yet in this thread is:
1. What is your pc make and model (would tell people it's specs.)
2. What is your video card and monitor (would give people an idea of what modeset you might need to use).
3. Just where is your PC locking up and what is it doing or not doing? (This will tell people what piece is going south.)

See-- You said you ran it successfully in "Virtual"... but virtual uses a standard boxed hardware platform for it's virtual machine... usually something with a cpu and video combination that is supported by the world.  This all changes when you start installing natively to specific hardware combinations in the real world.   Running natively from a LiveCD is a closer match to running natively after an install. 

I do a lot of dev build, alpha and beta testing.  People scoff at me for dedicating boxes for those tests // but real hardware does bring up different issues than things in virtual... Things that real users actually experience on their real hardware.

Hopefully supplying the info above will direct us in helping you and resolving the problems you are experiencing in a timely manner. If you can supply that here, we could save you some time and reading...

---

### Post by armendvisoka on 2011-05-15
> **MAFoElffen said:**
> Some people and their pc's have trouble getting to a grub menu.  If Ubuntu is the "only" OS on your PC, then Grub tries to skip over it's menu.  Pressing the shift key a few times, is supposed to bring it up when this is happening, but sometimes doesn't.

If it doesn't > Boot on a LiveCD, mount your drive (instructions in post 3 of my sticky), edit the /etc/default/grub file and add a "#" character before that line.  While mounted to your drive and sys, rerun the update-grub to pick up that change... That sometime works to get to a grub menu, when other ways fail.  If this still doesn't help, then there might be a problem with grub and it might have to be reinstalled.  There is a rare current GNU Bug that is doesn't display at all, which is usually corrected by a reinstall).l

The info that hasn't been seen here yet in this thread is:
1. What is your pc make and model (would tell people it's specs.)
2. What is your video card and monitor (would give people an idea of what modeset you might need to use).
3. Just where is your PC locking up and what is it doing or not doing? (This will tell people what piece is going south.)

See-- You said you ran it successfully in "Virtual"... but virtual uses a standard boxed hardware platform for it's virtual machine... usually something with a cpu and video combination that is supported by the world.  This all changes when you start installing natively to specific hardware combinations in the real world.   Running natively from a LiveCD is a closer match to running natively after an install. 

I do a lot of dev build, alpha and beta testing.  People scoff at me for dedicating boxes for those tests // but real hardware does bring up different issues than things in virtual... Things that real users actually experience on their real hardware.

Hopefully supplying the info above will direct us in helping you and resolving the problems you are experiencing in a timely manner. If you can supply that here, we could save you some time and reading...

Using shift hasn't done anything. I'm looking at the post and I'm not sure how to get to editing that file from that menu after pressing escape?


My computer is a Compaq Presario SR2019UK. Specs are AMD Athlon 64 2.2Ghz processor, 2GB RAM and a GeForce 7600 GS 256 MB. My monitor is an AOC LCD L19WH monitor.

It's locking up after the two start up screens where Compaq appears, then there's another where I have to hit F2 to continue, after that one the screen just goes black and I get something like 'input not supported' or the like.

---

### Post by MAFoElffen on 2011-05-15
> **armendvisoka said:**
> Using shift hasn't done anything. I'm looking at the post and I'm not sure how to get to editing that file from that menu after pressing escape?


My computer is a Compaq Presario SR2019UK. Specs are AMD Athlon 64 2.2Ghz processor, 2GB RAM and a GeForce 7600 GS 256 MB. My monitor is an AOC LCD L19WH monitor.

It's locking up after the two start up screens where Compaq appears, then there's another where I have to hit F2 to continue, after that one the screen just goes black and I get something like 'input not supported' or the like.
Along side windows?  Like with wubi or?  I'm sharp on multi-boots and graphics in Ubuntu itself... but (honestly) Wubi is a little fuzzy to me.

Now at least we know your hardware. It sounds like from what you've said, that to go any further that You used to get a grub menu, but now you can't.... and that would we asked you to do, still can't.  Sounds like to go on that you might need to reinstall grub.  

Once you can get that going... themn you can use the grub menu, edit to add a "nomodeset" to the kernel boot line, to start the kernel and be able to find and install your nvidia graphics drivers.

A test would be to go to post 3 of my sticky and follow the instructions with a LiveCD to start it in a "nomodeset."

---

### Post by armendvisoka on 2011-05-15
> **MAFoElffen said:**
> Along side windows?  Like with wubi or?  I'm sharp on multi-boots and graphics in Ubuntu itself... but (honestly) Wubi is a little fuzzy to me.

Now at least we know your hardware. It sounds like from what you've said, that to go any further that You used to get a grub menu, but now you can't.... and that would we asked you to do, still can't.  Sounds like to go on that you might need to reinstall grub.  

Once you can get that going... themn you can use the grub menu, edit to add a "nomodeset" to the kernel boot line, to start the kernel and be able to find and install your nvidia graphics drivers.

A test would be to go to post 3 of my sticky and follow the instructions with a LiveCD to start it in a "nomodeset."

I'm sorry, this is all pretty confusing hhaha... So what should I be doing now exactly? But yes I installed it alongside windows.

---

### Post by MAFoElffen on 2011-05-15
> **armendvisoka said:**
> I'm sorry, this is all pretty confusing hhaha... So what should I be doing now exactly? But yes I installed it alongside windows.
If you used a 11.04 LiveCD and followed the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)
Can you boot into a graphical desktop from the LiveCD?

If so or not, I'll tell you what to do from there.

---

### Post by armendvisoka on 2011-05-16
> **MAFoElffen said:**
> If you used a 11.04 LiveCD and followed the instructions in this post:
[http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)
Can you boot into a graphical desktop from the LiveCD?

If so or not, I'll tell you what to do from there.

Escape is doing nothing at that screen. What now?

Thanks!

---

### Post by armendvisoka on 2011-05-16
bump

---

### Post by MAFoElffen on 2011-05-16
> **armendvisoka said:**
> bump
Reviewing the thread from start to finish-- 

(Tell me if I'm wrong here anywhere)
It looks like you have no Grub menu or access to the grub menu no matter what you do or try.  Right?  It should listen for the shift key but is not...

If not, sounds like grub "is not" loaded and configured correctly and you need to reinstaal grub:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by armendvisoka on 2011-05-16
> **MAFoElffen said:**
> Reviewing the thread from start to finish-- 

(Tell me if I'm wrong here anywhere)
It looks like you have no Grub menu or access to the grub menu no matter what you do or try.  Right?  It should listen for the shift key but is not...

If not, sounds like grub "is not" loaded and configured correctly and you need to reinstaal grub:
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

  I'm looking at the options and the instructions and they aren't really made clear on what I'm supposed to be doing; which one should I be doing? Thanks!

---

### Post by MAFoElffen on 2011-05-17
> **armendvisoka said:**
> I'm looking at the options and the instructions and they aren't really made clear on what I'm supposed to be doing; which one should I be doing? Thanks!I just tested this again on another of my boxes with a current LiveCD.

When you are booting from a LiveCD... the first screen may look like purple or black hue with a "keyboard and human" icon at  the bottom of the scree...

As soon as you see that > Press <ecs>

A drab menu asking you for a language choice will come up > Press <esc>

A text styled Menu will remain, saying "ubuntu" Try, Install, etc... with the F key options at the bottom....

That is the screen where you should see familiarity with post 3 and be able to try the diffrent boot up options in the instructions.

---

### Post by armendvisoka on 2011-05-17
> **MAFoElffen said:**
> I just tested this again on another of my boxes with a current LiveCD.

When you are booting from a LiveCD... the first screen may look like purple or black hue with a "keyboard and human" icon at  the bottom of the scree...

As soon as you see that > Press <ecs>

A drab menu asking you for a language choice will come up > Press <esc>

A text styled Menu will remain, saying "ubuntu" Try, Install, etc... with the F key options at the bottom....

That is the screen where you should see familiarity with post 3 and be able to try the diffrent boot up options in the instructions.

The first option isn't working with 'nomodeset', I'm not sure if what I'm doing is right though. After I do the nomodeset thing, do I just restart my computer or start it up using LiveCD? I started it up with LiveCD earlier, restarted without and I still get no GRUB.

Is there a way I can just uninstall Ubuntu and get back to Windows without being in Windows, or start up Windows without the GRUB? I really like Ubuntu but I need to get something done in Windows, and this is such a big hassle. If not though it's fine and I'll continue on with getting this fixed.

---

### Post by MAFoElffen on 2011-05-17
> **armendvisoka said:**
> The first option isn't working with 'nomodeset', I'm not sure if what I'm doing is right though. After I do the nomodeset thing, do I just restart my computer or start it up using LiveCD? I started it up with LiveCD earlier, restarted without and I still get no GRUB.Ah... 
At the point where you hit <F6> and you arrow down to the nomodeset option, you then would select it by hitting the <shift> or ,enter> key... If you then hit the <esc> key, it will het you back to the main menu, where you would "Try"... If you "Reboot" your computer, then it would forget those settings and you're really not accomplishing anything.

> **armendvisoka said:**
> Is there a way I can just uninstall Ubuntu and get back to Windows without being in Windows, or start up Windows without the GRUB? I really like Ubuntu but I need to get something done in Windows, and this is such a big hassle. If not though it's fine and I'll continue on with getting this fixed.
If you started up on a Windows Install disk, you could reinstall the Windows MBR, which would over-write grub and you would have Ubuntu there but not functional.... 

My experience is with graphics and multi-boots.  I'm not real familiar with removing a wubi install of Ubuntu <> all my installs are multi-boot and more isolated from each other.  I guess someday I should really play with that and see what kind of adventures I can get myself into with that.

---

### Post by armendvisoka on 2011-05-17
> **MAFoElffen said:**
> Ah... 
At the point where you hit <F6> and you arrow down to the nomodeset option, you then would select it by hitting the <shift> or ,enter> key... If you then hit the <esc> key, it will het you back to the main menu, where you would "Try"... If you "Reboot" your computer, then it would forget those settings and you're really not accomplishing anything.


If you started up on a Windows Install disk, you could reinstall the Windows MBR, which would over-write grub and you would have Ubuntu there but not functional.... 

My experience is with graphics and multi-boots.  I'm not real familiar with removing a wubi install of Ubuntu <> all my installs are multi-boot and more isolated from each other.  I guess someday I should really play with that and see what kind of adventures I can get myself into with that.


Yep, I did click "try" and it still isn't working. I found a program called start-up manager which has allowed me to get back into Windows though :D

---

