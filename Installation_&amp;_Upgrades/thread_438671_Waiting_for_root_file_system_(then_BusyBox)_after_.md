---
title: "Waiting for root file system (then BusyBox) after remote upgrade"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by qopit on 2007-05-09
I just sort of completed a (very) painful upgrade from Dapper Drake to Feisty Fawn.  It wasn't a smooth undertaking... I ended up stripping down the OS a lot with dselect and then re-installing a heck of a lot (including base X stuff and ubuntu-core, etc).

In the end it all seemed to work great... to the point where a "sudo aptitude upgrade" came up with nothing to do whatsoever.

After much rejoicing I rebooted the machine...

Now I'm stuck in a "BusyBox" shell.  I've never seen this before but after much digging around I see more-or-less why Ubuntu has this, but more generally/importantly that this is probably not good news and usually means some sort of hardware problem.

There should be no hardware issue with this machine as it ran perfectly for many months with Dapper Drake.

When I interrupt GRUB the following kernel versions are available:

[LIST]
[*]2.6.15-28-386
[*]2.6.15-27-386
[*]2.6.15-26-386
[/LIST]
and the matching recovery mode versions and memtest of course.

None of the 3 (6) work.  All of them stall out at "begin waiting for root file system" when I run the recovery mode versions (after successfully locating USB and 2 ports).  After a little bit of waiting, the BusyBox shell pops up.

After much internet digging what I came up with was trying to get the file system to load right by running "update-initramfs" (worked for this guy: [https://answers.launchpad.net/ubuntu/+question/5429)](https://answers.launchpad.net/ubuntu/+question/5429)), or checking out the /etc/fstab file to make sure the drives are mounted right.  Unfortunately the former doesn't exist in BusyBox and there doesn't seem to be an /etc/fstab visible (!?!?) so that went nowhere. 

What is really weird to me is how BusyBox is behaving...
[LIST]
[*]"ls /" shows the expected slew of expected dirs like /bin, /etc, and more
[*]"ls /etc" comes up with nothing!
[*]"cat /etc/fstab" then clearly comes up with nothing
[*]"ls /bin" is empty
[*]"which ls" to try and figure out where everything is doesn't work
[/LIST]
What the heck?! :confused: 

Any advice on how to get out of this hole is appreciated.  What can I do in BusyBox to set the root filesystem straight?

My next attempt will be to try a live CD on this machine, but the kicker is that it is physicall 5 hours away from me... I've done all upgrading via SSH and the subsequent BusyBox investigations by phone with my mother-in-law (her pc).  If anyone knows how to work within BusyBox to get the root file system configured properly again I would be very grateful!

Thanks!

---

### Post by irieken on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I might have a solution for you!

In this post: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/32123)
I found a message by Alf Lervåg that was very helpful.

The gist was this: When you get dropped to Busy Box prompt, type in:
modprobe ide-disk; modprobe ide-generic; cat /sys/block/hda/dev; mknod /dev/hda1 b 3 0

Then press ctrl+D, and your machine will boot (worked for me)!

From there, I hear that installing and using YAIRD to build the initrd image fixes the problem:)

---

