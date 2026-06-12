---
title: "Reintroducing windows into a linux-only system."
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by Sutur on 2006-12-05
Hello, I am running Edgy Eft.

I recently found that dispite my best efforts, certain areas of my interest cannot be satisfied by linux alone, and I have decided to go back to a dual boot scenario with Windows on a small partition.

I just wanted to confirm the following steps were correct:

1. Backup data on the soon-to-be wiped partition.
2. Back up grub to a floppy disk.
3. Install Windows XP, destroying grub.
4. Restore grub as the primary boot loader.
5. Integrate the Windows kernel into grub.

However, I am stuck on these steps:

2. Despite my research is proving to be rather problematic. I can't seem to make a floppy that will boot linux the same way grub currently does, it presents the options when booting, but when I go to select one of them, it gives me an error and nothing loads.

4. Again, stuck on this one despite having read "info grub", "man grub", and various tutorials on google.

5. This is something the Ubuntu installer already configured for me and I am unable to figure out how to use it.

I am tempted to use LILO since it did it's job properly, was easy to install, easy to back up and easy to configure. But it appears Grub is a lot more popular, for reasons I can't fathom.

Any help would be greatly appreciated,

Hal.

---

### Post by Joe_CoT on 2006-12-05
[http://help.ubuntu.com](http://help.ubuntu.com) has a multitude of how-tos and explanations covering these sort of issues.

Here's a how-to about grub in general:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

And here's a how-to about recovering grub after installing windows:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have any problems that the community docs don't cover, feel free to post back and we'll help you out :-D

---

