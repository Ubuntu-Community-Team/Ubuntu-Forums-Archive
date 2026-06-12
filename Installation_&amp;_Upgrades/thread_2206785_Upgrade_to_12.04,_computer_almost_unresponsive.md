---
title: "Upgrade to 12.04, computer almost unresponsive"
date: 2014-02-20
forum: Installation &amp; Upgrades
---

### Post by uzzo23 on 2014-02-20
From 10.04 to 12.04 and the computer it's on has become almost unresponsive. It hasn't been very fast since I switched MOBO's out with a much slower CPU. But it was working in 10.04, but I started having boot up issues. So I decided to go ahead and upgrade. Has anyone else had the same issues?

---

### Post by papibe on 2014-02-20
Hi uzzo23. Welcome to the forum ):P

Could you describe your hardware? CPU, RAM, graphic cards, and free space in HDD?

In general, 12.04 would run slower than 10.04 in the same machine, because 12.04 is more graphic intensive.

Without knowing much details, I'd say you could either upgrade your graphic card, or use another less graphic intensive desktop (like Xfce).

Another idea would be to make a clean install of 12.04 as, in a few cases, upgrades don't work perfectively.

Regards.

---

### Post by uzzo23 on 2014-02-21
> **papibe said:**
> Hi uzzo23. Welcome to the forum ):P

Could you describe your hardware? CPU, RAM, graphic cards, and free space in HDD?

In general, 12.04 would run slower than 10.04 in the same machine, because 12.04 is more graphic intensive.

Without knowing much details, I'd say you could either upgrade your graphic card, or use another less graphic intensive desktop (like Xfce).

Another idea would be to make a clean install of 12.04 as, in a few cases, upgrades don't work perfectively.

Regards.

Thanks my friend for the welcome. But I've been a member since version 8.04, when they redid this website I couldn't log back on using my old login info. It created a brand new account, someone else was supposed to try and straighten it out and it wound up creating another new account. So I just gave up and decided to keep what I have and start over. Anyhow, you're probably right about it running slower if 12.04 is more of a memory hog. The old MOBO was an XFX with a dual core pentium d processor and 2GB of ram. It bit the dust and I found a salvage box that had a mobo in it and just for squats and grins put in this box and it worked. It's just WAY slower than the other board and CPU.
But it's a biostar p4m80-m4 with a single core pentium 4 and only two 256MB sticks of RAM. I've got two 1GB sticks ordered for it. Hopefully that'll straighten it out.

---

### Post by SuperFreak on 2014-02-21
Lubuntu might work better

---

### Post by uzzo23 on 2014-02-21
> **SuperFreak said:**
> Lubuntu might work better

I really hate to mess with it too much. The last upgrade I did was to 11.10 and I had audio issues with it. I went back to 10.04 and lost everything. Yeah, I know, I should've backed it up but I was in a hurry and thought it would be fine. I submitted a bug report on the audio issue and as far as I know, it's never been solved.

---

### Post by SuperFreak on 2014-02-21
I understand completely. Lubuntu needs considerably less RAM to run 12.04 than the regular Ubuntu 12.04, but you are right; it may result in hardware incompatibility

---

### Post by uzzo23 on 2014-02-21
> **SuperFreak said:**
> I understand completely. Lubuntu needs considerably less RAM to run 12.04 than the regular Ubuntu 12.04, but you are right; it may result in hardware incompatibility

Thanks for the advice, I really appreciate it. If 2GB of RAM doesn't fix it, then I will certainly look into Lubuntu. Is there a resource available where I can read about it. Is it pretty similar to ubuntu other than more graphic intensive? The only other distro I've tried was mint. I can't remember what it was now, but I didn't like it and switched back to ubuntu. Like I said, I'm just afraid to mess with things too much because I'm not near as smart as most everyone here when it comes to computers. I can build them, but making them work when there's an issue with it is a different story.

---

