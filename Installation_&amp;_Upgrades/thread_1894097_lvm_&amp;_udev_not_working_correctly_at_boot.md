---
title: "lvm &amp; udev not working correctly at boot"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by bassMonkey on 2011-12-11
Hello!

I'm experiencing a really long wait when booting freshly installed xubuntu 11.10 with only updates and mdadm + lvm2 installed. I have managed to narrow it down somewhat but still looking for a fix.

After disabling splash and quiet from grub I noticed it's waiting at /scripts/init-bottom/udev in initrd and continues after 61 seconds.
Not surprisingly i found a "udevadm control --timeout 61 --exit" line in there. Well, why does it fail so badly it waits for timeout before exiting?

After quite a bit of googling I found this:
[http://us.generation-nt.com/answer/problem-lvm-gets-stuck-during-booting-due-recent-uevent-change-help-205241751.html](http://us.generation-nt.com/answer/problem-lvm-gets-stuck-during-booting-due-recent-uevent-change-help-205241751.html)
Ari Savolainen writes:
> An init script (/scripts/init-bottom/udev in initrd) issues command
 "udevadm control --timeouta --exit".

 At the same time udevd is executing "/sbin/lvm vgchange -a y" (from
 /lib/udev/rules.d/85-lvm2.rules) that calls ioctl to resume a logical
 volume. After that lvm gets stuck forever. Booting continues after the
 61 second timeout.
Milan Broz writes:
> If you call vgchange or even vgscan from udev rule, it is completely wrong.

 This is not lvm upstream udev rule btw.

This makes me slightly worried, does this cause any other problems than a annoyingly slow boot? Is there any way to fix this? I this a known issue?

Popcorn for anyone with any ideas regarding this.. :popcorn:

---

### Post by bassMonkey on 2011-12-12
Added a question to Answers: 
[https://answers.launchpad.net/ubuntu/+question/181615](https://answers.launchpad.net/ubuntu/+question/181615)

Did a reinstall just to be sure, noticed that some of my lvm volumes were added after the first boot, some after the second.

---

### Post by zontor on 2011-12-13
Similar problem here and it got much worse after adding a 170G logical volume with mirror and disk mirrorlog.
Of the last 5 boots on my ubuntu-server all stopped for at least 3 minutes at **scripts init-bottom.  **2  times got dropped into a shell in the initramfs, 1 time it just froze  and I used the power switch, and 2 times boot continued after timeout  messages from > "watershed sh -c '/sbin/lvm vgscan; /sbin/lvm  vgchange -a y'"I unpacked my > /boot/initrd.img-3.0.0-14-server and found the only instance of this command in **/lib/udev/rules.d/85-lvm2.rules**.

Using this information and the reference you posted found a rationale for this at
[https://wiki.ubuntu.com/UdevLvm](https://wiki.ubuntu.com/UdevLvm)

But I've no clue how to fix it

---

### Post by zontor on 2011-12-13
Found Bug #631795 
very similar and  still open high priority but not **hot** 
-- one recommend for adding to bug-report for #631795 is to set "udev.log-priority=debug" on the kernel command line -- 
also possibly if you get dropped to the udeb command line in the initramfs on boot check to see if the UUID link is/isn't  created (Thx psusi)

Hope this helps -- I'll to do more diagnosis on my machine to get something for the old bug report or a new one if needed -- looks to me like it's an old problem that got worse with oneiric or with bigger or mirrored or whatever -- nobody's figured it out yet.

I would guess that anything you can post to the bug report #631795 would be welcome, but please read the bug first to see if it is relevant to your problem and if you can collect the desired logs and udev state in the initramfs -- me, I'll try but time and lack of expertise limits me.

ej

running ubuntu-server on most of my half-dozen boxes

Thanks for posting.

ej

---

### Post by bassMonkey on 2011-12-15
I've found a workaround that works for me! :)

Was trying to get multiseat working with xubuntu but lightdm wouldn't cooperate so I tried with kdm, that worked wonderfully and I decieded to try kubuntu. Lo and behold lvm was no longer an issue with kubuntu and booting takes ~8secs now, with 3 VG:s 4 LV:s on 3 PV:s! I haven't investigated the differences yet but I'm really happy now :KS

---

### Post by devil103 on 2011-12-15
I think I'm experiencing the same problem (topic: [http://ubuntuforums.org/showthread.php?t=1895646](http://ubuntuforums.org/showthread.php?t=1895646))

Strange that using a different distro worked. I'm using the netinstall version of the latest Ubuntu 11.10 and the latest kernel. 

I wonder where the difference could be

---

### Post by cweiske on 2012-01-10
That's probably [bug #906358]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/906358").

---

