---
title: "don't know my username :-)"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by bobetko on 2007-02-10
Ok... I feel stupid... angry... or whatever.... 3 days I am trying to install ubuntu 6.10 on my laptop Dell 900Mhz, Pentium 3 256Mb RAM, and installation freezes all the time. I have Ubuntu on Pentium 2 machine, a little bit slow, but works like a charm... I like it....

The laptop is problem...

So, I took Alternate Version, installed it and now, I am logging for first time and can't pass authentication. I don't remeber being asked to set username. I only remember setting password. Is there some default username that I could use? Somethin like Admin... etc...

Thanks,

---

### Post by Herman on 2007-02-10
Hello bobetko,
You may have performed an [OEM install]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview"), if so you should be able to log in with the username: oem
Then the system will ask you to make up a username and password as described in the link I just gave you.

If not, a simple way to find out the username for a regular install would be to run the Desktop Live/Install Cd and                            [Mount the Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").Then just take a look what's inside the /home directory. There will be a directory there with your username on it.

Another way would be to press your 'c' key from the grub menu, for a grub [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"). You can use grub to investigate what's inside your computer and see what your username directory inside your /home directory is, using techniques explained in that link.

Regards, Herman :)

---

### Post by bobetko on 2007-02-10
sure... I installed it again and made sure I've read all the info...yep... password is oem....

Thanks...

---

