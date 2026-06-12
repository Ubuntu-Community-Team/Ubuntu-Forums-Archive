---
title: "&quot;Resizing Impossible&quot;"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by bastianbux on 2010-06-10
I've always been curious about Linux but too Microsoft brainwashed to give it a go. Until I suffered a severe virus issue. After fixing that, I'm done with Windows.

Some quick researched showed Ubuntu to be everyone's fav version, so I thought I'd give it a go.

I burnt a Live CD of the current version (10.04) and popped it in my laptop.

It asked if I wanted to install or give it a try first. I decided to give it a try. A day's worth of testing had me convinced that I should install, but a a LOT of my programs are Windows-only. And I have over 40 gigs of music I don't want to lose. So I decided to try installing with a dual boot.

At first it showed the option for guided partitioning. I tried that. It showed I already had a 7 gig partition for Win XP/NT (which is weird) and another partition of 93 gigs for Win XP Professional (which I'd always thought was just regular XP). I tried to resize the larger one (which has a little over 20 gigs of free space) . . . and something went wrong. I don't remember what.

So then I rebooted and tried again . . . but that "guided" option was missing!
Now it only lists the option to erase the 93 gigs or to manually repartition.

So I chose "manual" . . . but I got lost very very quickly. 

Then I remembered the "alternate" version option and downloaded and burnt THAT CD and tried to use "Guided" on that . . . and my laptop turned off because I guess it was out of battery.

So then I rebooted . . . and "guided" was missing from THAT list. So I tried "manual" . . . easier to understand this time around . . . selected "resize" . . . and it never progressed beyond "0%" and paused there a while and then gave an error message that said something about "resizing is impossible"

Help!

I want to make the switch to Linux, but I don't want to lose the option to go back into Windows for all my windows-only programs. Nor do I want to lose all my files there.

---

### Post by darkod on 2010-06-10
If the first resize went wrong, there is a setting left somewhere and that's why it's preventing new resize until the problem is taken care of. In fact, don't push for another resize.

If you can boot your XP, open command prompt and run:

chkdsk /f /r

It will probably ask for reboot to do the check. You might even run few checks until you're happy all is sorted out.

One way to check if after that ubuntu still has issues with it, is to boot the live mode again, open Gparted in System-Administration and look at the disk. If ubuntu still has issues, next to the XP partition there will be triangle warning mark. Sometimes even right-click, Check on the partition can give you a hint what is wrong.

For XP it's actually better to boot in live mode like this, use Gparted to resize, don't use the guided mode. When the resize is done and leave unallocated space, leave it as unallocated. Boot XP few times because it might want to run disk checks again after the resize. Then in the installer just select Use Largest Available Free space and that will install ubuntu into the unallocated space.

Run the chkdsk from XP first and then continue as above.

PS. The 7GB partition might be recovery partition if you have one. It never shows in My Computer, but linux sees everything. :)

---

### Post by bastianbux on 2010-06-10
Thanks for that quick reply! I went ahead and ran chkdsk and it reported no issue.

> **darkod said:**
> 
open Gparted in System-Administration and look at the disk. If ubuntu still has issues, next to the XP partition there will be triangle warning mark. Sometimes even right-click, Check on the partition can give you a hint what is wrong.
Thanks! I've done that, and . . . I really don't understand what it's trying to tell me. Right clicking on the triangle shows a long list of "cluster failed at" and then a set of numbers.

> For XP it's actually better to boot in live mode like this, use Gparted to resize, don't use the guided mode. 
When I'm in GParted, I see two partitions. The top one is the weird 7gig one. It shows 5.74 GiB used and 1.27 unused. The second one, however shows "--" in both used and unused and in the Flags field says "boot" . . . 

When I select that one and right click  and select on "resize/move" I get lost.
It says "min 88224" and "max 88224" then it has three fields I can change, but I'm not sure what they mean. "Free Space Preceding" and "New Size" and "Free Space following"

eek.

> PS. The 7GB partition might be recovery partition if you have one. It never shows in My Computer, but linux sees everything. :)
I'm not really sure what that means, to be honest.

---

### Post by darkod on 2010-06-11
The 88224 is your current size.

The free space preceding is if you want free space in front of the new partition, the second field is the size of the new (resized) partition, and the third field is free space after it.

So if you want to chop 20GB off, but you want the free space to remain in front of the partition, the three fields would say like 20000, 68224, 0.

20GB new free unallocated space in front, 68GB the size of the resized partition, and 0GB space after it.

But I doubt it will allow you to resize as long as the triangle mark is there. You can try, but first make a full backup of your XP. These errors should not exist so you have to be careful and have a backup of your data.

---

### Post by efflandt on 2010-06-11
The small partition may be some sort of recovery partition.  But it is difficult to say without knowing what brand of computer.

You have not mentioned whether you ran **chkdsk /f** on your Windows partition or whether you can still boot from it.  If it will not boot, you may need to run your Windows CD or DVD or whatever it is, and do **chkdsk /f** from the recovery console.

Gparted is not going to touch that partition or allow you to change anything on it until you fix it from Windows.  Although, if you can boot an Ubuntu CD, you might be able to mount it and copy file from it to USB.

It is usually best to temporarily disable virtual memory (Windows version of swap) in WinXP before resizing, because that is in a fixed location and might limit the amount of resizing.  That is somewhere under System in an Advanced tab.  You have to reboot Windows for removing virtual memory to take effect.  After you install Linux, you could re-enable virtual memory in Windows.

When I first got my computer in 2004 I did not do that, and I could only free up 24 GB of a 200 GB drive.  More recently when I did disable WinXP virtual memory first, I could have resized it much smaller if I wanted to.

---

