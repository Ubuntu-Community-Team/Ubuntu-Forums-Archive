---
title: "Dual boot with Seperate HDD."
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by Gambit690 on 2010-06-15
[SIZE=4]Hi Everyone,[/SIZE]

[SIZE=4]I have 2 sata HDD, I wish to dual boot, but in a way to have Windows on one and Ubuntu on the other.

For some reason I could not get Ubuntu (10.04) to install from the live CD or Wubi or from Windows on the same HDD. 

I downloaded the advanced distro and went with that straight onto the HDD and it has been a gem (love how it just works with no drama).

I want to install windows XP again on the 2nd HDD, as there is one game that I play in windows. (I've got it to work in Wine I just don't like / can't get used to it)

My Question is: Can I please get some suggestions / instruction on installing windows on a 2nd HDD and then being able to choose which one to boot.

I've read about installing Windows after Linux in the user guide and reinstalling grub2 - I got the impression though, the they were installed on the same HDD and thought that what I want to achieve may differ?

All help is greatly appreciated.

Mat. ( Linux Noob - please be gentle, It's my first time).


[/SIZE]

---

### Post by Mark Phelps on 2010-06-15
What has worked best for me is to have MS Windows on its own drive and Ubuntu on a separate drive.

To do this, you will need to install XP on a drive with only that drive connected.  Make sure the Ubuntu drive is not connected when you do this install.  Of course, you will need to be able to boot from an XP install CD to do this.

Then, reconnect the Ubuntu drive, boot from it, open a terminal and enter "sudo update-grub".  This will autogenerate a new GRUB menu which will contain an entry for XP as well.

Then, when you reboot from the Ubuntu drive, you will get a menu.

---

### Post by Gambit690 on 2010-06-15
Awesome, 

Thanks heaps Mark, I'll do that today and let you know how I get on.

Coffee first me thinketh.

Mat.

---

