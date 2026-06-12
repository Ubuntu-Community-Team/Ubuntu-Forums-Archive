---
title: "Epidemic of Grub2 &quot;Error 15&quot; failures?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by yonkiman on 2009-10-26
I've tried 3 clean installs of 9.10RC and I keep getting Error 15. Karmic Koala seems great from what I've heard, but if you google:
"error 15" karmic OR "9.10"
there seems to be an epidemic (5000 links) of Error 15s - and 9.10 hasn't even been released yet. I'm a little concerned that once the masses start playing with it, this is going to sour a lot of people. Is it too late to do something about this?

I'm sure I can hack around and fix it, but it doesn't give a great first impression - previous releases worked on my hardware with no drama!

-Fred

---

### Post by cariboo on 2009-10-26
IF you consider how many people have Karmic installed, 5000 links on Google,is not a very big number. Have a look [here]("https://wiki.ubuntu.com/Grub2"), to solve your grub2 problems.

---

### Post by yonkiman on 2009-10-26
> **cariboo907 said:**
> IF you consider how many people have Karmic installed, 5000 links on Google,is not a very big number. Have a look [here]("https://wiki.ubuntu.com/Grub2"), to solve your grub2 problems.

The solution seems to be to run "update-grub".  That's a challenge for me because I can't boot into the newly installed OS because of the grub problem.  I booted from the CD and tried "boot first OS on harddisk" (or whatever it's called), but I get the same grub error 15.  I'm using the alternate install disk (because the desktop one won't boot at all), and it doesn't have an option to "try linux".  So now I need to find a bootable disk that has grub2 "update-grub" support and figure out how to make it point to my 9.10 install.

Like I said, I know *I* can eventually figure it out, but I don't think Joe Blow User who's decided to finally give linux a try is going to be very impressed when all he gets for his 10-30 minute investment is "Error 15" - so I hope you're right that 5000 or whatever is an insignificant number.  

I don't want to sound like I'm complaining about the effort that's gone into this project - quite the opposite.  I know how hard people have worked precisely to make this an easy-to-install and use OS, so I'd hate to see a significant fraction of new users have a bad experience, particularly if something can be done before the final release - like adding a menu item on the boot cd to run "update-grub" (though I know it's probably too late).

---

### Post by VMC on 2009-10-26
If you follow the link that cariboo907 gave down to section "Recover Grub 2 via LiveCD", it will explain how to recover grub2.

---

### Post by yonkiman on 2009-10-27
I appreciate all the help on getting my installation to work (one of the reasons I love the ubuntu community), even though my goal was to raise people's consciousness that "Error 15" might be a bigger issue than people think.  

In any case, my system's working great, so thanks again.

---

