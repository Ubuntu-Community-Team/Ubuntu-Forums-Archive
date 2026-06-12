---
title: "Can not boot 10.04, want to downgrade to 9.04"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by johnym on 2010-05-20
upgraded to 10.04 on a dell vostro v13. OS will not boot. tried some remedies. got the os to boot up, however, keyboard and trackpad did not work. Got a 9.04 live cd to boot on the dell vostro. can I access my hard drive in order to back up files with live cd? Then i can do a clean install with 9.04 and have all of my data and an os that actually works.
 
it is disapointing that ubuntu would put out a version with so many problams and issues. this is not what i expect from ubuntu. it's supposed to 'just work', isn't it????
 
Thank you in advance,
johnym

---

### Post by wilee-nilee on 2010-05-20
[http://ubuntuforums.org/showthread.php?t=1471573](http://ubuntuforums.org/showthread.php?t=1471573)

---

### Post by JaJaBinks on 2010-05-21
> **johnym said:**
> upgraded to 10.04 on a dell vostro v13. OS will not boot. tried some remedies. got the os to boot up, however, keyboard and trackpad did not work. Got a 9.04 live cd to boot on the dell vostro. can I access my hard drive in order to back up files with live cd? Then i can do a clean install with 9.04 and have all of my data and an os that actually works.
 
it is disapointing that ubuntu would put out a version with so many problams and issues. this is not what i expect from ubuntu. it's supposed to 'just work', isn't it????
 
Thank you in advance,
johnym

I Agree entirely with your sentiments. due to problems with Lucid Lynx, I am going back to Karmic. One should not have to have an intimate knowledge of the operating system to get things to work properly.
I have neither the expertise or time to learn the intricacies of linux to fix issues. Just have a look at all the options in configuration editor. I have no idea what all these things do or what will happen if I change something. I will be thinking twice before upgrading again !!

---

### Post by darkod on 2010-05-21
> **johnym said:**
> upgraded to 10.04 on a dell vostro v13. OS will not boot. tried some remedies. got the os to boot up, however, keyboard and trackpad did not work. Got a 9.04 live cd to boot on the dell vostro. can I access my hard drive in order to back up files with live cd? Then i can do a clean install with 9.04 and have all of my data and an os that actually works.
 
it is disapointing that ubuntu would put out a version with so many problams and issues. this is not what i expect from ubuntu. it's supposed to 'just work', isn't it????
 
Thank you in advance,
johnym

First of all, your assumption that only 9.04 would work is premature. Have you tried a clean install of 10.04? Maybe the upgrade process went wrong?

The support of 9.04 runs out in 6 months, so if you are preparing for a clean install I would think twice whether to go with 9.04. 10.04 is LTS, plus.

As far as the backup is concerned, yes, use live mode to get the data out. Again, not sure why you suggest 9.04 livecd, get a 10.04 livecd and do the backup from live mode.

Running 10.04 in live mode will also show you possible hardware problems.

Clean installs are always better than upgrades. It is enough to simply set up a separate /home partition and you can do a clean install when ever you want.

---

### Post by johnym on 2010-05-21
Darko,
I could not figure out how to do a back up in live mode. It is probably pretty easy, I am just missing something because I am upset. If you know how to do this, could you share it with me?
Thank you,
johnym
 
the 9.04 cd is what i had at the time.

---

### Post by darkod on 2010-05-21
> **johnym said:**
> Darko,
I could not figure out how to do a back up in live mode. It is probably pretty easy, I am just missing something because I am upset. If you know how to do this, could you share it with me?
Thank you,
johnym
 
the 9.04 cd is what i had at the time.

No problem. Just boot into live mode and all your partition will show in Places. Of course, live mode doesn't know what is root, what windows, etc, it will just show like 100GB filesystem, 50GB filesystem, etc.

Click on the partition you want to look at, and I think it will mount it automatically. Once you can look inside, copy all files you need to external hdd or similar (you can even copy on another partition on the same hdd if you want to, depends).

If you want to copy files from another partition, do the same after finding it in Places.

---

### Post by johnym on 2010-05-21
Okay, I booted into live mode. found the files in /media/disk/home/jay    Unfortunatly,
the files I want seem to be locked. When I try to open them, I get 'permission denied' I can not copy them or move them.
Thanks anyway
 
johnym

---

### Post by geerm on 2010-05-21
If you want graphic mode, try sudo nautilus on your terminal, should give you access to everything you want.

Edit: Or  Alt + F2 and type the same

---

### Post by johnym on 2010-05-21
Darko,
I am not sure what happened, but 10.04 lts finally booted up and everything works fine.
 
I also did a intall of 9.04 from the a cd. One of the options was booting along side of 10.04 lts, so I chose that. After the install, I saw a differant grub menu. It showed the 9.04 and 10.04 lts and the recovery mode choiced. I had tried them all to no avail.
 
After working on this all day, I said, lets try the 10.04 lts recovery mode one more time and low and behold it began to boot up. In terminal mode, it asked for a user name and password, whick I entered. completed the boot up, but still in terminal mode. I typed 'startx', and the graphical screne came up. 10.04 lts seems to be working just fine now. Hurray!!!!!!!!!!!!
 
Installing 9.04, change the grub menu. 
 
Thanks for you help,
johnym

---

### Post by wilee-nilee on 2010-05-21
> **johnym said:**
> Darko,
I am not sure what happened, but 10.04 lts finally booted up and everything works fine.
 
I also did a intall of 9.04 from the a cd. One of the options was booting along side of 10.04 lts, so I chose that. After the install, I saw a differant grub menu. It showed the 9.04 and 10.04 lts and the recovery mode choiced. I had tried them all to no avail.
 
After working on this all day, I said, lets try the 10.04 lts recovery mode one more time and low and behold it began to boot up. In terminal mode, it asked for a user name and password, whick I entered. completed the boot up, but still in terminal mode. I typed 'startx', and the graphical screne came up. 10.04 lts seems to be working just fine now. Hurray!!!!!!!!!!!!
 
Installing 9.04, change the grub menu. 
 
Thanks for you help,
johnym

I would be careful about being overly optimistic in that if you reinstalled 9.04 you have installed grub-legacy and now have a mixture of this and grub2 mixed in the operating systems possibly. You may want to post the bootscript to make sure everything is in order.Post it in code tags if you do, by pasting the output into a reply window highlight the text and click on the # in the reply panel.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by johnym on 2010-06-07
Just to let you guys know, after I got 10.04 working, I backed up all my data then did a clean install of 10.04. The OS prompted me to install the drivers for my wireless card, then i was able to connect to my wireless network. In order to do this, I had to connect to the network with an eternet cable connected to my router. No problem. 
 
Everything is working just fine now. I don't intend to do anymore upgrades until the next LTS version comes out.
 
Thanks for your advice,
johnym

---

