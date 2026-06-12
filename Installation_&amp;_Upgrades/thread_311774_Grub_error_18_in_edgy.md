---
title: "Grub error 18 in edgy"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by cpanaccione on 2006-12-03
Tried installing 6.1 on  a separate hd from winxp. Everything went well, but when grub loaded, I got error 18. How do I fix this? Complete linux newbie, and maybe average experience in windows, but am committed to becoming part of open source community.

---

### Post by Herman on 2006-12-04
Hello cpanaccione,
Here's a link with a little bit of info on your error,
Grub error 18.......................................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18")

So, how large is this new hard disk, and how old is your computer?
Will it help if you resize the partition smaller, to within the 137 GB BIOS limit?
I recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") for working with partitions.

Regards, Herman :D

---

### Post by cpanaccione on 2006-12-04
Hello Herman,

Thanks much, updating bios did the trick. Question: upon booting, I get about 4 Ubuntu choices, plus xp. Is that normal?

Really appreciate your help with the grub error.

Many thanks, Chris

---

### Post by bulldog on 2006-12-04
Then you have two different kernels installed,and yes that's rather common.

And a memtest entry as well.

---

### Post by Herman on 2006-12-05
>  Thanks much, updating bios did the trick. Question: upon booting, I get about 4 Ubuntu choices, plus xp. Is that normal? Thank you for your feedback too, cpanaccione, it enables me to improve the site for others in the future who may have the same error message.

I agree with bulldog, it is perfectly normal to have two lines for Ubuntu in our Grub menus, plus memtest86+. 
The top line is the normal Ubuntu boot, second line is rescue mode, and the third is for testing your RAM.
When new kernels are received during an update those also will be added to your list in your Grub menu. That's just a precaution is case a certain kernel might come out that might not suit certain machines. If you ever notice a problem you suspect might be related to a new kernel you received, you can just boot the older kernel instead. I have never had any problems like that or even read of any. 
I used to just delete the extra entries in my menu.lst file but leave the old kernels in place. If I ever needed to, I could boot them manually from Grub's Command Line. 
Now I edit my automagic kernels list in my menu.lst file so that the old kernels entries are automagically deleted from my list.
(I have read that some people uninstall thier old kernels with Synaptic Package Manager, but I don't think that's necessary). 
Here's a page about how to customize your Grub menu and lots of other neat things you can do with Grub, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm").

Regards, Herman :D

---

