---
title: "Dualboot Vista and Ubuntu 7.04?"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Martinbr on 2007-05-01
I have Vista on my laptop, and i would very much like to have Ubuntu too.

I have made 20 giga of unallocated space on my HD.

Can i just boot from the Ubuntu cd - choose install - choose guided "the largest free space"?

And will that work so that grub can see Vista too?

I hope it's that easy, but im afraid its not.

Hope to hear from some of you Ubuntu gurus.

Cheers
Martin

---

### Post by Belyel on 2007-05-01
Basically, yes, it should be that easy.  Some complications can arise if you are using a SATA hard drive or if you have RAID enabled.  However, if you can boot using the ubuntu live CD and your hard drive shows up fine for partitioning, you should be good to go.  Just make sure you have the correct partition selected for formatting. GRUB should set up the boot loader correctly.  It did for my vista/xp/ubuntu machine.  Good luck and welcome to Linux.

---

### Post by Martinbr on 2007-05-01
Thanks :) 

When u say 'the correct partition', can i go wrong if i choose the "guided - use the largest free space" (or what it's called) option?

Or should i use another install option?

Cheers
Martin

---

### Post by Belyel on 2007-05-01
Just make sure the partition it is trying to use is the one you set up, ie the 20GB partition.  If you didn't format the partition and left it as 'free space' on the drive, there should be no problems.

---

### Post by lbyrd33 on 2007-05-01
Ive done pretty much the same thing you are doing with unformatted free space and it worked fine. The installation also already configures the grub boot loader to give dual boot options.

---

### Post by Everywhere_at_Once on 2007-05-02
I, myself would take the manual route to create your own partitions, and create a seperate /home partition at the same time.
It's really more easy than it sounds, and gives you more control over how your machine is set up.

Im no linux master so take my advice with a grain of salt, although it has worked for me dual booting XPro and edgy.

If all else fails there are countless HOW-TO articles on this very topic, only a few keystrokes away on google.

Good luck on your journey to LINUX-MASTER-DOM
just remember to drop bits of cookie along the way so i can follow you there!
(mmm cookie)

---

### Post by Martinbr on 2007-05-02
Hi guys,

Thanks alot for the help. It worked like a charm :

---

