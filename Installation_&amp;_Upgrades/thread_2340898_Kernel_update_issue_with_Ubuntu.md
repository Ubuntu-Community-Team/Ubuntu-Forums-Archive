---
title: "Kernel update issue with Ubuntu"
date: 2016-10-23
forum: Installation &amp; Upgrades
---

### Post by 23senick on 2016-10-23
Hi,  I've just completed a mammoth session updating kernels on my ubuntu machines to make sure I had kernels patched for Dirty Cow - and it wasn't straightforward. I thought I'd sorted it as I got the reassuring "software on this computer is up to date" message from software updater. That was until I ran ```
uname -a
``` which showed a couple of them were stuck on old kernels (eg 14.04 using 3.13.0-36, when it needed to be on 3.13.0-36). Despite multiple attempts to run update-grub, they would not boot into the new kernel.  Worse still, on running software updater it kept saying "the software on this computer is up to date" even though I couldn't boot into a kernel that was anything like current.  


I am sure someone will say "you should delete kernels" but my challenge is  - howcome ubuntu/linux (which I love!) has allowed this issue to go unnoticed?  I pay great attention to updates, and am a reasonably competent amateur.  Normally I delete old kernels as I go along but guess I missed a few, though now I start to wonder how I could have missed so many in Synaptic. There must be thousands of laptops/PCs that unbeknown to their users have old kernels (with Dirty Cow and perhaps other vulnerabilities). Will this issue be addressed? Surely it can't be impossible to build in a check that alerts users if they are booting into an old kernel?


Apologies if there's an existing thread - I searched but can't see one.

---

### Post by Bucky Ball on 2016-10-23
Try this.

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot. 'uname -a'. What ya got? 

The commands above _will not_ upgrade your release to a newer version, just all software in it, including kernels.

PS: For your benefit, I suggest you change your thread title because Dirty Cow has nothing to do with what you are asking for support with and is the stuff of another thread. Edit first post and 'Go Advanced'. 'Kernel update issue with Ubuntu'. Most people have no idea about Dirty Cow. Chat area for that please. :)

---

### Post by howefield on 2016-10-23
Are the machines that appear to be running the "wrong" kernel multi booting, in which case the controlling grub would need to be updated which is not necessarily the one with the updated kernel. Sorry for stating the obvious but it can happen.

---

### Post by kostkon on 2016-10-23
Nothing has gone amiss; I guess you are unaware of [HWE]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2FSupport.A14.04.x_Ubuntu_Kernel_Support") and how it works. It is normal for 14.04.0 installations to still be on 3.13 (which is still supported and thus already received the dirty cow patch.)

Hope that helps.

---

### Post by 23senick on 2016-10-27
Apologies been away and thought my post hadn't uploaded as the forum went down as I uploaded. Thanks for the responses - I can't comment authoritatively on whether they would have helped as I successfully uploaded the new kernels in the end, so Bucky Ball may be right.  Howefield - one machine may fit into this category but not all of them.  Kostkon - I think you missed my point.  Of course 14.04 is on 3.13 - but one of my machines was stuck on 3.13.0-36, and I needed it to be on 3.13.0-100, so it was still vulnerable, and what's more, clearly hadn't updated the kernel for weeks/months, despite the fact that I check for and install updates most days, run update-grub etc.  

I think my question is unanswered, and I'd love a good answer as it has rather shaken my confidence in Ubuntu/Linux, which I love and want to work!  
**Why was Ubuntu not only leaving me vulnerable to security issues by not updating to the latest kernel, but giving false reassurance that my software was up to date?  **

---

### Post by oldos2er on 2016-10-28
Thread moved to *Installation & Ugrades*.

---

### Post by ian-weisser on 2016-10-29
> **23senick said:**
> I think you missed my point.  Of course 14.04 is on 3.13 - but one of my machines was stuck on 3.13.0-36, and I needed it to be on 3.13.0-100, so it was still vulnerable, and what's more, clearly hadn't updated the kernel for weeks/months, despite the fact that I check for and install updates most days, run update-grub etc.

Kostkon's answer was very good...for the information we had at the time. Be kind.


> **23senick said:**
> Why was Ubuntu not only leaving me vulnerable to security issues by not updating to the latest kernel, but giving false reassurance that my software was up to date?

The question is, on one level, FUD. Ubuntu provides *supported, patched* software (including Kernel) in an LTS, not the *latest* software. Purge that 'latest' idea from your mind when you choose to use LTS. For 'latest', use a newer release of Ubuntu.

On another level, you have identified one real support problem - a 14.04 system on the correct kernel path that failed to upgrade from the -36 kernel.
That we can indeed try to help you with.
Are you asking for help trying to diagnose and resolve this issue?

---

### Post by 23senick on 2016-10-30
Hi again, and if I didn't appear kind, my apologies, I appreciated the responses.  I've used and loved Ubuntu for years, so was trying to work out why a couple of machines got stuck on vulnerable kernels.  I have now got all machines onto the correct kernel versions after quite a bit of work.  But for the future, my question is why a 14.04 machine got stuck on -36, and whether any other action is needed to prevent it happening again.  I had downloaded and installed the latest patched kernel but for some reason Update-Grub would not locate it.  I guess next kernel patch may show - if the machines in question don't start using it - that there's something about the install that is causing the issue.

I read a post somewhere - and can't find it now, so may not be on this forum - something about having too many kernels affecting GRUB.  I routinely delete older kernels but normally keep a couple.  On one machine I seemed to have missed a few, but not on all of them.  Is there anything more that Ubuntu users should be doing to ensure Kernel updates are applied on LTS versions?  

I respectfully maintain that the software updater's message ("software is up to date" which I was getting despite the kernel issue) is misleading to users if the machine is not using the latest, patched version of the LTS kernel - if others think I'm wrong do please let me know why. By raising this point I hope it's helpful and may help improve Ubuntu in future - I'm raising it from the perspective of someone who loves and uses Ubuntu above MS/Apple products, encourages friends to use it as well, but I'm not from an IT background.

---

### Post by Bucky Ball on 2016-10-30
In 14.04 I always used

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Never had an issue. I have .5 on the laptop from memory.

In 16.04 LTS I use

```
sudo apt update
sudo apt full-upgrade
```

So far, so good. Your issue is very peculiar. :-k

---

### Post by 23senick on 2016-10-30
OK thanks Bucky Ball - I'll keep an eye on next couple of kernel updates and see what happens.  Thinking about it, a couple of my laptops which have - shall we say - less than optimal partition structures. Long story.  Perhaps that was the cause.

---

### Post by ian-weisser on 2016-10-30
> **23senick said:**
> I respectfully maintain that the software updater's message ("software is up to date" which I was getting despite the kernel issue) is misleading to users if the machine is not using the latest, patched version of the LTS kernel 
Fully agree.
That kind of misleading behavior I would consider a bug worth triaging and fixing...if we can figure out out to replicate it.
If we can't replicate the behavior in a test system, we can't fix it.

Are any of the systems still on old kernels?
If so, please show us the full output of:
```
uname -a
dpkg -l | grep linux
```

This is rather like the old accumulating-kernels bug (fixed in 16.04). Lots of users noticed the symptoms of the problem, and talked about it in this forum.
Finally a single sufferer provided enough information for a single community member to duplicate the issue in a test system.
The bug, affecting thousands, was triaged and fixed in 72 hours...once we had enough information to duplicate in a test system.

---

### Post by 23senick on 2016-10-30
Sorry I fixed them all :D

Not exactly sure what I did, deleted old kernels, think I used synaptic to find and install the updated/patched versions I needed.

When I originally posted, the forum went down - or my internet glitched - so I couldn't get back in for a while.  What I'll do is keep an eye on things next time there's a kernel change.

But thanks again

---

