---
title: "Ubuntu 10.4 LTS installation error"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by brickhead248 on 2010-06-12
Hey Ubuntu Forum,
I've been having the same problems installing 10.4 LTS (i386) on two machines, both 32-bit Athlons. I get the error:

"the installer has encountered an unrecoverable error. A desktop session will now be run etc.....".

I've had a look around on a few other posts where the error occurred on the RC version, and the suggestion is to run the alternate version for the RC, but that seems to be unavailable. Is there an alternate LTS? would that get around this error? what the hell is this error anyway?

thanks

---

### Post by brickhead248 on 2010-06-12
I probably should have mentioned that i get all kinds of crazy errors when i try to install from the desktop.

first it fails to create the ext4 files system (ill admit, that might be more my hard drive), 
then it tells me that "ubi-migrationassistant crashed with exit code 141..."
but if i decide to skip this step and install anyway, it goes straight back to the "who are you" section of the installation.

clearly the installer does not work on my machine.

what do it do?

---

### Post by eggdeng on 2010-06-12
You can download the alternate install cd from [http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")
You want the PC (Intel x86) alternate install CD
It won't do much good though if your HD is bad. I would wipe it first with Gparted and just go with the default partitioning on install.

---

### Post by brickhead248 on 2010-06-13
Thanks, i installed the alternate version, and it worked until it tried to boot.

what does it mean when i get an initramfs prompt?

---

### Post by 10dollarNOOBIE on 2010-06-13
Hi there! i just wanna ask how can i remove 9.10 boot loader "leftover" in my boot menu. i uninstall ubuntu 9.10 properly using wubi coz i want to try 10.04, now my only problem is how can i remove 9.10 in my boot menu, i saw some threads that vista cd is needed, how can remove it without using my vista cd to repair it coz i dont know where is it now. Is there other ways to get rid of it? Kindly put some step by step instruction for me, im a noobie linux user but im starting to love this os <3.[ATTACH]160248[/ATTACH][IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

thanks in advance .[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by brickhead248 on 2010-06-13
> **10dollarNOOBIE said:**
> Hi there! i just wanna ask how can i remove 9.10 boot loader "leftover" in my boot menu. i uninstall ubuntu 9.10 properly using wubi coz i want to try 10.04, now my only problem is how can i remove 9.10 in my boot menu, i saw some threads that vista cd is needed, how can remove it without using my vista cd to repair it coz i dont know where is it now. Is there other ways to get rid of it? Kindly put some step by step instruction for me, im a noobie linux user but im starting to love this os <3.[ATTACH]160248[/ATTACH][IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

thanks in advance .[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

theres a whole bunch of tutorials like this that can guide you through changing the grub boot menu, i just cant remember them.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

you might get more help if you start a new thread.


also, i think ill start a new thread because THIS problem is solved, but i've  run into another problem.

---

