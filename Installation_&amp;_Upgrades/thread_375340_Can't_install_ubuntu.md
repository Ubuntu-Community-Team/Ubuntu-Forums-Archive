---
title: "Can't install ubuntu"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-03-03
I just built myself a new computer with a DP965LT mobo and 2 ghz intel core 2 duo with a 400 gb hard drive and 2 gb ram.  And for some reason whenever i boot up linux from the live cd i get these error messages:

[     46.215450] PCI: Failed to allocate mem resource #6:20000090000000 for 0000:01:00.0

then it says type help for some list of commands and then this error message:

/Bin/sh: can't access tty;  job control turned off

i would really appreciate any help that could be given to me i have windows XP home up and running with all of the drivers installed and everything working perfectly.

thanks for the input

---

### Post by invalid on 2007-03-03
Try running a memtest and see what happens.

Also, you may want to subscrube to the numerous other threads with similar problems: 
[http://ubuntuforums.org/showthread.php?t=244817](http://ubuntuforums.org/showthread.php?t=244817)

---

### Post by Opeth115 on 2007-03-03
ok well i tried the memtest and it passed with flying colors 12 times...lol  anyone have any ideas of how i can get ubuntu installe don my system?

---

### Post by Kateikyoushi on 2007-03-04
The sata controller. A bug report was filled already concerning this. [LINK]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964")

---

### Post by Opeth115 on 2007-03-04
grr this is really frustrating is there any way id be able to install an earlier version or does anyone know of a distro that might work because i tried fedora and it did basically that same thing...

---

### Post by Kateikyoushi on 2007-03-04
Earlier versions won't work later ones will.

> I succeeded in booting by adding irqpoll to the boot options of the 2.6.20-9 kernel. (as suggested in duplicate #78288 of the bug)

So it might work if you try feisty herd 5 with the irqpoll option.

---

### Post by Opeth115 on 2007-03-04
how would i go about adding that option since i can't even boot into the live cd?

---

### Post by Kateikyoushi on 2007-03-04
He must have been able to boot the feisty live disc but the installer stopped which he solved by using the boot option.

---

### Post by Opeth115 on 2007-03-04
ok well im downloading the feist fawn iso and ill brun it to a cd and give it a test ill come back after to say if it worked or not...

---

### Post by Opeth115 on 2007-03-10
Ok well i downloaded many different distros,,, Sabayon, Knoppix, OPENSuse, and numerous others all to fail on me.  The only one i can get to boot is the feisty fawn live cd but every time after i try to create the partition the installer freezes on me i tried the irqpoll option but it continues to do the same thing i have been searching for days now to find a solution to this with no avail.  Maybe i put the irqpoll option in wrong could somebody give me a sorta tut. on adding boot options?  Or any other ideas that might help me get this installed on my new computer?

---

### Post by Opeth115 on 2007-03-11
Anyone have anything to help me with?

---

### Post by Kateikyoushi on 2007-03-11
It is in the hand of the kernel developers.

The last post on launchpad states that debian worked for him with the same chipset. [LINK]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84964/comments/52")
A pity he forgot to mention which version.

---

