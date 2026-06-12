---
title: "WinXP / Ubuntu Dual Boot Install"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by unsober on 2010-09-21
I have a quick question.

I have WinXP installed, so I want to resize that and make room for Ubuntu.
So I boot up the CD, and choose the bottom option so I can do manual partitioning, not automated.

I resize the Windows partition, set up my ext4 and swap. I go to click "Forward", and a window comes up telling me something like this;
"The NTFS partition has no mount point. If you continue, the partition will be unusable."

I go back to set the mount point for my WinXP partition, and I get these options:
/
/DOS
/WINDOWS


What do I do from here? I tried choosing /, but it said I couldn't have 2 partitions mounted on / at once.
Am I supposed to skip this and have it on no mount point at all, or what?

I want to Dual Boot and have the option to select which OS to boot from when I turn on the PC.

Thanks for any response

---

### Post by unsober on 2010-09-21
bumping this.

my thread got pushed down to the 6th page.

I'm sure it's a fairly easy question. I just need a quick answer.

---

### Post by wilee-nilee on 2010-09-21
> **unsober said:**
> bumping this.

my thread got pushed down to the 6th page.

I'm sure it's a fairly easy question. I just need a quick answer.

I might be a simple fix, but it is MS. A lot of use are familiar with MS but not as much as pro/power user/goldstar...etc on a MS forum. You might try other threads in other forums.

Your asking a lot of free help here, you have borked something that may have resulted in who knows what damage, hopefully not though.

Seek MS help or professional help from MS.

---

### Post by GeekGirl1 on 2010-09-21
I had lots of problems installing a dual-boot Win XP / Ubuntu. My problem was that it didn't recognize a firewire drive. To bypass the problem, I just installed Ubuntu *inside* Win XP with [Wubi](http://wubi-installer.org/). Worked great.

I've since installed a 2nd SATA hard drive and a normal install went fine.

You may have a configuration that the drivers can't handle. [Wubi](http://wubi-installer.org/) will get you going until you can figure it out. Or, just keep Wubi.

---

### Post by unsober on 2010-09-21
@wilee-nilee

I don't understand.
Yes, I do have Windows. But it works perfectly fine. There is no problem with my Windows whatsoever. The problem is during the Ubuntu installation. And this is an Ubuntu support forum. Hence me being here.
I am not going to seek "professional help from Microsoft" for a problem I'm getting during an Ubuntu installation.
That seems a bit silly.

Anyways, I'm thinking in order to leave my WinXP installation alone (and keep it bootable), I'm supposed to give it no mount point. If no one confirms, I'm just going to try it and see what happens.
This warning I'm getting makes me a bit nervous, though
```
"The NTFS partition has no mount point. If you continue, the partition will be unusable."
```

EDIT: thanks GeekGirl1 for the link. although I'd rather have a real Ubuntu partition. So I think I'm just going to guess and see what happens.

---

### Post by wilee-nilee on 2010-09-21
My only message was the limitations of this forum, and that getting outside help alongside would probably get you going. Sorry if it sounded like go away.;) Not my intentions at all, you had no responses, until just shortly ago; but here it is a unusual problem.

I think you just need to check in gparted and see if the ntfs partition is flagged, right click and look at the information. When you resize XP it needs to run a auto chkdsk and Ubuntu is probably seeing this. **Standard procedure** is re-size Windows partitions reboot make sure it works. Reboot into the new install. Is XP Unmounted as well when you run into this problem. The mount and unmount of partitions matter in any operations a lot of times.

I would add as well that wubi is a usable option just be very careful that you get to know the setup, it has some pitfalls although usually dealt with; but may make it a little more difficult to get help with as well. As well as more difficult to fix.

---

