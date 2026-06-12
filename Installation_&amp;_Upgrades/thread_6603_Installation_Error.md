---
title: "Installation Error"
date: 2004-11-29
forum: Installation &amp; Upgrades
---

### Post by herrard on 2004-11-29
Hi. I've been having trouble trying to install Ubuntu 4.10 amd64.

At first, I would use the default installation. Everything seems fine until it starts installing the base system and then I get an error with the "initrd-tools package". I've tried to reinstalling for at least 5 times now with the same results.  

There is something odd though that I noticed... when I'm in the partition screen, Ubuntu thinks that my disk is SCSI and not IDE. From what I know from the other distros I've installed, I'm quite positive I have IDE.

Finally, after many futile attempts installing Ubuntu with the default installation, I decided to try out expert mode. I went through the whole thing without any problems.  In fact, the base system installation was able to go further than in the default, asking me what kernel i was to install (i think.. I'm not sure now--I can't remember).. I chose "linux.amd64.generic".. there were 3 other choices but I thought this one made the most sense. Alas, after picking linux.amd64.generic... I get the error again.  Interestingly tho, during the expert installation mode... it said that the following modules were unavailable: ide-scsi, ide-mod, ide-probe-mode, ide-detect, ide-floppy.  So I guess I was right... Ubuntu couldn't dectect my IDE hard drive because the modules won't load.

Well... I guess my question is whether the fact that Ubuntu thinks that my harddrive is SCSI instead of IDE is making the installation fail? If so, how do I work around it? If not, what am I doing wrong?


Thank you in advance.

p.s. I have a 120GB Maxtor DiamondMax Plus 9

---

### Post by adbak on 2004-11-30
Perhaps the CD that you're using to install Ubuntu is bad?

---

### Post by herrard on 2004-11-30
I don't think so. I used the integrity check that the cd had and it said the integrity was fine.  In addition, I checked the md5sum of the file I burned and it matches the one indicated by the website. Finally, I used k3b to burn the cd and verify the written data and everything was ok. I doubt its the cd.. because this is the second cd I burned and I got the same result.

Well.. I guess a 3rd burned cd won't hurt. I'll get back to you if anything changed.

Thanks.

---

### Post by herrard on 2004-11-30
I got it... I was using the wrong kernel... even still though... i can't install Ubuntu through the default installation setting... i need to use the expert mode for some reason. I don't know why but that doesn't matter now i guess because I got it installed (however, i must note that it took me about 1 hour to set everything up.. I was having trouble setting up emacs21 and ubuntu-linux... i was forced to apt-get remove them and then reinstalling them again)

---

### Post by busser on 2004-12-05
Can you give a more detail description of how you solved the problem.

I have similar problem with unavailable modules (same modules as yours). Actually the first part of installation, until the first reboot, works fine, but then GRUB won't load the kernel complaining about being unable to mount partition (my root is /dev/hdb3 and that's what the root parameter for the kernel is set to).

If I use LILO as the boot loader, it stops after trying to start the base-config script saying that respawn is too fast or something like that and that it will wait 5 minutes. Then it tries to start base-config again with the same result. The error message base-config gives is:
Configuring the base system...
/usr/sbin/base-config: ./prep-menu: /bin/sh: bad interpreter: Access denied
Script started on Su* 5.*Dec*2004,*13:44:55*UTC

---

