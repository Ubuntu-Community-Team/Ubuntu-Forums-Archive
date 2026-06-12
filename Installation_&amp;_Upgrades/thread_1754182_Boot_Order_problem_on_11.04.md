---
title: "Boot Order problem on 11.04"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by kevb8ll on 2011-05-09
I've just upgraded to 11.04, no problem with that - however it doesn't pick up the preference in startup manager to have XP default boot OS. (The PC is shared with the kids).

I have tried uninstalling and re-installing startup manager. I have searched through and found a couple of threads, but the file edit suggestions don't seem to match up with 11.04.

Anyone help?

Thanks

Kev

---

### Post by wilee-nilee on 2011-05-09
> **kevb8ll said:**
> I've just upgraded to 11.04, no problem with that - however it doesn't pick up the preference in startup manager to have XP default boot OS. (The PC is shared with the kids).

I have tried uninstalling and re-installing startup manager. I have searched through and found a couple of threads, but the file edit suggestions don't seem to match up with 11.04.

Anyone help?

Thanks
Kev
Startup manager has not caught up with natties grub. Your loking for the grub customizer to do this I believe look in the thread.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by chris.dangerfield on 2011-05-09
Hi there,

I am a recent Ubuntu convert - and am having the same problem. I was using Grub 2 (don't know if this was Natty Grub 2) under 10.10 and upgraded - now the startup manager only loads the default - which in mycase doesn't work, because it needs a modified "boot delay" option. Any ideas of how to set the preference in grub.d or modify the startup manager to get it working are most appreciated!

Thanks,

Chris

---

### Post by wilee-nilee on 2011-05-09
> **chris.dangerfield said:**
> Hi there,

I am a recent Ubuntu convert - and am having the same problem. I was using Grub 2 (don't know if this was Natty Grub 2) under 10.10 and upgraded - now the startup manager only loads the default - which in mycase doesn't work, because it needs a modified "boot delay" option. Any ideas of how to set the preference in grub.d or modify the startup manager to get it working are most appreciated!

Thanks,

Chris

Read my post and if you have a problem beyond that the forum protocol generally is to have single threads per user. Being in this thread will not speed up any responses. You also have a bit of a different problem, only the same application.

Pm me if needed, if you start a new thread.;)

---

### Post by kevb8ll on 2011-05-10
Hi wilee-nilee which part of that thread applies to me?

I'm getting frustrated because I have now spent a lot longer that I wanted to trying to sort this.

At the end of the day I just want XP to be the primary boot OS for the kids. Which ever is the EASIEST solution will do me.

(Not having a go at you - I'm just very frustrated at getting this from the update).

Kev

---

### Post by wilee-nilee on 2011-05-10
> **kevb8ll said:**
> Hi wilee-nilee which part of that thread applies to me?

I'm getting frustrated because I have now spent a lot longer that I wanted to trying to sort this.

At the end of the day I just want XP to be the primary boot OS for the kids. Which ever is the EASIEST solution will do me.

(Not having a go at you - I'm just very frustrated at getting this from the update).

Kev

So not knowing what your set up is, and not really ever doing this myself, this link should get you going.
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

I don't think the startup manager works in Natty yet.

Can you get into the Ubuntu install, to do this stuff?

If you start a thread with a appropriate header like dual boot set grub menu default, and post the script in my signature called the bootscript, in code tags, you will have a lot more help.

I tried to point you this way already, if you look at my account you will see I'm not a new person here, I know the drill, I'm just sharing it with you. If I new the perfect fix I would have given to you, I hope this make sense.

---

