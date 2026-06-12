---
title: "fixing failed installation of 10.04"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by doihavetodothis? on 2010-09-07
Please help me to save my home folder, mail and bookmarks. 
I have a dual boot PC, tried to upgrade to Lucid Lynx and the upgrade failed. Can't boot into it at all. Windows XP still works fine. I have the live CD for a re-install now. I read this post but don't understand the difference between the instructions for the partitions. Have posted my screen shots below. 
First screen shows that I have 10.04 and offers me the option to partition further.
Screenshot 1 I choose manual partition and then it gives me the right sized partitions. . Then in screenshot 2 I edit and choose the mount point as /, is that right? 
(screen shot 3). Do I then change that option again to choose /home? 
because otherwise  it takes me straight to screenshot 4, the user name set up.

What am I missing? 
Here is the post I am using as a guide:
[http://ubuntuforums.org/showthread.php?t=1569675](http://ubuntuforums.org/showthread.php?t=1569675) 

              There's No Custom User Title Here
             [IMG]http://ubuntuforums.org/images/rank_uf_staff.png[/IMG]
                                                                  
[[IMG]http://ubuntuforums.org/customavatars/avatar610428_55.gif[/IMG]]("http://ubuntuforums.org/member.php?u=610428")                 
                                             
                Join Date: May 2007
                 Location: The New Forest
                       My beans are hidden!
                    Ubuntu 10.04 Lucid Lynx                                                                                          
             
                                                                                                   **Re: Re install Ubuntu but keep /home**             
                                                                If your /home is on a seperate partition, start the installer - pick manual at the partition stage.

Select the existing / partition - Edit partition - Use as ext4,format and Mountpoint - / then save/close that window

Select the existing /home partition - Edit partition - Use as whatever  it was previously, DO NOT FORMAT and Mountpoint /home - save and close  that window

Check that the only partition that is going to be formatted is the existing / partition.

Carry on - that will install over the existing installation and use the old /home.

Use the same username though.

Always good to have backups though :wink:
                                                                                               __________________
                [B][CENTER][[COLOR=Navy]Realtime help at #ubuntu-beginners[/COLOR]]("http://webchat.freenode.net/?channels=ubuntu-beginners")[/CENTER]
[/B]
[COLOR=Navy][B][CENTER][Help us help you]("http://ubuntuforums.org/showpost.php?p=8920811&postcount=1")[/CENTER]
[/B][/COLOR]

---

### Post by rotave on 2010-09-07
This tutorial video might explain the process better: 
[http://www.youtube.com/watch?v=wOMIbf_dbDY]("http://www.youtube.com/watch?v=wOMIbf_dbDY")

---

### Post by doihavetodothis? on 2010-09-07
Thanks, I'm working off the liveCD right now, and can't watch the vid... but the partitioning is already done and has been working with Hardy Heron and XP for the last two years. The prob is replacing the failed upgrade without losing my data?

---

### Post by rotave on 2010-09-07
Your current configuration does not have a seperate /home partition, therefore the only way to save your home folders, docs etc is to back them up from the live cd to a usb drive and then reinstall ubuntu with a seperate /home partition.

---

### Post by doihavetodothis? on 2010-09-08
Thanks - I can get most of my files, that way and have already, but not my mail and my bookmarks - can't get permission to copy them and even if I could I don't think that the right way to save/back up my mail... gksu nautilus doesn't work.

---

### Post by doihavetodothis? on 2010-09-12
> **doihavetodothis? said:**
> Thanks - I can get most of my files, that way and have already, but not my mail and my bookmarks - can't get permission to copy them and even if I could I don't think that the right way to save/back up my mail... gksu nautilus doesn't work.
Just for anyone's info - from the live Cd go to your ubuntu partition use sudo nautilus in the command line and change the permissions of files to read (by others or to read and write) then copy them to where ever you want to back them up. - usb, dvd, other partition. Then re-install. You should change permissions back afterwards...
I haven't got there yet, but I'm assuming that if I split my partition between / for the OS and /home this problem will never happen again :D
And of course next time I will back up before trying to update.

---

