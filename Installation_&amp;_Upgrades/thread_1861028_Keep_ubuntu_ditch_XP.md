---
title: "Keep ubuntu ditch XP"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Mean Mr Mustard on 2011-10-15
ALL I want to do is wipe XP system off my desktop PC but retain the present wubi  install of 11.04 that I have along with certain files and folders from  my "XP days". My PC has TWO hard drives each of 156GB and I would like  to put the wubi install on one drive say  in a suitable partition and then retain rest of that hard drive and the other hard drive for whatever. Being a newbie I would like to keep it nice and  simple if that’s possible? Anyone care to help me with this please? Many thanks. 

 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11345950") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11345950")

---

### Post by 2F4U on 2011-10-15
Unfortunately, what you want is not possible. Wubi runs "inside" Windows, so if you remove Window you also remove Wubi. If you want to get completely rid of Windows, you have to do a clean install of Ubuntu. You should do a backup of your files before you do that.

---

### Post by critin on 2011-10-15
Download a live iso image and burn it to cd or usb stick.  Install it to the other drive and keep your xp drive intact.  You will be able to get to your xp files through a network share.  Copy files and move them to your ubuntu if needed.  You will be dual booting.  Easy to use both worlds.

When you have all your files removed from Wubi through the share, you can delete it from Windows through the Add/Remove program.

critin

---

### Post by oldfred on 2011-10-15
Wubi is meant to run from inside Windows. But one old timer here did show a very advance way to boot it mostly just for fixing things. Best just to convert to standard partitions.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Even the designer of wubi expects you to convert:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Mean Mr Mustard on 2011-10-15
> **2F4U said:**
> Unfortunately, what you want is not possible. Wubi runs "inside" Windows, so if you remove Window you also remove Wubi. If you want to get completely rid of Windows, you have to do a clean install of Ubuntu. You should do a backup of your files before you do that.
Thanks for that - I will back up my important files FIRST!

---

### Post by Mean Mr Mustard on 2011-10-15
> **critin said:**
> Download a live iso image and burn it to cd or usb stick.  Install it to the other drive and keep your xp drive intact.  You will be able to get to your xp files through a network share.  Copy files and move them to your ubuntu if needed.  You will be dual booting.  Easy to use both worlds.

When you have all your files removed from Wubi through the share, you can delete it from Windows through the Add/Remove program.

critin
I understand what you are saying but I was hoping to keep my present wubi settings and transfer ubuntu 11.04, particularly my wireless card settings (eg drivers) as it works great now but took an enormous effort  from forum members to get to get it to work, did'nt want to throw all that away.

---

