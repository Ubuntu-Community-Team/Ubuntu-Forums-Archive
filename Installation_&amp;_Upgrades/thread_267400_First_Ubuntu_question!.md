---
title: "First Ubuntu question!"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by n3r0 on 2006-09-28
Hello! I recently upgraded (today) from redhat to ubuntu.

I did not have a package selection option when installing ubuntu. This has made things like sshd and who knows what else, require the CD to be in the drive to install. Ok thats fine, Ill leave it in there, but then the cd boots and doesnt load the OS on reboot.

Basically, is there a way to get it to not ask for the cd every time I want to install something from the cd? This is a racked server and im not about to drive all the way to the colo every time, just to insert a stupid cd.

Is there any way to either 1) install everything (or at least copy the files) 2) redirect apt-get to fetch the packages from the internet and never prompt for a cd insertion.

Thanks

---

### Post by Lord Illidan on 2006-09-28
Certainly.. Just edit your /etc/apt/sources.conf and remove the line which refers to your CD ROM. if you have any doubts, post your sources.conf here, and we will tell you what to do :)

---

### Post by n3r0 on 2006-09-28
Hi! thanks i just figured it out myself by reading man pages hehe... just had to comment out the cdrom line in /etc/apt/sources.list.

thanks for the help though!

---

