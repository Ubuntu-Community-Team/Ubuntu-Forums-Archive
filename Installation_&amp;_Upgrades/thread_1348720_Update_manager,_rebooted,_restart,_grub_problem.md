---
title: "Update manager, rebooted, restart, grub problem"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by fchartier on 2009-12-07
Hi all, 

I have juste ubuntu 9.10 and and downloaded all the sofware listed in Update manager = 90mb

a) Once finished install, I rebooted, selected ubuntu and before the ubuntu loading window, a dark window appeared with commands. **grub (i am not 100% sure how u spell it) **showing ( ''Press TAB for command list etc''.. which i did as i thought that it was part of the update process. There is a list of commands separated by spaces. Unfortunately i do not know how to get pass this point. the only command i was able to type: reboot.

 b) Just so you know how i installed which could part of the reason of this bug or not. I used wubi and seen as the normal way of letting wubi install the iso. which i did a couple of times. i managed to follow some tips on the forum saying to download the iso file for ubuntu directly, placing the file in the same folder as wubi, then executing wubi. It all worked !! it was a great relief. Now i am a bit stuck. 

c) Other question, it seems that my laptop is a bit slow on ram, 500 mb, processor 1.7 ghz. when i installed ubuntu i used 17 gb, (33 were free on my C = 55 in total). Should i reinstall ubuntu (the same way) using more size for better conditions of use? 

If you know anything about this, THanks a lot.

Cheers
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8455112") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8455112")

---

### Post by darkod on 2009-12-07
Look at post #10 here about wubi being broken by updates. Depending on which partition on your drive you installed you should use /dev/sda1 maybe /dev/sda2, etc.
If you are following XP instructions be careful there is typing mistake in the third command, 26.31 should be 2.6.31

If it's working slowly you can consider a derivative called Xubuntu, for older machines with less cpu power and ram. And also you might consider proper ubuntu dual boot install as opposed to wubi which is installing (and working) inside windows. That is making it bit slower it seems.
Any questions, ask.

---

### Post by fchartier on 2009-12-08
Thanks Darko for the advice, 

I migtht install xubuntu, my machine is a bit slow which also the reason why i am migrating to linux from windows as it seems to be lighter and more robust. 
I didn't find your post 10 ...
As for update manager, i think i will wait to have a proper installation perhaps using dual boot so that i avoid situations like these. Then it will be worth digging through. 

Cheers

---