### Post by Mean Mr Mustard on 2011-10-15
> **oldfred said:**
> Wubi is meant to run from inside Windows. But one old timer here did show a very advance way to boot it mostly just for fixing things. Best just to convert to standard partitions.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Even the designer of wubi expects you to convert:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
Many thanks for all the info, but that one thread [COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1519354[/COLOR]  really scares me!  Don't think I could manage that at my stage of learning!

---

### Post by oldfred on 2011-10-15
I have not done it, but I though bcbc had a nice little script, where you create / (root) & swap partitions first and then use the script to copy everything over for you? Or the bit more complex manual method.

Of course good backups are important. You user settings are all in hidden files in /home but your system setting like your wireless are in /etc.

---

### Post by Mean Mr Mustard on 2011-10-15
Many thanks for your reply but can you please explain to me what you mean by "Your user settings are all in hidden files in /home but your system setting like your wireless are in /etc."
 
Also please tell what this means "To migrate to [COLOR=red]/dev/sda5[/COLOR] without swap" and this "To migrate to [COLOR=red]/dev/sda5[/COLOR] with swap on [COLOR=blue]/dev/sda6 "[/COLOR]

AND what is a grub bootloader as opposed to no-bootloader option ?
 
Many thanks for your understanding but as you can tell I am very new to this.

---

### Post by oldfred on 2011-10-15
Ubuntu is a multi user system, so each user has setting & files in his/her /home. But system wide settings are normally stored in /etc.

Many settings in /home are . files or hidden unless you turn on show hidden files. like /home/fred/.mozilla for Firefox settings and profile which has all your Firefox data.

---

### Post by Mean Mr Mustard on 2011-10-16
Well I followed the script and got this:-
 
mike@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sda
[sudo] password for mike: 
Sorry, try again.
[sudo] password for mike: 
bash: wubi-move-2.1.sh: No such file or directory
mike@ubuntu:~$ 
 
Please explain where I went wrong and yes I did download the file to my Home Folder, then Downloads. Then I opened a Terminal and followed the script from bcbc??????????????

---

### Post by oldfred on 2011-10-16
Understand the difference between a drive like sda or sdb and a partition like sda1 or sda5.

If you created a new partition sda5 for your new / (root) you need to tell it to install to that not sda.

sudo bash wubi-move-2.1.sh [COLOR=red]/dev/sda5[/COLOR]

---

### Post by Mean Mr Mustard on 2011-10-16
> **oldfred said:**
> Understand the difference between a drive like sda or sdb and a partition like sda1 or sda5.

If you created a new partition sda5 for your new / (root) you need to tell it to install to that not sda.

sudo bash wubi-move-2.1.sh [COLOR=red]/dev/sda5[/COLOR]
Created partition [COLOR=Red]sdb5[/COLOR] [COLOR=Black]and got this AGAIN![/COLOR]

mike@ubuntu:~$ sudo bash wubi-move-2.1.sh /dev/sdb5
[sudo] password for mike: 
bash: wubi-move-2.1.sh: No such file or directory
mike@ubuntu:~$

I if try the CD route to get ubuntu on second hard drive will I lose my wireless connection that I have now via wubi?

---

### Post by Mean Mr Mustard on 2011-10-16
> **critin said:**
> Download a live iso image and burn it to cd or usb stick.  Install it to the other drive and keep your xp drive intact.  You will be able to get to your xp files through a network share.  Copy files and move them to your ubuntu if needed.  You will be dual booting.  Easy to use both worlds.

When you have all your files removed from Wubi through the share, you can delete it from Windows through the Add/Remove program.

critin
I if try the CD route to get ubuntu on second hard drive will I lose my wireless connection settings that I have now via wubi?

---

### Post by oldfred on 2011-10-16
As critin said you can copy your setting from your wubi install after you install to your second drive if that is what you want to do.

---

### Post by Mean Mr Mustard on 2011-10-17
> **oldfred said:**
> As critin said you can copy your setting from your wubi install after you install to your second drive if that is what you want to do.
Installed ubuntu 11.04 via Live CD after partitioning hard drive. But when I boot up now I get black and white vertical bands right across monitor screen  for about three seconds followed by usual purple screen buts all distorted for a further few seconds and then it gets to normal desk top? All looks very messy at first, is there a way that I can remove these first few seconds of Bootup?

---

### Post by Mean Mr Mustard on 2011-10-17
> **critin said:**
> Download a live iso image and burn it to cd or usb stick.  Install it to the other drive and keep your xp drive intact.  You will be able to get to your xp files through a network share.  Copy files and move them to your ubuntu if needed.  You will be dual booting.  Easy to use both worlds.

When you have all your files removed from Wubi through the share, you can delete it from Windows through the Add/Remove program.

critin
Installed ubuntu 11.04 via Live CD after partitioning hard drive. But  when I boot up now I get black and white vertical bands right across  monitor screen  for about three seconds followed by usual purple screen  buts all distorted for a further few seconds and then it gets to normal  desk top? All looks very messy at first, is there a way that I can  remove these first few seconds of Bootup?

---

### Post by critin on 2011-10-18
<<*Installed ubuntu 11.04 via Live CD after partitioning hard drive. But when I boot up now I get black and white vertical bands right across monitor screen for about three seconds followed by usual purple screen buts all distorted for a further few seconds and then it gets to normal desk top? All looks very messy at first, is there a way that I can remove these first few seconds of Bootup?*>>

I wouldn't know what to suggest to clean that up, but I do know my screen occasionally does the same things.  It goes away quickly so I don't worry about it.  In my case it may be because I install/reinstall so many distros to try them out.  I figure it's just trash left over and it gives me no problem.

critin

---

