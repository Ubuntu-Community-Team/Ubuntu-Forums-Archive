---
title: "[bug] Splash screen failure after &quot;Install Unbuntu&quot; &quot;okay&quot; option."
date: 2013-08-20
forum: Installation &amp; Upgrades
---

### Post by 6Hkx6TR on 2013-08-20
Specs:

2008 acer aspire mobo
Intel core duo 
HD Radeon 7750

OS:
12.04 LTS
12.10
13.04

ALL AMDX64 VERSIONS

the rest of the stuff honestly doesnt matter.

there's a problem some people, I've noticed through googling for 1 hour, have been having which has NOT BEEN RESOLVED correctly. some people, when installing 12.04 LTS/ 12.10/ 13.04 64 BIT have not been able to succesfully install. they get to the install unbuntu window and then click next.

they then arrive at this window:
[IMG]http://assets.ubuntu.com/sites/ubuntu/533/u/img/download/desktop-install-2.png[/IMG]

They unknowingly check the "download updates" and "install 3rd party" options and click continue only for the system to lock up and then a black splash screen with kernal bugs pops up.

This is a BUG because I have been able to replicate it, on my system and others, a total of 23 times. yes I am that sad that after the first attempt i did it 23 times. What did you do for 23 times? Swapped processors, swapped hard drives, swapped cd drives swapped gfx cards swapped RAM chips etc etc etc.

Simple solution? I didnt check "download whilst updating" and "install this third party..." and it went to install properly 100% of the time. For "scientific" error checking after sucesfully installing on a "control" system, the one above, i deleted ubuntu and wiped the HDD, reinstalled Windows 7, then did the whole process again and replicated the bug a further 24th time. 

yes i dual booted - i.e. i had wind 7 on the hdd, and yes I used Universal-USB-Installer-1.9.3.5 to make a USB and booted into it. 

I dont care if others havent had this bug, this is a legit bug which exists - annoyingly - for some users and the cause it simply checking those two boxes. 
[U][B]
Solution: dont check the boxes and install the stuff after. [/B][/U]

I hope those few people who did have the problem actually see this thread and to those who had it, and didnt report it as a bug should next time post so this OS becomes more viable commercially. The benefit of unbuntu and in general linux based system is that when it comes to old architecture and old systems, they are MUCH more accessible and usable than windows systems/ OS due to being lightweight and not taxing on hardware such as not defragmenting HDDs etc etc. If you try to install Ubuntu on a new system and it wont be bugged, then that respect should be carried out to older (2008) systems. 

With newer systems even when you install ubuntu you get a black screen after successful installation because first it tells to to remove the device which you use to install the OS, then it turns out to load the OS it actually needed that device in... (apart from the turn up brightness bug).

---

