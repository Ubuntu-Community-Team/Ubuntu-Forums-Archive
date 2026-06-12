---
title: "After installing Ubuntu 16.04 LTS - How to get to the Home window with the icons?"
date: 2016-08-05
forum: Installation &amp; Upgrades
---

### Post by philo4 on 2016-08-05
Hi everyone,
Ubuntu 16.04 LTS is now installed.  As a novice in IT, that is already an achievement.  How to now get to the Home window with the icons which gives access to softwares and the internet? [What to write after the Dollar sign?]  At this stage, the screen only shows:


Ubuntu 16.04.1 LTS philo-laptop tty1

philo-laptop login: philo
Pasword:
last login: Thu Aug 5 13:19:48 GMT 2016 on tty1
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 3.13.0-0-92-generic i686)

* Documentation: https:.............................................
* Management:    https:.............................................
* Support:           https:.............................................
[EMAIL="philo@philo-laptop:~$"]philo@philo-laptop:~$[/EMAIL]

What to write after the Dollar sign?

Many thank for your help and support!

Philo

---

### Post by ajgreeny on 2016-08-05
> Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 3.13.0-0-92-generic i686)That is a little confusing unless you have upgraded from 14.04 to 16.04 as the kernel shown is a 14.04 version, not normally seen in 16.04.

What is your hardware?

---

### Post by grahammechanical on 2016-08-05
> How to now get to the Home window with the icons which gives access to softwares and the internet?

There is no access to icons that will load applications when we use the command line. Which is where we are when we open the terminal or a Linux console (tty1). Is this a server edition? The server edition does not have desktop applications that have a graphical user interface. The server edition does not have a Desktop Environment.

If this is Ubuntu 16.04 desktop edition. There should be a launcher on the left hand side of the screen. That will have some icons for applications put there by default. My advice would be for you to pull down the power/cog menu that we use to shut down Ubuntu and select Ubuntu Help and read about the Ubuntu user interface. All you need to know is there.

It comes into my mind that this is Ubuntu 16.04 desktop edition but it is not loading to a desktop and instead it is only loading to a Linux command prompt. 

Regards.

---

### Post by philo4 on 2016-08-05
Hi ajgreeny,  many thanks for your reply.

Exactly, that is it.  Two days ago, the computer was working really well with Ubuntu 14.04.  An option came up the screen to upgrade to 16.04.  Since upgrading, if the option 'Advanced options for Ubuntu' is selected in GNU GRUB version 2.02~beta2-9ubuntu1.11, I managed to get to the information provided in my first message after opting for 'Ubuntu, with Linux 3.13.0-92-generic (recovery mode)'
If I let the computer chooses automatically the option 'Ubuntu', it displays  " end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) "

---

### Post by philo4 on 2016-08-05
Hi grahammechanical,
Since upgrading from 14.04 to 16.04 two days ago, all icons for applications have disappeared, and there is only that black Terminal page with:
- Either the information provided in my first message comes up the screen after I have opted for 'Advanced options for Ubuntu' is selected in GNU GRUB version 2.02~beta2-9ubuntu1.11, and then 'Ubuntu, with Linux 3.13.0-92-generic (recovery mode)'
- Or the computer chooses automatically the option 'Ubuntu', and then it displays: " end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0) "

---

### Post by ajgreeny on 2016-08-06
I doubt that I can give you a real answer but it may be worth trying to run fsck on the root partition of your system.

Boot to a live DVD/USB and from that run ```
sudo e2fsck /dev/sdx#
``` where sdx# is your root partition; it is possible that you may have a corrupt filesystem in some way which the system check will put right.

I have never upgraded my OS version, preferring a clean install, so I have no experience of the possible problems of doing an upgrade, but the one time that I had a kernel panic, a long time ago now, fsck sorted it for me.

---

### Post by philo4 on 2016-08-09
Hi ajgreeny,
Thank you for your suggestion.
Anything tried so far with or without Live USB downloaded from the internet has not shown any real satisfaction.
As a result, this led me to carry out a lot of search online, before realizing so many people have encountered electronic crisis and paralysis because of 16.04 LTS.
A call to Canonical in London did not bring any solution either.
 These have been 5 days without access to my data...
Any further suggestion?
Many thanks in advance
Philo

---

### Post by ajgreeny on 2016-08-09
It occurs to me that we know nothing of your hardware and I am wondering if you have too low a spec of machine to successfully run Ubuntu with the unity desktop.

Have you tried running a live system of Ubuntu and also the other less resource-hungry versions such as Xubuntu or Lubuntu?  It might be as simple as that.

---

### Post by philo4 on 2016-08-11
Toshiba Satellite L300 with a hard drive of 320 GB

---

### Post by philo4 on 2016-08-20
Dear Ajgreeny,
Your contributions have  been highly appreciated.  Suddenly, it gave a sense of one not being  left on one's own in a technological island. 
As the computer has  refused so far to boot on the Live USB, CDROM, Boot Repair Kit,...,  hopefully I will come across in person with a Linux user for whom this  challenge will be a simple game.
Once again, many thanks ! 
Philo

---

