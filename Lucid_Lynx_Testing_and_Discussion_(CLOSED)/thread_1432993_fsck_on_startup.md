---
title: "fsck on startup"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mick222 on 2010-03-18
Every time i reboot I get fsck util linux-ng for a couple of seconds, my computer then starts normally.Does anyone know where i can get more information on this, something like a log file so that i can give more info.

---

### Post by awam66 on 2010-03-18
I get the same and it says it is doing a check but it doesn't, or if it does it only lasts a few seconds.

---

### Post by tajreed on 2010-03-18
Samething here after tuesdays update, except that my laptop will not boot> Screen says checking disks but nothing happens for hours. I guess I'll have to do a clean install with the Beta.

---

### Post by mick222 on 2010-03-18
can no one help or is it a bug.If it is a bug I still need more information as it obviously affects more people than me.
    Tajreed that happened to me but skipping the disk check allowed my computer to boot

---

### Post by seeker5528 on 2010-03-18
> **mick222 said:**
> Every time i reboot I get fsck util linux-ng for a couple of seconds, my computer then starts normally.Does anyone know where i can get more information on this, something like a log file so that i can give more info.

Not 100% sure if this applies to what you are seeing, but my expectation is that fsck will run on every boot to see if some condition exists that requires recovery or if it is time to do a file system check because it is set in the file system options to do a check after every X number of times you have booted, then if there is no reason to check the file system it exits and the boot continues.

It could be argued that unless you have opted to see all the text produced during the boot process you should not see anything about fsck unless it actually has to do a recovery/file system check, which I would agree with, but personally if it comes down to a choice between seeing something about fsck on every boot or not seeing anything to indicate why the boot is taking so long in the cases where a file system check is being done, I would prefer to see something about fsck on every boot.

Later, Seeker

---

### Post by mick222 on 2010-03-18
Thx that could be it

---

### Post by dcstar on 2010-03-19
> **mick222 said:**
> Every time i reboot I get fsck util linux-ng for a couple of seconds, my computer then starts normally.Does anyone know where i can get more information on this, something like a log file so that i can give more info.

Add in the /var/log/fsck logs to your Log File Viewer list.

---

### Post by dino99 on 2010-03-19
> **dcstar said:**
> Add in the /var/log/fsck logs to your Log File Viewer list.

interesting but the latest info added into /var/log/fsck was Dec 27th , strange as i boot several times a day every day and having like many of us some competition of fsck/ureadahead/plymouth, for example ureadahead always ended with status 4. (dont know exactly what that mean)

But the fact is nothing is logged about that.

---

### Post by grandtoubab on 2010-03-19
same here
[http://ubuntuforums.org/showthread.php?t=1429761](http://ubuntuforums.org/showthread.php?t=1429761)

---

### Post by mick222 on 2010-03-20
thx this is what i was looking for but cant find var/log/fsck only  var/log/fsck/checkroot or checkfs which are both empty
> Add in the /var/log/fsck logs to your Log File Viewer list.

---

### Post by keybuk on 2010-03-20
> **mick222 said:**
> Every time i reboot I get fsck util linux-ng for a couple of seconds, my computer then starts normally.Does anyone know where i can get more information on this, something like a log file so that i can give more info.

fsck is the filesystem checking tool, we always do a quick check of your disk before we enable writing to it on boot - it takes no more than a tenth of a second or so.

The fact you see the message at all is because we haven't hidden the console messages yet, we'll be doing that before Lucid releases but left them on for now to aid in debugging

---

### Post by kansasnoob on 2010-03-20
> **keybuk said:**
> fsck is the filesystem checking tool, we always do a quick check of your disk before we enable writing to it on boot - it takes no more than a tenth of a second or so.

The fact you see the message at all is because we haven't hidden the console messages yet, we'll be doing that before Lucid releases but left them on for now to aid in debugging

Thanks for the explanation. I was going to, and still will, add a note here that seeing that can actually be quite helpful. The Lucid install I'm actually using now was reinstalled on 3-13 as it had been the original that I started with when the toolchain was first uploaded.

But in the process of doing iso testing I noticed a huge difference in boot time, degree of quietness, etc. So I knew that something I'd done had made a negative difference. Well, I'd recently copied some of my partitions to a different drive due to hard drive failure so it was time to reinspect everything :)

Sure as heck I found a problem. I have four shared data partitions that I set up to auto-mount and symlink to my home folder so no matter which OS I'm using my Downloads, Documents, Pictures, and Backups are accessible and up-to-date without searching and fiddling.

Well in the process of copying these partitions and then editing fstab I goofed, they did still mount because I use UUID's but I had the mount-point wrong so that accounted for an additional 30 to 40 seconds of "thrashing" before things all mounted ;)

---

### Post by mick222 on 2010-03-20
thx for the replies guys .

---

