---
title: "Feisty Upgrade ends in Grub Error 18"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by jacrider on 2007-04-19
As the title describes, I tried upgrading using the Update Manager.

Left the machine unattended and it was shut down when I returned.  Thought that was a good sign.  Booted the machine only to get a Grub  stage 1.5 Error 18.

Any ideas on how to resolve this?

Searched and didn't find anything on this.

Thanks.

---

### Post by jacrider on 2007-04-19
Rebooted and this time came up with a Grub error 16???

Any ideas?

---

### Post by Megatog615 on 2007-04-20
[quote=www.gnu.org]16 : Inconsistent filesystem structure
    This error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.[/quote]
Um, did you have any valuable data? A reinstall *should* correct the problem.

---

### Post by gatdammit on 2007-08-02
Damn, I think that's what happened to me.  I've been reading about Error 18 and it seems that all the threads have been about people doing first installs that have never booted into the machine.  I was using my machine for 3 months and I did an upgrade and this is my exact problem at the moment.  

If reinstall is the only course, is there a way to reinstall and leave my data intact? or am I just screwed ?

---

### Post by typesour on 2007-10-10
I can't offer solutions, but I can commiserate....this happened to me too! What do I do? I'm in the middle of college apps...I need the stuff on my computer.

---

### Post by Kilz on 2007-10-10
Have you filed a bug report [on launchpad?]("https://bugs.launchpad.net/ubuntu")

---

### Post by joao82 on 2007-10-10
Can't you just restore Grub using the live CD? search on the forum how to do a grub recovery/re-install.
maybe this topic can help [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by typesour on 2007-10-10
I finally got my computer to boot from the install cd, but when I tried to follow the directions on that link, the terminal told me that the disk doesn't exist! I'm so confused...what do I do?

---

### Post by joao82 on 2007-10-10
well, if you can boot from the install cd and can't find a solution, then backup all your data and do a clean install.

---

### Post by typesour on 2007-10-14
How do I back up all my data if I can't access any of it? Is there a way to back up my files from the install cd?

---

