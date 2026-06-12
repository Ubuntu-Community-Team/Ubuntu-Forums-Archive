---
title: "not booting"
date: 2010-01-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phillw on 2010-01-13
Well, it had to happen .. That carnivore finally ate piglet.  Boots to grub, select 2.6.32-10-generic, Ubuntu splash come up .. Then the wholse screen darkens. Keyboard un-responsive. Have to power off.  ran fsck via the backup of 9.10 reports as clean - I can boot into recovery .. But, as this is a 1st for me .. Any ideas ?  

edit - tried repairing roken packages from rescue - no good

Thanks,  Phill.

---

### Post by phillw on 2010-01-13
I read in another thread of a similar problem - could some one tell me how / where to use nomodeset as per thread [http://ubuntuforums.org/showthread.php?t=1378815](http://ubuntuforums.org/showthread.php?t=1378815)   

Not  sure if I have the same problem, and that *should* prove it one way or the other

Thanks,

Phill.

---

### Post by alphacrucis2 on 2010-01-13
After the latest updates, the boot up appears to halt with a black screen but curiously, the system still responds to the keyboard. If I start in recovery mode and boot to root terminal with networking, then I can login as myself and startx, Then everything is ok. Maybe a problem with gdm login screen? Dunno

---

### Post by jerrylamos on 2010-01-13
> **phillw said:**
> I read in another thread of a similar problem - could some one tell me how / where to use nomodeset as per thread [http://ubuntuforums.org/showthread.php?t=1378815](http://ubuntuforums.org/showthread.php?t=1378815)   

Not  sure if I have the same problem, and that *should* prove it one way or the other

Thanks,

Phill.


On the initial grub boot screen,
Down arrow to the desired grub line then push
e
down arrow to the line starting with linux
push end then add 
nomodeset 
right after quiet splash
Crl-x 
to boot.

This has to be done with every boot.

For putting it in permanently, 
sudo gedit /etc/default/grub
add after quiet splash but before the "
nomodeset
save
quit
then do
sudo update-grub

The whole thing about mode is to put the video graphics into graphics not text mode before the desktop is displayed.  This then speeds up logging out as one user and in as the next since the video mode doesn't have to be changed.  My view, the code is very buggy and gives me a pain in the neck.  However, I can deal with it...

Jerry

---

### Post by phillw on 2010-01-13
Thanks Gerry,

I've  tried that patch (I kidnapped one of the guyz who knows grub2) - but it is still a non-starter. 

Still, it's the 1st time they've managed to bork my machine since the rc of A1 :)

So, it sorta had to be my turn - just out of fairness to everyone else

Hey, ho - it'll get fixed...

Just cannot bug report it, as no crash report etc.

:-(

---

### Post by phillw on 2010-01-13
Reading further . I found a thread on intel drivers (the jaunty one) from the thread earlier posted  [http://ubuntuforums.org/showthread.php?t=1378815](http://ubuntuforums.org/showthread.php?t=1378815)

```
 /etc/init.d/gdm restart
```

deffinately gives the black screen of death.

Laptop is on WiFi link, which doesn't work in rescue mode - So, I'm goin gto try rolling back the intel driver to my 9.10 system tomorrow on ethernet.

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

I'm not going that far back ...

---

### Post by phillw on 2010-01-13
anyways it looks like i'm on an intel one -- 945GM/GMS/GME, 943/940GML  chip-set

It's 03:00 here in the uk - I'll hook the laptop upto ethernet after some sleep and try to find a working one.

9.10 reports back  2:2.9.0-1ubuntu2  as the 
xserver-xorg-video-intel  one - So, I guess it is use those instructions to hit the Karmic
repositry and get that one.

edit  10.04 reports back that it has 2:2.9.1-1ubuntu1    So that's a start ;-)

If any one has any other success - please post !! - but, A2 is not quite ready to ship as it is the 1st time from the rc of A1 that 10.04 has 'killed' my system.

Phill.
Using a part built XP machine to help a Linux one ..... :(

---

### Post by Ibidem on 2010-01-13
Intel (945) graphics here, no Plymouth installed--no splash at all--, no display manager present, starting display by startx.  No problems at all (since I updated to the last X version).
I'd guess to try starting in CLI, and run startx.
Ibidem

---

### Post by phillw on 2010-01-14
Solved - by the email instructions over here --> [http://ubuntuforums.org/showthread.php?t=1379719&page=3](http://ubuntuforums.org/showthread.php?t=1379719&page=3)

Phill.

---

