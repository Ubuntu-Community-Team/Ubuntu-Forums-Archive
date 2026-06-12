---
title: "Installing 11.04 - manual partitioning issues"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-06-08
I had previously tried to install 11.04 with a partition layout (this is to be a many-multi-boot machine) that included 57 partitions, using a GPT partition table.  The installer hung.  Here is the thread about that: [http://ubuntuforums.org/showthread.php?t=1772299](http://ubuntuforums.org/showthread.php?t=1772299)

So I am following a suggestion to stay with GPT, but limit the visible partitions to only the ones I will need for this install, which are:```

4 = /boot
40 = /
41 = /var
42 = /var/log
43 = /usr
44 = /usr/local
7 = swap
8 = /tmp (not formatted)
9 = /home (not formatted)
```I went with manual partitioning, of course.  But when I go to partition 42, the mount point I need (/var/log) is not in the drop down menu AND it won't let me type in the mount point path directly, either.

So did someone break the type-in entry to this?  How can it be fixed?  It worked OK in 10.10 (just tested it 20 seconds ago).

---

### Post by psusi on 2011-06-08
Why on earth are you using so many partitions?  Why would you want /var/log on its own partition?

---

### Post by srs5694 on 2011-06-08
I noticed that it's impossible to specify mount points that aren't on the list in 11.04, too. I don't know of a way around this in the installer. My only suggestion is to install using the mount points that *are* defined and then redefine them manually by editing /etc/fstab after the installation completes. You may also need to move files from the original partition to the new one -- something that might best be done from an emergency CD.

---

### Post by jramshu on 2011-06-08
I would only set up / and /home.

---

### Post by Skaperen on 2011-06-08
> **srs5694 said:**
> I noticed that it's impossible to specify mount points that aren't on the list in 11.04, too. I don't know of a way around this in the installer. My only suggestion is to install using the mount points that *are* defined and then redefine them manually by editing /etc/fstab after the installation completes. You may also need to move files from the original partition to the new one -- something that might best be done from an emergency CD.
Yeah, that was the workaround ... just leave out /var/log for now and set it up, manually.  But there is definitely a feature regression going on here.  But there has been a lot of "if the average user doesn't do this, then no one should be able to" going on.

Since I already have 3 different Slackware systems install on it, I can do things from them instead of an emergency CD.

FYI, it is set up to allow up to 16 systems to be installed, 6 with production-grade isolated partitions, and 10 with simpler single partition layouts.

---

### Post by Skaperen on 2011-06-08
> **psusi said:**
> Why on earth are you using so many partitions?  Why would you want /var/log on its own partition?
This particular machine is a multi-boot test platform.  Among its purposes is a place to test out new distribution versions in ways that testing in virtual machines just can't do.

So I can have /var/log mounted with sync, without having to mount everything else that way.  It's also a way to keep runaway processes writing to other filesystems from filling up log space.

On classic mail servers with mbox-style mailboxes, which used the last access time to determine for shell users if new mail had arrived, I mounted the mailbox tree with the "atime" option, while other partitions had "noatime".  In many server cases I also mount "/usr" and "/usr/local" in read-only mode.

---

### Post by psusi on 2011-06-08
> **Skaperen said:**
> 
So I can have /var/log mounted with sync, without having to mount everything else that way.  It's also a way to keep runaway processes writing to other filesystems from filling up log space.

Why?  Some of the critical error log files are already written sync by syslog, and for the others, doing so is detrimental to performance.  And how often do you have a runaway process run as root fill up the disk?

> **Skaperen said:**
> On classic mail servers with mbox-style mailboxes, which used the last access time to determine for shell users if new mail had arrived, I mounted the mailbox tree with the "atime" option, while other partitions had "noatime".  In many server cases I also mount "/usr" and "/usr/local" in read-only mode.

It makes sense to have /var/mail/spool on its own partition for a heavy mail server still using mbox ( don't most use Maildir or something else these days? ), but why mount /usr and /usr/local read-only?  And why have /usr and /usr/local on separate partitions ( instead of just all of /usr )?  And can't you use a read only bind mount for that?

---

### Post by Skaperen on 2011-06-09
> **psusi said:**
> Why?  Some of the critical error log files are already written sync by syslog, and for the others, doing so is detrimental to performance.  And how often do you have a runaway process run as root fill up the disk?
It doesn't have to be just root.  Then that only leaves a few percent for root.  Runaways don't happen very often.  But for some odd reason, that seems to happen at around the same time as some kind of problem I need to investigate.
As for the sync issue, sure, sync degrades performance.  But it's not that bad since as you mention, syslog does that.  But that's not the only way logs get written.  Why is sync bad for them if it's not bad for syslog?  Sure, sync is bad for other stuff, which is why I've separated /var/log since before Linux.

> **psusi said:**
> It makes sense to have /var/mail/spool on its own partition for a heavy mail server still using mbox ( don't most use Maildir or something else these days? ), but why mount /usr and /usr/local read-only?  And why have /usr and /usr/local on separate partitions ( instead of just all of /usr )?  And can't you use a read only bind mount for that?
Ever little bit of protection layer is better.  Separating /usr from /usr/local isn't always needed.  But I do so where I expect more frequent updates to /usr/local.  Now days I could bind mount something like /home/usr/local over /usr/local and have it not be read-only for certain machines.  But if there are suid issues (I mount /home with nosuid ... and also /tmp if I choose to have that separate which is rare these days, using /home/tmp instead, possibly with /home/tmp bind mounted as /tmp), I can't do that.

Of course, I do have to work with /etc/fstab often, because installer mount choosers are really not up to speed on things like bind mounts at all.  Why even have these?  Just ask what partition to dump all the files into and let the end user juggle them around.

---

### Post by psusi on 2011-06-09
> **Skaperen said:**
> Why is sync bad for them if it's not bad for syslog?

It IS bad for syslog, which is why it only uses it on the most critical messages, and not on everything.

---

### Post by Skaperen on 2011-06-09
> **psusi said:**
> It IS bad for syslog, which is why it only uses it on the most critical messages, and not on everything.
Well, it does on everything for me, and I don't see issues with it.

---

