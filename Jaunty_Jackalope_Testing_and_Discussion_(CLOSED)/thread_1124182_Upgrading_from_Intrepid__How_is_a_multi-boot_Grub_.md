---
title: "Upgrading from Intrepid:  How is a multi-boot Grub handled?"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bobnutfield on 2009-04-13
Hello Everyone,

I just finished wiping my desktop hard drive and installing Jaunty, having tested in on my netbook now for about a month.  It is by far the best release of Ubuntu I have ever used.  It will now be my main workhorse on all my computers, but before I do the upgrade on my main laptop. I was wondering if anyone has upgraded Intrepid on a machine that multi-boots and if so, how are the other OS's handled on the new installation of Grub.  My main laptop multi-boots with Fedora and Slackware, and I want to keep them intact as I use them as well for different tasks.  Ubuntu is on sda1 and sda2, Fedora is on sda3 and sda4 and Slackware is on an extended partition, sda5 and sda 6 (I use a separate partition for /home on each.)

My question is:  will the new installation of Grub during the upgrade automatically recognize the other OS's and install accordingly, or will I need to make a backup of Grub and edit the new Grub manually?

If there is a Grub command that anyone knows of that will do this for me (rather than manually edit), that would be nice, too.  But it is no big thing if I have to edit.

Thanks for any replies

---

### Post by markbuntu on 2009-04-13
Are you chainloading Fedora and Slackware?
If so you should not have a problem and if you do you can just put the chainload lines back in the new grub menu.lst.

---

### Post by bobnutfield on 2009-04-14
> **markbuntu said:**
> Are you chainloading Fedora and Slackware?
If so you should not have a problem and if you do you can just put the chainload lines back in the new grub menu.lst.

Thanks for the replay...didn't think this one was such a tough questioin, but yours is the only reply.  No, I am not chainloading them.  I have their boot entries below the *******End of Debian Kernels****** line with full boot kernel entries.  It really isn't a big deal, I guess, becuase I can manually re-enter them, but I was just wondering if an upgrade kept the original boot entries in Grub intact or if wiped them for a new grub installation

Thanks again.

---

### Post by Seventh Reign on 2009-04-14
Just save a copy of your current menu.lst file.  Your current Grub menu shouldnt be effected at all, but I've learned that linux and grub can be .. unpredictable at times.  If it is effected just run the live CD and copy & paste the entries for your other OS's into the new menu.lst.  As long as your drives havent changed you shouldnt need to modify anything else.

---

