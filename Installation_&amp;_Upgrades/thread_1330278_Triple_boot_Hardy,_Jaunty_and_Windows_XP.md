---
title: "Triple boot: Hardy, Jaunty and Windows XP?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by iniesta on 2009-11-18
Hi guys, 

My computer currently has Jaunty and Windows XP installed. My hard disk partitioning is as follow:

+ /dev/sda1: Ubuntu 8.04
+ /dev/sda2: Linux Swap
+ /dev/sda3: Windows XP
+ unallocated: ~50GB

And now I want to install Ubuntu 9.10 on the unallocated space. To do so, I intend to choose the option "Use the largest continuous free space" in the Hard disk partitioning stage of the installation process. Is that ok?

Thanks and regards,

Iniesta.

---

### Post by darkod on 2009-11-18
Yes, or if you prefer to create the partitions manually. It gives you more control.

---

### Post by iniesta on 2009-11-18
> **darkod said:**
> Yes, or if you prefer to create the partitions manually. It gives you more control.

Hi darkod, 

Thank you very much for your answer. Since I'm a newbie I think I should not manually create the partitions (maybe I will choose this option when I become a pro :D).

Well, I have another question: If I choose the option "Use the largest continuous free space", then the Jaunty's installation will create another Linux Swap partition or it will share the old one with Hardy?

Thank again.

Iniesta.

---

### Post by darkod on 2009-11-18
Don't know, never used it. :) And I'm fairly new to linux myself.
Don't be afraid from manually creating partitions, it's only one click with the mouse. I don't use automatic options just because I want control which partitions to create and what size.
Also, I never installed two ubuntu OS on the same pc, you are right asking about swap because you can probably use the same swap partition. After all, you will be able to run only one ubuntu at a time.

---

### Post by raymondh on 2009-11-18
> **iniesta said:**
> 

Well, I have another question: If I choose the option "Use the largest continuous free space", then the Jaunty's installation will create another Linux Swap partition or it will share the old one with Hardy?


It may and if it does, it will create an extended partition to house both jaunty root and swap. 

It may also pick-up/see your existing swap and mount it to jaunty.

If you decide to go manual and create partitions beforehand .....

1.  Use a  jaunty liveCD and in live session access gparted (system > admin > partition editor)
2.  Live session ought to unmount existing partitions.  2-check by rt. click on each partition and if given the option unmount, do so.  For swap, use swapoff.
3.  Identify and rt. clk. to highlight the unallocated space.
4.  Select NEW and FORMAT to your preference (ext3 or ext4).  Review and APPLY.
5.  Exit gparted and proceed with the install.
6.  In step 4 of the installation process, select MANUAL
7.  Click to Highlight the intended (newly created partition) and select EDIT > USE AS > select MOUNTPOINT which will be root (/) > File Format (ext3 or ext4) > FORMAT
8.  Click to highlight your existing SWAP and EDIT > USE AS > Linux Swap file > DO NOT FORMAT  (you just want to mount it for Jaunty as well)

If you're not comfortable with manual install .... use the 'largest continuous' and we can go from there. :)

Regards

---

### Post by iniesta on 2009-11-18
Hi raymondhenson,

Thank you for your detailed instructions. Perhaps I should try the manual option ;)

Regards,

Iniesta

---

### Post by raymondh on 2009-11-18
> **iniesta said:**
> Hi raymondhenson,

Thank you for your detailed instructions. Perhaps I should try the manual option ;)

Regards,

Iniesta

It all depends on your comfort level.  Either way will work.  Remember that during the install process, you can always quit out until step 7.

If this is for a production/main system and you feel uncomfortable, I suggest you try it on a test machine first should you have one.  Also, if you decide to create partitions beforehand, you can also consider separating /home from root (/).  It will be the same process except you will now make 2 partitions (one for root and another for /home).  15gb for root is plenty.  The rest can go to /home.  Post back if you want to do this and need a guide that includes /home.

Nevertheless, as the old/usual saying goes ...... "always have a working back-up before using any partitioning tool" ;)

Happy Ubuntu-ing :)

---

