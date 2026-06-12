---
title: "DualBoot, Ubuntu booting error"
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by Carlos_Portela on 2015-02-18
Hi,

I installed Ubuntu 14.04.1 LTS on a Computer that had only Windows 7 and now I am having an error booting Ubuntu. When I select in the Grub to boot Windows, it works nice.. but Ubuntu seems to have an error. 

Error:
[IMG]http://i.imgur.com/53UT2cB.jpg [/IMG]

The laptop is a Lenovo ThinkPad L440.

Thank you for the help :)

Regards

---

### Post by oldfred on 2015-02-19
What video card/chip do you have?
Have you tried booting recovery mode, or second Ubuntu line?

May need boot option for video or other hardware issue.

---

### Post by Carlos_Portela on 2015-02-19
Hey, thank you by the help. I just reinstalled ubuntu because I had only root and swap partition. This time, I added the home partition and seems to be working fine now :) I thought the home partition wouldn't be needed to create. Am I wrong about it?

---

### Post by oldfred on 2015-02-19
While you should not have to create a /home, I often suggest it just so / (root) is smaller & more efficient. 
But I still have a smallish / of 25GB with about 11GB used including /home, but then use a /mnt/data partition for all my data and link the standard folders back into /home. So /home only really has the user settings which then are less than .5GB. But setting up a data partition is more advanced as you have to set ownership, permissions & edit mount in fstab, all manually.

---

### Post by kc1di on 2015-02-19
you don't need a /home partition normally but if your /root partition is not big enough it can cause that problem.

---

### Post by Carlos_Portela on 2015-02-19
Well, I did it this way:
[IMG]http://i.imgur.com/LDDmkMU.jpg[/IMG]

I did it this way, what do you think? Is it fine or should I try to reinstall everything with root only again ?

---

### Post by oldfred on 2015-02-19
What you have is fine.

The only other suggestion is if you use both systems a lot and have some data you want in both like Firefox or Thunderbird profiles or music etc. Then better to only set Windows system partition as read only and have a read/write shared NTFS data partition. But you still cannot hibernate Windows without issues as it does not seem to unmount a partition.

---

