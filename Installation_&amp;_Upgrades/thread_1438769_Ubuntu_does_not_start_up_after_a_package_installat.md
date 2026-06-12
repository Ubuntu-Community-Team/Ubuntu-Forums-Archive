---
title: "Ubuntu does not start up after a package installation"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by dabonai on 2010-03-25
Hi. I am new to Ubuntu. My version is 9.10 I have been using it for a couple of weeks.
When I install a new software from the list of available applications something weird happens to Ubuntu the next day I turn on my desktop.

Issue: Ubuntu shows the white color logo and never shows the log in screen.
How to fix it ? Unknown. Sometimes I restart it 3 times or attempt the second option to enter Ubuntu and it works.

I would like to know if there is a fix I can place in Ubuntu. I don't want to damage my hard disk while restarting my desktop.

Regards,
Danny

---

### Post by dabl on 2010-03-25
I think you are associating two things that are probably not related.

There probably is some kind of hardware issue (thermal issue, slow spinup of hdd, video driver not happy, BIOS needs upgraded, whatever) that is at the root of the occasional boot problem.  The fact that you installed software in the prior session is probably irrelevant.  On a new installation, one normally does install a new package fairly often -- maybe every booted session.  Try letting it run a few hours with no new software installed, then shut it down and let it get completely cooled, and reboot (the next morning).  I think you will find there is an occasional boot problem, whether new software was installed, or not.

---

### Post by dabonai on 2010-03-31
Thanks for your advice. I found out how to disable the Splash and was able to monitor the executed lines during the start up for several days.

Finally, a couple of days ago my pc failed again while starting up ubuntu. Last lines executed "were out of memory error" and stopped start up in line "modem-manager: Loaded plugin Nokia"


More Details:

Day 1 - Message (PC temperature 90 F )

Starting init crypto disks /dev/sda1
...

modem-manager : Loaded plugin Erickson
modem-manager : Loaded plugin MotoC
modem-manager : Loaded plugin Sierra
modem-manager : Loaded plugin Nokia

(After 30 mins I decided to shut down my desktop because nothing else happened in the start up)

Day 2 - Message

Killed process 504 (unreadahead)
init: unreadhead main process (504)
killed by kill signal
fs ck from util-linux-ng 2.6

---

### Post by sudo-i on 2010-04-01
I've been having this same issue multiple machines.
Your problem lies (lays?) in the grub update.  If you can get into your recovery boot, run the update manager again. Most times it fixes it.

if not, open terminal and 
sudo apt-get install grub-pc 
and follow the prompts.

Ref: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

no guarantees, but this solved my issues.

eta:  so I was wrong.  The sony vaio desktop I put 9.10 two days ago is displaying the same symptoms.  But the other 3 machines are still running...

---

### Post by roldannarag on 2010-04-01
Please Help me..I have a lot of files in my Ubuntu..

I Just Mark all Upgrade in my Synaptic package..after restarting my laptop..Login appears but when i log in olny mouse cursor with black screen appears..

please help..


Im using lenovo with ATI video Card..

thanks...
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		 		 		  	 	 	 	 		  		 		 			[[IMG]http://ubuntuforums.org/images/buttons/forward.gif[/IMG]]("http://ubuntuforums.org/private.php?do=newpm&forward=1&pmid=1275426")

---

### Post by dabonai on 2010-05-01
Sure, I will do. Now, I am using Ubuntu 10. Let's how it goes.

---

