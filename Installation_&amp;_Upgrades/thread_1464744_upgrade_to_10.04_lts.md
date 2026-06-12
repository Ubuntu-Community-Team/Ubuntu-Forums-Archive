---
title: "upgrade to 10.04 lts"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by shipinomore@gmail.com on 2010-04-28
I installed Ubuntu 9.10 and then turned around and did the Alt F2 and did the upgrade to 10.04 LTS.
all went well until at 3 min to go it hung up with a window to continue without installing GRUB.
would not proceed after waiting a very long time so checked the box and now cannot log in as the keyboard is out due to the system is waiting for me to log in and will not accept my passord.
any ideas of what to do with this other than "we told u so"
this thing will not allow you to even get into the installe version.
Larry

---

### Post by kenni on 2010-04-30
> **shipinomore@gmail.com said:**
> I installed Ubuntu 9.10 and then turned around and did the Alt F2 and did the upgrade to 10.04 LTS.
all went well until at 3 min to go it hung up with a window to continue without installing GRUB.
would not proceed after waiting a very long time

I'm seeing the exact same behaviour...the upgrade process stalls at the "Continue without installing GRUB" window and clicking "Forward" has no effect. We're not the first ones who have this problem, the following guide also mentions the problem:
[http://www.howtoforge.com/how-to-upgrade-ubuntu-9.10-karmic-koala-to-10.04-lucid-lynx-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-9.10-karmic-koala-to-10.04-lucid-lynx-desktop-and-server)

I'm on Mythbuntu 9.10, I did a upgrade of all 9.10 packages and booted into the new kernel before initiating the upgrade to 10.04. This seems to be a bug in 10.04.

---

### Post by pavera on 2010-04-30
I think its definitely an issue in 10.04, cause I tried the upgrade and had the same problem (couldn't complete install without telling it not to install grub, then no keyboard at login screen after boot)

I then did a clean install, and still had the same issue with the keyboard at the login screen.  The keyboard just appears to not be connected at all.  However, if I boot into single user mode, the keyboard does work, and it works in the bios, so I know the keyboard is functional...

---

### Post by kenni on 2010-04-30
I selected not to install grub and thereby keeping the old bootloader. Just like in the guide I posted above, I had no problems booting afterwards. Perhaps because I don't need any fancy modules? (I'm really not into the Ubuntu boot process).

If I try to run "dpkg-reconfigure grub-pc" after booting into 10.04, I once again get a similar question "Continue without installing GRUB? Yes/No" - This time just in the terminal. Selecting "No" asks me the same question again and again without any error message, eg. this time I can also only continue by selecting "Yes" to not installing GRUB.

---

