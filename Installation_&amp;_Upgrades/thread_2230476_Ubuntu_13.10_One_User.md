---
title: "Ubuntu 13.10 One User?"
date: 2014-06-19
forum: Installation &amp; Upgrades
---

### Post by Matthew_Smith on 2014-06-19
Hi all,

I've been wondering: Can you install Ubuntu, or set it up, in such a way that Ubuntu is installed on both users' accounts, but only one shows the grub selection menu on startup?
I'm sure there is a way to make the computer auto log-in on a user's account on startup... (normally it asks which user to log in onto) and then have grub on that user's account and change the auto log-in to the other account if needed. I am currently running Windows 8 64-bit and have a 16Gb SD card for the installation. If you need any more info then feel free to ask me in a reply ;). 

Thank You,
Matthew Smith

P.S: Once, I used the SD card for the installation, didn't complete it, and rebooted into Windows 7 (yes, I said 7...) and didn't have ANY internet connection. Did I do something wrong? Will it be fine on Windows 8? Again, If you need need more info feel free to ask!

---

### Post by mörgæs on 2014-06-19
Grub executes before the operative system. The user is defined within the operative system. Hence, the same Grub menu is shown everyone.

By the way, 13.10 is out of support in a month. Better to install 14.04.

---

### Post by ajgreeny on 2014-06-19
You have confused me totally!
You don't install Ubuntu on users' accounts; you install Ubuntu with a primary first user set up at the installation time and then after booting onto the installed OS you can add another user, or as many users as you want.

I don't think it is possible to only show the grub menu for one user and not the other as grub executes long before any user or OS files are available.  All grub does is quickly tell the computer which OS to boot, so grub knows nothing about the users on the machine.

You are correct in saying that you can choose to autologin a user from those users set up on the machine, but that has nothing to do with grub, and it will not help you either. With autologin set, your computer will login to that chosen user with no chance for you to change user except by logging out again, which will then show you the users in the login screen, which does appear after logging out but not from a cold boot.

I can't help with your other network connection, I'm afraid.

---

### Post by Matthew_Smith on 2014-06-19
Shame. Oh well, thanks!
MODERATORS: Close Thread.

Thank You,
Matthew Smith

Thank you! Sorry my post wasn't clear enough...

---

### Post by mörgæs on 2014-06-19
We don't close a thread but please mark it 'solved' using 'thread tools'.

---

