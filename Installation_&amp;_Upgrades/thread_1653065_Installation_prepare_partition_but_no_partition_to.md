---
title: "Installation: prepare partition but no partition to choose"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by willerman on 2010-12-26
I am in the middle of the Ubuntu 10.10 installation. Then I am asked to prepare my partitions, but the screen with partitions is blank. I see no option to add or edit stuff and I can only go back or forward. When I go forward I get an error because I don't have any partitions. If I go back then I don't progress in my installation...  
 Strangely, when I start GParted from the same live CD I can see and edit all the partitions and can also access them via Nautilus.  
 I already deleted all partitions and even the partition table but nothing helps. The installer just wont work.  
 Even more strangely Ubuntu 9.04 doesnt have a problem with the installation. The problem starts with Ubuntu 9.10.  
 My HW setup is one IDE channel with my DVD drive as master and the HDD as slave.  
 Does anybody know, how I can solve this??

---

### Post by srs5694 on 2010-12-26
Post the output of the following command:

```

sudo fdisk -lu

```

Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

### Post by sikander3786 on 2010-12-27
If there is an option in your Bios, switch the HDD mode to 'ahci' or compatible and your HDD might get detected.

And also, post the output of above command from Application > Accessories > Terminal.

---

### Post by willerman on 2011-01-15
Problem is solved!

The key-word is [COLOR=#800000]dmraid[/COLOR]

[viewtopic.php?f=46&t=54989&p=315075&hilit=dmraid#p315075]("http://forums.linuxmint.com/viewtopic.php?f=46&t=54989&p=315075&hilit=dmraid#p315075")


Cheers everybody

---

### Post by dino99 on 2011-01-15
> **willerman said:**
> Problem is solved!

The key-word is [COLOR=#800000]dmraid[/COLOR]

[viewtopic.php?f=46&t=54989&p=315075&hilit=dmraid#p315075]("http://forums.linuxmint.com/viewtopic.php?f=46&t=54989&p=315075&hilit=dmraid#p315075")


Cheers everybody

i'm happy for you :) then please mark this thread as SOLVED using the "thread tool" on top

---

### Post by Muzzab on 2011-09-15
I have the same problem. I tried running dmraid and it just says nothing is blocked? I've been trying to get this to work all day. Any ideas?

---

### Post by Quackers on 2011-09-15
It's solved for the original poster.
If you have a problem you should start a thread of your own giving details of what has happened. You haven't given much info so far :-)

---

### Post by Muzzab on 2011-09-15
OK so I'm was trying to install windows 7 Ultimate along side Ubuntu 10.04. Windows has installed no problem but when I boot the computer to install Ubuntu, step 4 takes me not to the screen asking me if I would like to install Ubuntu alongside windows as usual, but to the screen to edit and select the partitions to install Ubuntu on. The problem is there is no partitions available to select or edit. I tried running the dmraid as mentioned earlier to solve the problem but it says nothing is blocked. 

I have tried Ubuntu 9.10, 10.04, 11.04 as well as the alternate versions and Fedora on both cd and usb but always the same thing. I have searched the forums but found nothing that helps. That's all the information I have, sorry I'm not a computer genius. It's always worked no problem in the past.

Any info would be appreciated.
Cheers.

---

### Post by srs5694 on 2011-09-16
> **Muzzab said:**
> OK so I'm was trying to install windows 7 Ultimate along side Ubuntu 10.04. Windows has installed no problem but when I boot the computer to install Ubuntu, step 4 takes me not to the screen asking me if I would like to install Ubuntu alongside windows as usual, but to the screen to edit and select the partitions to install Ubuntu on. The problem is there is no partitions available to select or edit. I tried running the dmraid as mentioned earlier to solve the problem but it says nothing is blocked.

You've probably got damaged partition table data or leftover GPT data. (Old RAID data is another possibility, but it sounds like you've taken the steps to remove that.) My [FixParts program](http://www.rodsbooks.com/fixparts/) will take care of most of the partition table errors that cause this problem. If you want more diagnosis before trying that, please boot the Ubuntu installer to its "try it now" mode, launch a Terminal window, and type:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. That will probably give us the information we need to positively identify the problem. (If not, further tests will be necessary, perhaps revisiting the leftover RAID data possibility.)

---

