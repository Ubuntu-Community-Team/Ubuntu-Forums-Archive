---
title: "Move 10.04 to on top of 8.04?"
date: 2011-02-24
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2011-02-24
Can this be done?

My 3 year old Hardy partition is just how I like it, except for Hardy. I put 10.04 on another partition, slave drive, and I've got it customized for permanent.

Can I move the System files in place of the Hardy System files, and retain my personal data?

---

### Post by tommcd on 2011-02-25
> **Moozillaaa said:**
> 
My 3 year old Hardy partition is just how I like it, except for Hardy. I put 10.04 on another partition, slave drive, and I've got it customized for permanent.

Can I move the System files in place of the Hardy System files, and retain my personal data?
First off, you should have a separate home partition for your data. If you have a separate home partiton already, then you have nothing to fear!!!
 With a separate home partition all of your data would be safe on a separate partition. 
With a separate home partition there would never be any need to even contemplate this question.

I would think that the best option would be to backup your data and do a clean install of 10.04. This would also be a good opportunity to create a separate home partition if you do not already have one.
If you are balking at this, then you are fighting an uphill battle. If you want to continue using linux, you will have a separate home partition at some point. It is inevitable. You may as well learn to do it *now*!!!!

Your next best option would be to do a dist-upgrade from 8.04 to 10.04. You have already verified that 10.04 works for you, so (hopefully!!!) a dist-upgrade to 10.04 should go well.
I hope that you are not one of those people that feels compelled to install a bunch of 3rd party repos on their system. This includes those all too problematic PPA repos that cause so many problems around here.

I prefer to always do clean installs of each Ubuntu version. It is the simplest way to avoid problems with upgrading.

---

### Post by Moozillaaa on 2011-02-25
(ed.: can you take a look [here](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/) tommcd, and see if this procedure is close?

I don't think that a separate /home would solve the customizations that I want to preserve.

So the answer is 'Yes, it can be done' (maybe FF, power schemes, and window appearances can or cannot be saved - let's try tho'), and what better way to learn the nuts and bolts, than to transfer new OS files into an old install! :D

Question IS, how to do this?

1) Back up personal data. Done

2) Boot up a Live environment. 

3) Help?

---

### Post by tommcd on 2011-02-25
> **Moozillaaa said:**
> (ed.: can you take a look [here](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/) tommcd, and see if this procedure is close?

Something like that might work. I did not know exactly what system files you wanted to copy over.
I think that something like that is only worth it if you have a lot of users on your system.
Also, with a separate home partition, all of your user specific configuration files and folders (those that start with a period) in your home directory would be preserved when you upgrade Ubuntu.
Otherwise, if you replace the config files in the new home directory in 10.04 with the config files from the old home in 8.04, then all of your settings from 8.04 should transfer to 10.04. I would backup the files on 10.04 before doing this though, in case something goes wrong. 
As for Firefox, if you copy the .mozilla directory from 8.04 to 10.04, then your Firefox settings from 8.04 will transfer to 10.04. Likewise, I would backup the .mozilla in 10.04 before proceeding.

---

