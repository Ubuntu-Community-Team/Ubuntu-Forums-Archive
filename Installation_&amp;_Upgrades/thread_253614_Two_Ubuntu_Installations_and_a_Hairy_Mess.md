---
title: "Two Ubuntu Installations and a Hairy Mess"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by bumblebeef on 2006-09-08
Hi,

I'm not *too* computer-savvy, so please bear with my improper computer terminology and general ignorance.

For about eight months I had my Inspiron 1100 dual-booting Windows XP and Ubuntu, and it did so nicely until sometime earlier this week. I'm not entirely sure what happened, but XP freaked out on me and somehow managed to wipe out the computer's boot file. I've since deleted XP completely off of my computer, but the only way I've gotten Ubuntu 6.06 working again was by partitioning my computer and re-installing 5.10 off of an old CD I had. 

So right now I've got two different versions of Ubuntu on my computer. All of my data has been preserved in the 6.06 installation. I want to get rid of 5.10, but I can't seem to do this because the Grub boot information is stored within the 5.10 installation, and when I get rid of that, Grub disappears and I can't access 6.06. I've made a little bit of a mess, in short.

Is there any way I can change the Grub information so that my computer will by default boot into 6.06? And after I get this accomplished, is there any way I can delete 5.10 and not have to worry about it messing with the Grub?

I appreciate any help on this, and I know it's quite a mess. Just let me know what information you need (how to get it might help, too), and I'll be more than happy to get it for you. I'm loving 6.06, and I'd like to continue using it without too much trouble.

Thanks!

---

### Post by daller on 2006-09-08
It seems like you have the 2 versions installed on different partitions!

Simply upgrade your 5.10 to a 6.06? (and then remove the other 6.06?)

Or what is the problem?

---

### Post by bumblebeef on 2006-09-08
> **daller said:**
> It seems like you have the 2 versions installed on different partitions!

Simply upgrade your 5.10 to a 6.06? (and then remove the other 6.06?)

Or what is the problem?

Yeah, I have the two different versions installed on different partitions. Really annoying. On one partition I have 5.10, and on the other I have 6.06. I would update the 5.10, but it would be so much easier if I could just keep 6.06 I already have (which has all of my customizations and files and such). Additionally, the boot file has the 5.10 as the default partition to load, and I want it to be the 6.06. After I get that set, I'd like to delete the 5.10, if at all possible. Like I said, it's a mess. But thanks for the help so far, and if you can me any further, that'll be even better!

---

### Post by confused57 on 2006-09-08
You might be able to reformat the 5.10 partition as ext3, using gparted live cd:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then reinstall grub using the Dapper live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then mount the ext3 partition in Ubuntu for storing files, etc:

[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

I can't guarantee if my suggestions will work, but it'll give you some ideas...you may want to wait until someone more experienced with your situation reads your thread.

Here's how to change the Default OS in grub:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by bumblebeef on 2006-09-10
> **confused57 said:**
> You might be able to reformat the 5.10 partition as ext3, using gparted live cd:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Then reinstall grub using the Dapper live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Then mount the ext3 partition in Ubuntu for storing files, etc:

[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

I can't guarantee if my suggestions will work, but it'll give you some ideas...you may want to wait until someone more experienced with your situation reads your thread.

Here's how to change the Default OS in grub:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

Your suggestions worked, by the way. I couldn't get the LiveCD to work, so in the Ubuntu 5.10 I edited the boot file to recognize the 6.06 and edited it to state the 6.06 as the default OS. After doing that, I deleted the 5.10, and everything's been working just about fine since. Thanks a lot for the help!

---

