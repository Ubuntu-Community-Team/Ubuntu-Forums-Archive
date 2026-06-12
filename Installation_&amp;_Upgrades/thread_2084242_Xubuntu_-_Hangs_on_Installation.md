---
title: "Xubuntu - Hangs on Installation"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2012-11-14
Xubuntu 12.10

I have seen that a lot of people are having this problem.  The installer starts, allows you to partition your HD, and then won't go past the part where it asks you your location on the globe.  

You can click on "Next", the installation line finishes, and then it just sits there, doing nothing, like uncle after dinner when a football game is on.

I did fortunately figure out a solution.

The reason it sits there, is because the changes to the partition never took place, as Xubuntu has not "unmounted" your HD.

Boot up the Live CD (say "try Xubuntu" on initial boot).  You will see your HD on the desktop.  Right click on it, and unmount it.  (There may be more than one of your HD on the desktop, if one is unmounted, make sure the other is too.)

After this drive is actually unmounted, you can then proceed with the installation, partitioning, and so on.

I had one discrepancy.  The installation finishes, but doesn't close the install window letting you know it's done.  Wait until the status bar is completely filled to the end, and then restart your computer.

Then just reboot and viola!  

*Sidenote:  I have noticed that Ubuntu, Ubuntu GR, and Kubuntu also hang for a bit during installation.  Could they have the same problem, but eventually unmount the drives automatically?*

This was a solution for me.  If this is a solution for others, please say that it was so I can mark this solved.

---

### Post by Bucky Ball on 2012-11-14
All good but you have omitted to mention the release you are using. V important.  I am presuming it is 12.10.

---

### Post by Shibblet on 2012-11-15
> **Bucky Ball said:**
> All good but you have omitted to mention the release you are using. V important.  I am presuming it is 12.10.

It is.  I apologize.  I will make an edit.

---

