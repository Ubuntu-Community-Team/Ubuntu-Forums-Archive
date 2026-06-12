---
title: "question on partitioning new HD - openSUSE, BT3, UbuntuStudio, XP"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by Koohiisan on 2008-10-27
Hello!  I posed this question to the kindly folks over at openSUSE's forums, but I thought I might find some useful guidance here as well.

(original question: [http://forums.opensuse.org/install-boot-login/398194-partitioning-new-hd-opensuse-bt3-ubuntustudio-xp.html](http://forums.opensuse.org/install-boot-login/398194-partitioning-new-hd-opensuse-bt3-ubuntustudio-xp.html))

I inherited a Japanese Toshiba Dynabook E9 and want to upgrade the HD from a 30 GB to 160GB (or 250GB if I can justify it to myself and my wallet).  The laptop is four years old, so I believe it to be new enough to have defeated the 32-bit barrier on hard drive size.  

I want openSUSE, UbuntuStudio, and BackTrack 3 installed, plus a minimal XP Pro for the stuff I may need Windows for, or I could virtualize it I suppose.

I want to lay out my partitioning plan first, before I decide on what size drive to get, and before I sit down to actually do the partitioning!  Here is my idea, which I have changed a bit since my original post on the openSUSE forums:

10GB - / (openSUSE)
2GB - swap (laptop has 1GB memory)
110GB - /home (to be used by openSUSE, UbuStu and BT3, if it is possible)
10GB - / (UbuntuStudio)
8GB - / (BackTrack 3)
20GB - Windows XP

(If I get a larger drive, I will probably add all the extra space to my /home partition.)

Are there any fundamental flaws here?  Are my partitions large enough?  Too large?  Do I need to separate /var or any other partitions?

As far as the /home partition, I am going to use different usernames on the different distros, so they will not conflict with each other's settings (e.g., myname-suse, myname-ubustu).

I'm going to use the unofficial installer script thingy for BT3.

I look forward to whatever guidance and ideas you may have!  I have gotten some good help here in the past--that's for sure.  Thanks in advance!

---

### Post by lemming465 on 2008-10-28
I don't see any problem with that.  You might want to make XP the first partition, and primary, and install it first, thought that's not absolutely required.

---

