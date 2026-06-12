---
title: "Re-install Ubuntu 7.10"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by blueskyabove on 2008-03-22
I installed 7.10 a while ago (dual boot with XP) but I can't carry out any administrative tasks. I can't add "Add/remove" to the Applications Menu, I can't see "services" in the Administration menu, "Edit Users and Groups" asks for a password but I obviously don't have the right one -  and so on, right across the board.  I'm new to Ubuntu and Linux and am lost.  I have no files in Ubuntu that matter so I now want to start over, keep my XP partition as is and completely re-install Ubuntu 7.10 over the existing installation.  Can this be done?  If so, how.  HELP!

---

### Post by sandysandy on 2008-03-22
>  password but I obviously don't have the right one 

its ur user password. the password u chose at the time of installation. 


here are some linux tutorial links

[http://lowfatlinux.com/](http://lowfatlinux.com/)

[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)


regards

---

### Post by sandysandy on 2008-03-22
> **blueskyabove said:**
> I installed 7.10 a while ago (dual boot with XP) but I can't carry out any administrative tasks. I can't add "Add/remove" to the Applications Menu,   HELP!
some more links

[http://users.bigpond.net.au/hermanzone/p5.htm#Add_Terminal_Launcher_to_Panel](http://users.bigpond.net.au/hermanzone/p5.htm#Add_Terminal_Launcher_to_Panel)

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

[https://wiki.ubuntu.com/Training](https://wiki.ubuntu.com/Training)

no need to re-install. go thru the links before u re-install

regards

---

### Post by forestpixie on 2008-03-22
If you do decide to reinstall - it's easier this time as you already have a partition. If you don't know which one it is then open a terminal and post the output of this command

```
sudo fdisk -l
``` 
one line will have _similar_ to this, there will also be a swap partition - don't worry about that
> [COLOR="Red"]
/dev/sda1[/COLOR]               1        1094     8787523+  83  Linux
the /dev/ information is what you need to know.

Boot the livecd - choose manual partition option.

You will get a list of partititions - choose the one which corresponds to your existing installation, highlight it and click the 'edit partition' button - you'll get a new screen with mountpoint option - choose / and save or close that screen. Now you'll be back in the first screen - pick the partition again and put a tick in the 'format' box - DO NOT PUT ONE ELSEWHERE. 

You should now have a line showing a mountpoint of / and it has formatting enabled. That will now install buntu over the original one.

---

