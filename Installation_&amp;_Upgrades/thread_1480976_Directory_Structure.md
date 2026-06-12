---
title: "Directory Structure"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by alexchamberlain on 2010-05-12
Hi,

I'm new to Linux and Ubuntu, so if this question is obvious, I apologise.

I want a quiet system, which boots quickly and doesn't cost the earth to build or run; don't we all? Anyway, I was planning on building my own PC with two hard drives:
[LIST]
[*]A solid state drive, which is relatively small to store the OS and essential programs.
[*]A normal hard drive for everything else.
[/LIST]

I understand Linux stores everything under a single root directory, rather than partition-based drives used by Windows. My question is this: can I choose which drive each directory is stored in? For instance, I want to store /boot and /etc on the solid state, but /home and /usr on the normal hard drive. Furthermore, I understand I could use separate partitions for each directory, then mount them, but that doesn't seem very flexible. Would anybody disagree with this strategy?

Furthermore, is there anything else software-wise I can do for a quick boot?

Thanks,

Alex

---

### Post by mikewhatever on 2010-05-12
You can create separate partitions for /usr and /home on the regular hdd and keep the rest on the ssd. It would be a good setup, given the small size of the ssd, as /usr takes a significant amount of disk space and keeps growing as you install applications.

---

### Post by alexchamberlain on 2010-05-12
mikewhatever: Is it possible to store /usr and /home on a single partition?

---

### Post by dino99 on 2010-05-12
i dont know what doc you've read but Ubuntu is designed for Humans :P
no need to add complications when they are not requested .

follow this mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by alexchamberlain on 2010-05-12
Last time I checked, students were still human...

Anyway, if I have to fix the partition sizes I suppose I will, but I really don't want to. I want the system to be flexible, which means I want to see /home and /usr stored on a single partition...

---

### Post by dino99 on 2010-05-12
> **alexchamberlain said:**
> Last time I checked, students were still human...

Anyway, if I have to fix the partition sizes I suppose I will, but I really don't want to. I want the system to be flexible, which means I want to see /home and /usr stored on a single partition...

so you may specified you need a server structure

---

### Post by alexchamberlain on 2010-05-12
> so you may specified you need a server structure

Do I really need a server structure? I'd like to learn about how to set up a server, but I wasn't planning on doing it quite yet.

I still don't believe it can't be done though; I thought Linux was suppose to be flexible...

---

### Post by alexchamberlain on 2010-05-12
I might have solved my own problem...

Rather than find a flexible way of storing the folders, I thought is there a flexible way of managing the partitions... I resolved to using Logical Volume Manager. I have no idea how it works, but I think it will do what I want it to do.

However, I just have to decide which folders to put where... The folders on the SSD should be the ones accessed most frequently and/or need to be accessed quickly; everything else should be on the hard drive, which will be comparatively loud, slow and uses more power. Has anybody got any advice on this?

Thanks a lot!

---

