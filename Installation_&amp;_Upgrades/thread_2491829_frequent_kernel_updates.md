---
title: "frequent kernel updates?"
date: 2023-10-22
forum: Installation &amp; Upgrades
---

### Post by dmueller87 on 2023-10-22
Hello there,
I'm running Ubuntu Server 22.04.3 - with enabled unattended Upgrades. I noticed that there are frequent Kernel Updates almost every 14-15 days. I'm just curious, is there a way to make this less frequent without sacrificing security that much? 
Best Daniel

---

### Post by ian-weisser on 2023-10-22
Risk: By going off-track, you are taking on some risk, and it's up to you to determine what risks you will accept and how you will manage them.

There are a couple ways to ignore newer kernels.

First, you can simply not reboot into the newer kernel. Just keep running.
The system will complain at login that a newer kernel is available...but it's just a notification. Not an error. Not a warning. Nothing is broken.

Second, when you reboot, you can choose the older (working) kernel at GRUB.

Third involves mucking with packages:

Kernel updates are governed by the kernel metapackage, Ubuntu Server 22.04's default metapackage is "linux-image-generic", which keeps 22.04 on the 5.19 kernel. Some users opt to use the "linux-generic-hwe-22.04" metapackage, which currently pushes 22.04 to the 6.2 kernel.

Cease frequent kernel updates using the following. Resume kernel updates before future release-upgrades, or those upgrades will fail.

```

sudo apt-mark hold <metapackage_name>          // Cease kernel updates
sudo apt-mark unhold <metapackage_name>        // Resume kernel updates

```

---

### Post by dmueller87 on 2023-10-22
Thx. Helped a lot.

---

### Post by MAFoElffen on 2023-10-22
What he warned about was... Not doing kernel updates puts you at risk of some things. Kernel updates correct bugs, and security vulnerabilities. Also, along with kernel updates, is the update on the system package  'linux-base', which is the Linux system's core toolset used with that  range of kernels, paralleled in the tree. Some things may potentially  break if they are not kept in-sync.

What he didn't mention was: Like me... For my servers, I disable un-attended updates. I do mine manually.

The reason I (personally) am not a fan of that is that I want direct control of what is updated and not. That comes from years of Systems Administration... Where some places I worked, we had to test proposed updates before they were applied to a production system. That way we didn't end up having to roll back a production system from prospective problems. I don't like unexpected surprises.

Not to say that there is usually any problems with updates, but... 

Things do happen. Even with Desktops... Some updates of some packages will remove things you might require or want to keep.

I have 'live-patch' updates turned on. It took me a while before I signed off on that for my systems. I am still holding off on 'realtime kernel' updates until I finish what that means for my own systems and how I allow things to happen...

---

### Post by dmueller87 on 2023-10-23
That's a very good point. It's for a small home server, also doing basic network stuff like DHCP, DNS, NAS. So I guess for my use case I'll be better of to move unattended-upgrades into early morning and hope for the best. If something happens I'll have to deal with it in the morning. But my bet is, it'll work out just fine most times. So I save time. If things break to often, I'll revert to applying the updates manually.

---

### Post by ian-weisser on 2023-10-23
Risk management: I keep network-critical tasks (dhcp) on separate hardware.
The crash of a complex optional service, or the unexpected death of a hard drive, shouldn't take down the whole network.

I will need network access to look up how to restore the complex service!

---

### Post by TheFu on 2023-10-23
If you want fewer updates, use older kernels, that had their main series of security problems already solved.  20.04 would be good for that, but realistically, a security update every 2 weeks isn't a bad thing. It is a good thing.

If you want to control when updates happen, do them manually. Once you've been burned by auto-update, you may never enable it again.  I was burned around 2012 and stopped then.  1 time was enough.  I've been patching, manually, every week, on Saturdays, since then. I do pay attention to huge security issues related to my most at-risk systems and twice since 2012, I've applied specific patches mid-week.  All the other stuff could wait until the weekend.

It isn't like autopatching saves time.  I have bonehead script that does my patching. It loops over a list of system names, ssh'es into each, runs 2 commands and moves onto the next system.  All this is logged for my review.  I tend to run the script then go take a shower and when I'm done, they are all patched.  A quick review for errors/warnings in the log file and a cursory view of it using **less** and I've seen what was updated and if there were serious issues.  System Admins spend a bunch of time reviewing log files.  I also use logwatch daily to do the same high-level review on all my systems and email the results.  Usually takes about 10 seconds per system to review those summaries. Now, if something odd happened, I'll need to spend a few minutes checking it out.  Most commonly, it will be some new attacks against a public-facing webapp.  I'll tweak my fail2ban regex to block and ban the new attacker, then move on with my day.  Getting incrementally better. Plus my fail2ban work is shared to all my webapps, to it isn't just 1 being protected.  

If you want a little extra protection against bad updates, use your storage volume manager and create a snapshot before the update.

Same happens for email spammers. Just last week a new TLD started spamming, so rather than try to be too specific, I just added a block to it.  After all, who would I or anyone want to email them from .yum domain?  Right up there with .buzz.  All those new domains that Google pushed to be allowed have become homes to spammers.  I feel bad that some other domains got caught too, but not THAT bad.  Accepting email is for our needs, not those of spammers.

---

