---
title: "Post-GRUB 2 Delay"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by dwitkin on 2011-05-11
I'm hoping a Ubuntu guru can point me in the right direction on how to troubleshoot this.

After GRUB 2 comes up (I'm running Ubuntu 10.10) and I choose the OS to boot, there is about a 5 second delay where nothing appears to happen after I make the selection -- no disk activity.  It happens consistently every time I boot.  Again, this is after I choose the OS to boot, so it shouldn't have anything to do with the standard delay to allow me to choose the appropriate OS.

Is there a good way to troubleshoot this and determine what is causing the delay?

Thanks for your help.

---

### Post by MAFoElffen on 2011-05-11
> **dwitkin said:**
> I'm hoping a Ubuntu guru can point me in the right direction on how to troubleshoot this.

After GRUB 2 comes up (I'm running Ubuntu 10.10) and I choose the OS to boot, there is about a 5 second delay where nothing appears to happen after I make the selection -- no disk activity.  It happens consistently every time I boot.  Again, this is after I choose the OS to boot, so it shouldn't have anything to do with the standard delay to allow me to choose the appropriate OS.

Is there a good way to troubleshoot this and determine what is causing the delay?

Thanks for your help.
Remove " quiet splash " (which suppresses those messages) from the kernel boot line and add " nosplash --verbose " by temporarily editing the grub menu start-up item.

You could also turn on boot logging to a file... which is a little more involved and detailed.

---

### Post by dwitkin on 2011-05-12
Thanks.  I'll give that a try and see what it tell me...

---

### Post by dwitkin on 2011-08-08
MAFoElffen (or another boot-time guru),

Ok... so I removed "quiet splash" and noticed the system appears to hang (i.e., no disk activity) briefly when the following line is shown: running /scripts/local-premount.  I didn't see a "scripts" directory off root... how can I determine what script is causing the delay?

Thanks for your help...


> **MAFoElffen said:**
> Remove " quiet splash " (which suppresses those messages) from the kernel boot line and add " nosplash --verbose " by temporarily editing the grub menu start-up item.

You could also turn on boot logging to a file... which is a little more involved and detailed.

---

### Post by oldfred on 2011-08-08
I am not expert on booting issues, but when I have a problem I look in the log files. You can see what it posts when you remove quet, splash in messages ( I think) with time stamps on what it is doing. If there is repeated entries where it is trying to load and then tries again, or long times between entries those are areas to research further.

System, Administration, Log File Viewer
(Not sure if same in 11.04)

---

