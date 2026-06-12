---
title: "problem after increasing disk space in wubi, getting stuck in login page"
date: 2013-08-09
forum: Installation &amp; Upgrades
---

### Post by amir4 on 2013-08-09
Hi, 
I have a very complicated problem I hope someone can help me.

I kept taking a warning from Ubuntu that the remaining space is less than a Gb. so I looked some forum to learn how I can increase the space of Wubi.
and find this [http://superuser.com/questions/125990/how-to-increase-disk-space-in-wubi-ubuntu-via-windows](http://superuser.com/questions/125990/how-to-increase-disk-space-in-wubi-ubuntu-via-windows) which says I need to do following
[FONT=tahoma]
[/FONT][COLOR=#000000][FONT=Arial][FONT=tahoma]Download [wubi-add-virtual-disk]("https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=wubi-add-virtual-disk"), open a terminal and run:[/FONT][/FONT][/COLOR]
[FONT=tahoma]sudo sh wubi-add-virtual-disk /home 15000
[/FONT][FONT=Arial][FONT=tahoma]Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.[/FONT][COLOR=#FF0000]

[/COLOR][COLOR=#000000]I did exactly the same and when I reboot, I entered my password, it did not work. A black page appeared whenever I entered my password and then I get redirected to the login page. At this time I was able to log as guest.
I look for some solution for this problem. I tried following. 

press  cntrl+Alt+F3, log in , then enter ls -lah (did not work)
                                                   enter ls -ld/tmp (did not work)
                                                   enter chmod a+wt/tmp (did not work)
                                                   enter chown username:username .Xauthority (did not work)
and finally i did 
                                                   enter sudo apt-get update
                                                   enter sudo apt-get install nvidia-current

After this point everything get worse. Now I can't even log in as guest. basically ubuntu does not seem accessable at all. 
I was wondering if some has some idea . I really appreciate that. I hate reinstalling Ubuntu as I have tons of stuff on it. 

Thanks[/COLOR][/FONT]

---

