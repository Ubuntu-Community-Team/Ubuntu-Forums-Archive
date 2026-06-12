---
title: "ubuntu server 22.04.4 &quot;apt upgrade: breaks boot"
date: 2024-04-19
forum: Installation &amp; Upgrades
---

### Post by granthjones on 2024-04-19
First off I'm a newbe.  I just got back from out of town for a week and went through "apt update" then "apt upgrade."  I was(am) on 22.04.4 LTS @ 5.15.0-102-generic.  After running "apt upgrade" the system fails on boot.  I've looked at grub a bit but I really don't have any experience.  One error I do see is Invalid Magic Number, you need to load the kernel first.  In the options in the grub menu after the boot fails if I choose the earlier version (102) and not 105 it will boot.  Where should I go from here?  What should I look for?  I would expect others are seeing this.  This is a clean install on a dedicated machine, no dual-boot.  I restore my HDD image of 22.04.4 102 and it boots fine.  Thanks in advance for your feedback.

---

### Post by MAFoElffen on 2024-04-20
Magic Number has to do with filesystem and disk errors.

Do you have good backups? As another member has this quote in their signature line, "Backups are not sexy, until (after) you need them." So true.

fsck...

---

### Post by granthjones on 2024-04-20
Yea, I've got a good backup, restored it many times then upgrade breaks it every time.  I saw that Magic # & FS & disk errors but I can re-install the image and everything works fine.  I'm betting it has something to do with the kernel upgrade, breaking grub, I ran that boot repair util to no avail, I'm too just thinking about a reinstall...

---

### Post by granthjones on 2024-04-20
FIXED.  Bizarre.  So I think what my problem may have been is I was too impatient and was rebooting before a service was complete.  Still running after I got the # prompt.  Just a long-shot!  This time I got called away to dinner and it sat quite a bit longer at the # prompt and when I came back and rebooted it it came to life.   :)

---

### Post by MAFoElffen on 2024-04-21
Good deal that is corrected itself! Happy it works now.

We are responsible for Marking our own Threads we open as Solved when we feel it is. Please use the "Thread ztools" link in the upper right of the page. to mark it as "Solved".

---

