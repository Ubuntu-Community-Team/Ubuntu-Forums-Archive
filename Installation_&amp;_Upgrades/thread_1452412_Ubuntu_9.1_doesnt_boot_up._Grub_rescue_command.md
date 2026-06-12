---
title: "Ubuntu 9.1 doesnt boot up. Grub rescue command"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by adam123 on 2010-04-11
Greetings Ladies and Gentlemen:
I decided to install Ubuntu 9.1 on new system.  I downloaded ISO file on hard drive and burned the image on CD.  I run Ubuntu on new PC from CD without problems.  Then I installed it on blank hard drive.  Installation went without any problems. I removed a CD. Then I went for a restart.  However Ubuntu doesnt boots up.  Instead, I am in command line just after the boot up with the following message:
Crub loading.
error: out of disk.
grub rescue>

Note that my hard drive capacity is 325 GB.  Ubuntu took about 4GB of space the rest is free space.
What I am doing wrong?
How do I fix it?
I can access hard drive and its contents from live CD.
I am completely a greenhorn on Linux.  I appreciate your guidance.
Thank you for your time.
Adam:confused:

---

### Post by dstew on 2010-04-12
The most straightforward thing to do is [re-install grub from a Live CD boot]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). It is possible -- maybe -- to [re-configure grub from the grub-rescue prompt]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode"), but it is a bit harder. If you want to try using the grub-rescue prompt, you will need to find the installed Ubuntu partition using the **ls** command, load the linux kernel using the **linux** command, and the **initrd** file using the initrd command. Then issue the **boot** command. If all goes well, and you have re-entered your hard-disk Ubuntu system, you can re-install grub permanently using **sudo grub-install /dev/sda**

---

### Post by oldfred on 2010-04-13
More info on solution to out of disk error:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

