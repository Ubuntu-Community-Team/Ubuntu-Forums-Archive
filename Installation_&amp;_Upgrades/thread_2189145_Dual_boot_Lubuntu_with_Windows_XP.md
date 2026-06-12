---
title: "Dual boot Lubuntu with Windows XP"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by rafranz56 on 2013-11-20
Good evening everyone.  I have done 1 straight install of Lubuntu from live CD with success.  I would like to do another install from live CD alongside Windows XP on my laptop.  When I get to the part where it asks me where I want to install Lubuntu there is no option to install alongside Windows XP.  This option appeared to be available on earlier versions. The only options appear to write over Windows XP. Are there any ideas?  I have Lubuntu 13.10. I apologize if this question was previously answered.

---

### Post by papibe on 2013-11-20
Hi rafranz56. Welcome to the forum ):P

You may need to shrink your XP partition first to make space for Lubuntu. It is recommended to use Windows tools to do that, but you can use Gparted which is available when you choose 'Try Lubuntu wihout installing it'.

Note that if you are going to to do it with Gparted, I'd advice these steps:
[LIST]
[*]Within XP defrag your disk.
[*]Restart.
[*]Defrag your disk again.
[*]Use the Lubuntu media installation to shrink your partition.
[*]Restart and make sure your XP system work with a smaller partition.
[*]If everything goes well, next time you try to install Lubuntu, I believe the option 'along side' will be offered now.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.: don't forget to backup your important data before any of this ;)

---

