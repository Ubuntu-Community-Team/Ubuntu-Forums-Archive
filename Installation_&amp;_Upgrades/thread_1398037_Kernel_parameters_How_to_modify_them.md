---
title: "Kernel parameters: How to modify them"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-02-04
Greetings.
Bottom line first: Is there a GUI or otherwise friendly tool to modify the kernel parameters?  One that will give help on a highlighted parameters?

Now as to my reason for this question:

In preparing for an Informix installation, I may need to change some kernel parameters.  I could follow the advice of Gérard BIGOT from a couple of years ago at [_[COLOR="Blue"]this URL[/COLOR]_]("https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134978.html").  However, messing with the kernel this way, by directly editing /etc/sysctl.conf, is a bit scary.  I have already backed up the current one and started editing according the Informix machine notes.  However, I have commented out my new settings. [:Chicken]

The scariest aspect of this is that the notes recommend settings to kernel parameters that I do not find in /proc/sys/kernel. for example, it recomments setting SHMMIN to 1 but when I can /proc/sys.kernel/shmmin, there is no such file.  (I did find shmmax.) Similarly for the very logical shmseg (max number of shared memory segments) - not found.  I am afraid to add these into sysctl.conf if the equivalent pseudo-files don't exist.

Additional question: Where [on-line] do I find all kernel parameters documented?  This is so that I am more certain of what I am doing instead of relying on my memory. For example, I don't recall the names of the parameters that control Kernel-Asynchronous I/O (KAIO) events.  Such a doc would be most helpful here.

Thanks much.

---

### Post by tgalati4 on 2010-02-04
What are your performance goals?  Perhaps the default settings will work.  I have found that tweaking has unintended consequences.  The default settings work for a lot of workloads.

---

### Post by efflandt on 2010-02-04
If you did a fresh 9.10 install (or updated to grub2 after 9.04 to 9.10 update) you modify kernel parameters in /etc/default/grub.  The DEFAULT is for regular boot and without DEFAULT is for recovery boot.  In this case I temporarily disabled "quiet splash" while installing a new digital monitor (actually 1080p HDTV), until I had a chance to modify /etc/usplash.conf to proper resolution.

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

After any modifications **sudo update-grub** to update grub.cfg.

---

### Post by rpaskudniak on 2010-02-08
In response to tgalati4:
ON my dinosaur box, I have no great performance goals.  My concern is merely that the kernel resources that Informix requires are available.  For example, I have seen that the default semaphore resources exceed the basic requirements.  But the shared memory  and KAIO resources listed in the machine notes were not found in the pseudo-files fro the kernel parameters.  Hence, I need to find a way to set them so that the Informix engine will find them.  Hence, editing /etc/sysctl.conf is a logical starting point.

This is why I am looking for on-line documentation or some nice package to adjust the parameters graphically.  (I think I'm gonna give up on that last item. :-k  )

As to efflandt: Your comments left me scratching my head for a while, since I could not see the relevance of the grub to this discussion.  However, a google search of ubuntu kernel parameters led me to the [_[COLOR="Blue"]GRUB2 page[/COLOR]_]("https://help.ubuntu.com/community/Grub2"). Still no discussion of actual parameters but I begin to see relevance. But no direct help yet.  And since I updated from 9.04 to 9.10, I am still using the legacy GRUB.  Converting to GRUB2 is rather intimidating, especially since the illustrated examples [in that page] seem to ignore Windows.  (It's mentioned as "other OS" but not with explicit instructions.)

Still, Google is our friend here.  If I find what I'm looking for, I will post it.

Thanks.

---

