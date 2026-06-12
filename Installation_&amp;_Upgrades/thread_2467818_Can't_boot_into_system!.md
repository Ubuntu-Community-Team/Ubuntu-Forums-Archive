---
title: "Can't boot into system!"
date: 2021-10-08
forum: Installation &amp; Upgrades
---

### Post by gruffalo2 on 2021-10-08
info from Boot-repair: [https://paste.ubuntu.com/p/M8MTQS58Mq/](https://paste.ubuntu.com/p/M8MTQS58Mq/)

I have a laptop dual booted with Windows and Ubuntu. Never used Windows apart from when I first installed it. I accidentally deleted the Windows partition (and maybe a few other partitions) when I thought I was formatting my USB drive

Rebooted the machine and now I cannot log into Ubuntu. Any ideas?

---

### Post by tea for one on 2021-10-08
[COLOR="#0000FF"]Line 17 [/COLOR] - 0 (zero) OS detected

No sign of installed Windows nor installed Ubuntu.

Something went pear-shaped during the installation procedure?
No error messages reported while installing?

Install Ubuntu again and re-store your backups?

---

### Post by gruffalo2 on 2021-10-08
Yes, I noticed that line... however, I have been using Ubuntu for about 3 months with no problems. I dont understand why the install has just disappeared. Do you think it is definitely disappeared or I am doing something wrong?

---

### Post by Impavidus on 2021-10-08
It only appears to detect one hard drive, sda, which appears to be a live disk on a 128GB Lexar USB Flash Drive, according to line 77. So no internal hard drive is detected. Loose cable maybe?

---

### Post by gruffalo2 on 2021-10-08
Strange, it is a m.2 SSD. When I go to install Ubuntu it detects the M.2 drive. Let me try and get a screenshot

---

### Post by tea for one on 2021-10-08
> **gruffalo2 said:**
> Yes, I noticed that line... however, I have been using Ubuntu for about 3 months with no problems. I dont understand why the install has just disappeared. Do you think it is definitely disappeared or I am doing something wrong?

Impossible to answer whether you are doing something wrong?
I would have to be looking over your shoulder wearing my invisible spy outfit? ;)

> **gruffalo2 said:**
> I accidentally deleted the Windows partition [COLOR="#FF0000"](and maybe a few other partitions)[/COLOR] when I thought I was formatting my USB drive

This is probably the relevant info.
Do you know which partitions you deleted?

---

### Post by gruffalo2 on 2021-10-08
I think it was all partitions apart from the Ubuntu partition because it threw a "disk in use" error!

I ignored it as I thought I only deleted the Windows partition which I dont need anyway

---

### Post by tea for one on 2021-10-08
Boot into a live session using your Ubuntu installation media.
Open a terminal and post the output:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

Please post the output within code tags

---

### Post by gruffalo2 on 2021-10-08
> **tea for one said:**
> Boot into a live session using your Ubuntu installation media.
Open a terminal and post the output:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

Please post the output within code tags

Thanks for your suggestion. It turns out the m.2 drive was loose. After fixing that I got the &#8220;GPT detected. Please create a BIOS-Boot partition&#8221; while using boot-repair. I decided to back everything up and reinstall Ubuntu. During the reinstall I saw an option to run new Ubuntu with my previous install, choose that and now I am back into my system!

I do have 2 x Ubuntu installs but at least I am back in business!

---

### Post by tea for one on 2021-10-08
That's good news.

Please mark the thread as solved [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

