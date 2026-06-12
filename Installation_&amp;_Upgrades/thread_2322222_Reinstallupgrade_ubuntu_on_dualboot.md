---
title: "Reinstall/upgrade ubuntu on dualboot"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by diego57 on 2016-04-27
First of all i didnt know if this thread would be better on installation & upgrade but im relatively new on linux and by consequence ubuntu. 

I want to upgrade to 16.04 but since i dont have a good connection at home i downloaded the iso from another location instead of doing the normal way. The question is, could 
someone guide me to do it? i have dualboot (windows 8 and ubuntu 14.04) with these partitions: windows partitions, root, home and swap. 
The issue is that i want to use the partitions that i already have (not to keep the files, only the partitions). I was going to use the option "reinstall ubuntu it will delete all your documents etc," or something like that but the times i tried to use a default option it lead to some errors so i prefer to use the "something else" option.

If theres anything you dont understand from the post or you need to know further details let me know and i will try to search it.

I forgot to mention, there's a sign that appears when i run the installation that says something like dismount the partitions in the dev/sda to be able to format and partition etc. and gives yes/no as option.

These are the partitions  : 
[IMG]http://i.imgur.com/i5JnfhQ.png?1[/IMG]

---

### Post by DuckHook on 2016-04-27
*Your thread has been moved to **Installation & Upgrades** for replies more relevant to your subject.*

---

### Post by oldrocker99 on 2016-04-27
You do need to unmount sda in order to make changes, which is why you can't use gparted on a running system, but need to use a live boot DVD or USB to do that.

The "Something Else" choice is what you need to use. Choose the / partition (the one colored in your image), check format and mount as /.

Of course, if you want to keep your documents and settings, back up everything in your /home folder **first**. If your home folder is in that partition, it will be lost. You'll need to copy everything over to the new installation. If your /home is in a separate partition, you just format and install in that partition and mount where /home is as /home.

By the way,  before long, Windows 8 will no longer be supported. I'd advise the upgrade to Windows 10, which is still a free upgrade.

Any other questions, just ask.

---

### Post by diego57 on 2016-04-27
Ok when i get home i will try it. Just to clarify, the partition 5 is /, 6 home and 7 swap so by doing what you say it will turn partition 3 into / ? and what would happen to the others (5,6,7)?

I'm at home, I did what you say but checking partition 5 and 6 to format (mount as / and home respectively), everything went right. About windows 8 I forgot to include it is 8.1 not 8 so i guess there's no need to upgrade but if it is just tell me to see what to do and thanks for the help.

---

