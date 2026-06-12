---
title: "Please improve [UbuntuReinstallation]: &quot;Serious data loss due to misleading UI&quot;"
date: 2017-01-10
forum: Installation &amp; Upgrades
---

### Post by maxbb on 2017-01-10
I'd like to reinstall (not upgrade) 14.04 from the DVD, and keep my /home and its encrypted directories.

I couldn't find any detailed instructions on how to do that (For example, how do I communicate to the installation program that I want to keep the same users? Will the fact that the directories are encrypted be a problem?)

Instead, I found 

[LIST=1]
[*]Lots of people complaining that Ubuntu wiped their /home when they tried to avoid doing it
[*][This bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") that mentions "Serious data loss due to misleading UI"
[*][This sorry article]("https://help.ubuntu.com/community/UbuntuReinstallation") on ubuntu.com that is called "Reinstallation", but its included screenshot is clearly and major version upgrade. (**Edit**: And it doesn't warn the reader about the misleading UI at all)
[/LIST]

Now, one can't improve the installer's UI for 14.04, but I hope the community can at least improve the online documentation to mitigate the "misleading UI" somewhat.

I personally want to know how to reinstall 14.04 from the DVD, as I mentioned, but I don't expect someone to write a HowTo just for me. I hope that if the article gets improved, others may benefit.

On the other hand, if Ubuntu actually can't reinstall itself without screwing up /home, FFS, please state so clearly in the article too.

**Edit** From the bug report thread:

> [COLOR=#333333][FONT=monospace]Even if you have a single boot system, "reinstall ubuntu" or "replace windows" silently erases all partitions on the hard drive.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2017-01-10
1. When you reinstall, make sure the existing /home is not ticked to format. You can also set it as 'Do Not Use'. Its that simple. /home will not be touched.

If you want to use the /home partition for the new install, untick 'format' and set to 'Use'. The install will then consider /home to be /home, utilise it accordingly but won't reformat it. 

Bottom line: there is a box next to /home when you are installing in the 'Format' column. Make sure it is not ticked.

As far as data loss goes because of a pear-shaped install? ALWAYS do reliable backups of any important data prior to doing anything like what you are talking about. Rule of thumb. Doesn't matter how simple or hard Ubuntu or any other OS might be to install or upgrade or whatever.

Serious data loss is due to a lack of serious back ups. When you say 'you' I presume you mean the community, which you are now part of. Feel free to make any improvements you have come across to whatever pages you find where you can and contributing that way. As far as improving installers, you can approach Canonical Ubuntu devs with your suggestions re. that. 

Good luck. ;)

---

### Post by maxbb on 2017-01-10
Isn't there more to it: matching UIDs required, encryption issues, as I mentioned in the OP?

---

### Post by Bucky Ball on 2017-01-10
Keeping the same users? Yes, probably. As for not destroying /home when you are reinstalling, no.

Try this:
[https://ubuntuforums.org/showthread.php?t=2057342](https://ubuntuforums.org/showthread.php?t=2057342)

Or this:
[https://ubuntuforums.org/showthread.php?t=1569675&p=9815691&viewfull=1#post9815691](https://ubuntuforums.org/showthread.php?t=1569675&p=9815691&viewfull=1#post9815691)

PS: You can also use the existing /swap. No need to create another. Same applies. Doesn't matter if you mark to format or not, though. Just make sure it is set to 'Use'. ;)

Bottom line: Set /swap and / to format and use; /home set to use but NOT format. As for keeping the same user, the hunt goes on. If you use the same user name in the new install as the old that may be all there is to it, but don't quote me. That's gonna need some (more) research ...

---

### Post by ian-weisser on 2017-01-10
> **maxbb said:**
> Instead, I found 

[LIST=1]
[*]Lots of people complaining that Ubuntu wiped their /home when they tried to avoid doing it
[*][This bug report]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192") that mentions "Serious data loss due to misleading UI"
[/LIST]

Now, you can't improve the installer's UI for 14.04, but I hope the community can at least improve the online documentation to mitigate the "misleading UI" somewhat.

That serious bug was fixed years ago...in ubuquity 2.20, included with Ubuntu 14.10.
There shouldn't need to be many online documentation changes. Please feel free to make the online doc changes that need to be made. Remember to note that your additions apply to 14.04 only to avoid confusing everyone.

You won't find many developers in the support forums, so 'please-improve-this' posts are generally wasted here. They tend to congregate in places in code-heavy places that they find more rewarding.

---

### Post by maxbb on 2017-01-10
> **ian-weisser said:**
> That serious bug was fixed years ago...in ubuquity 2.20, included with Ubuntu 14.10.
There shouldn't need to be many online documentation changes. 


I am using 14.04 LTS (as I mentioned a few times), so it's not fixed there.

Side note: I think it's still the most popular version among professional users.

> 
You won't find many developers in the support forums, so 'please-improve-this' posts are generally wasted here. 

That article is community-supported. (Although frankly, the people who messed up the UI should at least have the decency the minimize the damage via online documentation)

---

### Post by ian-weisser on 2017-01-10
> **maxbb said:**
> I am using 14.04 LTS (as I mentioned a few times), so it's not fixed there.
Since you feel it's important, have you requested [an SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") to 14.04 for the fix?
SRUs are not automatic.

> **maxbb said:**
> That article is community-supported. (Although frankly, the people who messed up the UI should at least have the decency the minimize the damage via online documentation)
Have you reminded them? Perhaps they merely forgot? Good people forget things all the time.

---

### Post by ubfan1 on 2017-01-10
It isn't clear to me that you actually have a separate partition mounted at /home.  Of course, a partition may be easily left out of any reinstall, as Bucky Ball said. but if /home is just part of the root filesystem, not a mount, then the reinstall will probably wipe it (I don't do reinstalls, so I assume the UI is like the plain install). Back up in any case.

---

### Post by maxbb on 2017-01-10
Separate partition, although the article should of course address both cases.

The question of matching user IDs and encryption in /home remains totally open, as I understand it.

In this case, the article should say it, instead of pretending that it's all good.

---

### Post by ian-weisser on 2017-01-10
The installer will ignore or retain a /home directory, if told to (and if not reformatted).
However, the retained /home dirs will be temporarily orphaned, as the user accounts will be wiped with /etc, and must be restored with adduser, an adduser script, or backed-up /etc files

---

### Post by maxbb on 2017-01-10
From the bug report thread: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/20](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192/comments/20)

>  [COLOR=#333333][FONT=monospace]Even if you have a single boot system, "reinstall ubuntu" or "replace windows" silently erases all partitions on the hard drive.[/FONT][/COLOR]

I am trying to understand this part. Are you never presented with the choice not to format `/home` if you choose "reinstall"? That's what the above sounds like.

---

### Post by ian-weisser on 2017-01-10
Try it in a VM and find out definitively.
I installed many 14.04 machines, and reinstalled a few, and do not recall any problems with either...but that was years ago. I stopped using the 14.04 installer when 14.10 came out.

---

### Post by Bucky Ball on 2017-01-10
> **maxbb said:**
> Are you never presented with the choice not to format `/home` if you choose "reinstall"? That's what the above sounds like.

When you are installing you choose 'Something Else' at the partitioning section of the install and manually partition. Then you can make the changes we have been talking about and select where and what you are going to install.

If you select 'Install using whole disk', or whatever the wording of that option is, instead of selecting 'Something Else', then no, you will not be offered the option to do anything more but sit back and watch. The disk will be wiped and Ubuntu will be installed (or Ubuntu will be installed next to Windows if you have chosen the 'side-by-side' dual-boot install option).

---

### Post by maxbb on 2017-01-10
Thanks for the clarification, Bucky Ball.

I still don't understand how encryption would "just work" though. Ubuntu uses a long key, different from your password, to decrypt your home directory. 

Does it need to be communicated to the new OS installation?

---

### Post by maxbb on 2017-01-11
By the way, I tried editing the article: clicked on "Log in to Edit" and logged in, but then the web site told me that it's an "Immutable Page" (Talk about non-misleading UI)

I guess I don't have the right permissions or something.

---