### Post by SuperFreak on 2014-02-21
[http://lubuntu.net/]("http://lubuntu.net/")

It is actually less graphic intensive I think, and is just a variation of Ubuntu

---

### Post by uzzo23 on 2014-02-21
I'm sorry guys, but I had one more question that I forgot to ask. In 10.04 I had several applications running from the panel. One was a temp. monitor that monitored temperatures for the CPU and HD. The other was a force quit application for unresponsive programs. Did that go away with 12.04?

---

### Post by papibe on 2014-02-21
> **uzzo23 said:**
> it's a biostar p4m80-m4 with a single core pentium 4 and only two 256MB sticks of RAM. I've got two 1GB sticks ordered for it.
I have a pentium4 laptop running [Xubuntu]("http://xubuntu.org/") very well. Xubuntu uses the Xfce desktop which has a very similar look and feel to 10.04's GUI.

It uses less resources than vanilla Ubuntu, but a bit more than Lubuntu (SuperFreak's suggestion).

I'd recommend taking a look at it because it may be a smother transition from 10.04

Hope it help.
Regards.

P.S.: I'd recommend only considering Xubuntu with at least 1Gb of RAM.

---

### Post by uzzo23 on 2014-02-21
> **papibe said:**
> I have a pentium4 laptop running [Xubuntu]("http://xubuntu.org/") very well. Xubuntu uses the Xfce desktop which has a very similar look and feel to 10.04's GUI.

It uses less resources than vanilla Ubuntu, but a bit more than Lubuntu (SuperFreak's suggestion).

I'd recommend taking a look at it because it may be a smother transition from 10.04

Hope it help.
Regards.

P.S.: I'd recommend only considering Xubuntu with at least 1Gb of RAM.

I definitely will look at it. Would I be in trouble of losing any of my files, bookmarks, etc... if I made the switch?

---

### Post by papibe on 2014-02-21
There are some risks.

You can keep your data only if you have a separate /home partition, and during the installation process you explicitly set to not format that partition and mount it as /home.

If you don't have a separate /home partition, you can either, carefully:
[LIST]
[*]Boot into a Live CD and launch Gparted.
[*]Shrink the main partition to create extra space.
[*]Create a new partition on the freed space and format it.
[*]Boot normally
[*]Mount the new partition on a temporary location (e.g. /mnt/home)
[*]Copy, or better rsync your home directory to the temporary location.
[*]Modify your /etc/fstab to mount the new partition as /home
[*]Reboot.
[*]If everything goes well you should notice anything different.
[/LIST]
Or you can (may be easier):
[LIST]
[*]Backup your data to an external or network drive.
[*]Do a clean install on your laptop, and restore your data afterwards.
[/LIST]
Hope it helps. Let us know if you need more details on that.
Regards.

---

### Post by uzzo23 on 2014-02-21
> **papibe said:**
> There are some risks.

You can keep your data only if you have a separate /home partition, and during the installation process you explicitly set to not format that partition and mount it as /home.

If you don't have a separate /home partition, you can either, carefully:
[LIST]
[*]Boot into a Live CD and launch Gparted. 
[*]Shrink the main partition to create extra space. 
[*]Create a new partition on the freed space and format it. 
[*]Boot normally 
[*]Mount the new partition on a temporary location (e.g. /mnt/home) 
[*]Copy, or better rsync your home directory to the temporary location. 
[*]Modify your /etc/fstab to mount the new partition as /home 
[*]Reboot. 
[*]If everything goes well you should notice anything different. 
[/LIST]
Or you can (may be easier):
[LIST]
[*]Backup your data to an external or network drive. 
[*]Do a clean install on your laptop, and restore your data afterwards. 
[/LIST]
Hope it helps. Let us know if you need more details on that.
Regards.

Actually, right after I posted my last reply I started researching it and came upon this.

[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

I just got finished with it, it seemed to have worked fine.

---

### Post by mörgæs on 2014-02-21
If it worked then please mark the thread solved using 'thread tools'.
If not then I (like others) suggest a fresh install of X/Lubuntu 13.10. Upgrades are risky.

---

