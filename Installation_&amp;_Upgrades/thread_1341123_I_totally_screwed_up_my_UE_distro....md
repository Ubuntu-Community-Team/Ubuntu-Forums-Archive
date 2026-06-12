---
title: "I totally screwed up my UE distro..."
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by T11LMG on 2009-11-29
Well, I had a partition with Ubuntu Ultimate 2.3 on it, along with the grub bootloader. I decided to upgrade the distro to 9.10, and my laptop battery died during installation. (I hadn't realized I didn't plug the brick into the cable that runs to the socket.) I want to wipe it clean and put Ubuntu Studio 9.10 or maybe some other distro, but I fear that I'd mess up my dual boot of Vista and Ubuntu. Any suggestions of what to do so I don't do that? I have actually did that exact thing before...:P

---

### Post by phillw on 2009-11-29
> **T11LMG said:**
> Well, I had a partition with Ubuntu Ultimate 2.3 on it, along with the grub bootloader. I decided to upgrade the distro to 9.10, and my laptop battery died during installation. (I hadn't realized I didn't plug the brick into the cable that runs to the socket.) I want to wipe it clean and put Ubuntu Studio 9.10 or maybe some other distro, but I fear that I'd mess up my dual boot of Vista and Ubuntu. Any suggestions of what to do so I don't do that? I have actually did that exact thing before...:P

Make Vista the boot loader (you'll need the vista install disk for this)  [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Then delete the ubuntu area - leave as unallocated - when you boot from the LiveCD, tell ubuntu to use the un-allocated space & you'll be up and running

Regards,

Phill.

---

### Post by T11LMG on 2009-11-29
That would be great,except my custom build desktop has XP, and my laptop didn't come with a Vista CD. I need Vista for Media Editing which I why I haven't tossed it yet. Thanks for your answer, as I do appreciate it, but it isn't an option for me. D:

---

### Post by phillw on 2009-11-29
the thread tells you how to get a recovery cd ;-)

Regards,

Phill.

---

### Post by phillw on 2009-11-29
If you don't fancy that way (It's the safest) you can choose the manual re-partitioning of your hard-drive at install time for ubuntu 9.10 - You'll want 1GB or whatever your RAM is (whichever is LARGER) as swap, the rest for the installation.

It should recognise your vista area anyways, That was just a safer & easier method.

DON'T pick your vista area for resizing !!!!!

Regards,

Phill.

---

### Post by phillw on 2009-11-29
[http://www.futuredesktop.org/](http://www.futuredesktop.org/)   has a good howto for manually partitioning

Regards,

Phill.

---

### Post by T11LMG on 2009-11-29
Ahh, you sure got me on that one. I read the top, skimmed down to see what I generally had to do, and I must of skipped over that link, as it wasn't a direct link but a BBcode link with a word in place of it. I'm going to attempt such now. Thanks!

---

### Post by phillw on 2009-11-29
> **T11LMG said:**
> Ahh, you sure got me on that one. I read the top, skimmed down to see what I generally had to do, and I must of skipped over that link, as it wasn't a direct link but a BBcode link with a word in place of it. I'm going to attempt such now. Thanks!

Ahh... the Howto's are done that way - it part of the guidelines for writing them !!

Phill.

---

